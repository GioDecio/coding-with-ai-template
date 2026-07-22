# Python Coding Standards

## General

- Python 3.11+
- Use [PEP 8](https://www.python.org/dev/peps/pep-0008/) style guide
- Line length: 100 characters max
- Use type hints for all functions and class methods
- Use `uv` for dependency management

## Imports

- Group imports: standard library, third-party, local (separated by blank lines)
- Sort imports alphabetically within each group
- Use `from X import Y` for specific items, avoid `import *`
- Use relative imports for local modules

```python
import os
import sys
from pathlib import Path
from typing import Optional

import requests
from dotenv import load_dotenv

from .models import User
from .utils import validate_email
```

## Naming Conventions

- **Modules/Files**: `snake_case` (`user_service.py`)
- **Classes**: `PascalCase` (`UserManager`, `DatabaseConnection`)
- **Functions**: `snake_case` (`fetch_user`, `validate_input`)
- **Constants**: `SCREAMING_SNAKE_CASE` (`MAX_RETRIES`, `DEFAULT_TIMEOUT`)
- **Private**: Prefix with underscore (`_internal_method`, `_private_var`)

## Type Hints

Always use type hints:

```python
from typing import Optional, List, Dict, Tuple

def fetch_user(user_id: int) -> Optional[User]:
    """Fetch a user by ID."""
    pass

def process_items(items: List[str]) -> Dict[str, int]:
    """Process items and return counts."""
    pass

def get_coordinates() -> Tuple[float, float]:
    """Return x, y coordinates."""
    pass
```

## Docstrings

Use Google-style docstrings for public modules, classes, and functions:

```python
def calculate_total(items: List[float], tax_rate: float = 0.1) -> float:
    """Calculate total with tax.
    
    Args:
        items: List of item prices.
        tax_rate: Tax rate as decimal (default 0.1 for 10%).
    
    Returns:
        Total amount including tax.
    
    Raises:
        ValueError: If tax_rate is negative.
    """
    if tax_rate < 0:
        raise ValueError("Tax rate cannot be negative")
    return sum(items) * (1 + tax_rate)
```

## Classes

```python
class UserManager:
    """Manages user operations."""
    
    def __init__(self, db_connection: Database):
        """Initialize with database connection."""
        self._db = db_connection
        self._cache: Dict[int, User] = {}
    
    def get_user(self, user_id: int) -> Optional[User]:
        """Get user by ID from cache or database."""
        if user_id in self._cache:
            return self._cache[user_id]
        
        user = self._db.query(User).filter(User.id == user_id).first()
        if user:
            self._cache[user_id] = user
        return user
```

## Testing

- Use `pytest` for testing
- Test files: `test_*.py` in the same directory as source
- Use fixtures for setup/teardown
- Mock external dependencies

```bash
uv run pytest                # Run all tests
uv run pytest -v            # Verbose output
uv run pytest tests/         # Run specific directory
uv run pytest --cov         # With coverage
```

## Environment Variables

- Use `.env` files (add to `.gitignore`)
- Load with `python-dotenv` or similar
- Never commit `.env` files

```python
from dotenv import load_dotenv
import os

load_dotenv()
DATABASE_URL = os.getenv("DATABASE_URL")
SECRET_KEY = os.getenv("SECRET_KEY")
```

## Error Handling

```python
class UserNotFoundError(Exception):
    """Raised when user is not found."""
    pass

def fetch_user(user_id: int) -> User:
    """Fetch user or raise error."""
    user = self._db.get(user_id)
    if not user:
        raise UserNotFoundError(f"User {user_id} not found")
    return user
```

## Code Organization

```
src/
├── __init__.py
├── models/
│   ├── __init__.py
│   ├── user.py
│   └── item.py
├── services/
│   ├── __init__.py
│   └── user_service.py
├── utils/
│   ├── __init__.py
│   └── validators.py
└── main.py
```

## Async/Await

When using async code:

```python
import asyncio
from typing import Coroutine

async def fetch_user(user_id: int) -> User:
    """Fetch user asynchronously."""
    return await self._db.get_async(user_id)

async def main():
    """Main async entry point."""
    user = await fetch_user(1)
    print(user)

if __name__ == "__main__":
    asyncio.run(main())
```

## Linting & Formatting

Configure these tools in `pyproject.toml`:

- **Formatter**: `ruff` or `black`
- **Linter**: `ruff` or `pylint`
- **Type Checker**: `mypy` or `pyright`

Example:
```bash
uv run ruff check .          # Lint
uv run ruff format .         # Format
uv run mypy src/             # Type check
```
