# Example: ASPT in Action

Below is a simplified example demonstrating ASPT in action for a user authentication system:

```python
# GENERATE: Initial User class implementation
class User:
    def __init__(self, username, email, password):
        self.username = username
        self.email = email
        self.password = password  # Store password directly
        self.is_active = True
        self.last_login = None

# SHALLOW STITCH REVIEW:
# - Security issue: Password stored in plaintext
# - Missing input validation
# - No docstrings

# REFINE:
class User:
    """
    User class representing system users with authentication capabilities.
    
    Attributes:
        username (str): Unique identifier for the user
        email (str): User's email address
        is_active (bool): Account status
        last_login (datetime): Timestamp of last successful login
    """
    def __init__(self, username, email, password):
        # Validate inputs
        if not username or not isinstance(username, str):
            raise ValueError("Username must be a non-empty string")
        if not email or '@' not in email:
            raise ValueError("Valid email address required")
        if not password or len(password) < 8:
            raise ValueError("Password must be at least 8 characters")
            
        self.username = username
        self.email = email
        self._password_hash = self._hash_password(password)
        self.is_active = True
        self.last_login = None
        
    def _hash_password(self, password):
        """Hash password using secure algorithm."""
        import hashlib, os
        salt = os.urandom(32)
        self._salt = salt
        return hashlib.pbkdf2_hmac('sha256', password.encode(), salt, 100000)

# GENERATE: Authentication method
    def authenticate(self, password):
        hashed = hashlib.pbkdf2_hmac('sha256', password.encode(), self._salt, 100000)
        if hashed == self._password_hash:
            self.last_login = datetime.now()
            return True
        return False

# MEDIUM STITCH REVIEW:
# - Missing import for datetime
# - No rate limiting for authentication attempts
# - Authentication success/failure not logged

# REFINE:
    def authenticate(self, password):
        """
        Authenticate a user with password.
        
        Args:
            password (str): The password to verify
            
        Returns:
            bool: True if authentication successful, False otherwise
            
        Raises:
            LockoutError: If account is locked due to too many attempts
        """
        from datetime import datetime, timedelta
        import hashlib
        
        # Custom exception for account lockout
        class LockoutError(Exception):
            """Exception raised when account is temporarily locked."""
            pass
        
        # Check for account lockout
        if hasattr(self, '_failed_attempts') and self._failed_attempts >= 5:
            if datetime.now() - self._last_attempt < timedelta(minutes=15):
                raise LockoutError("Account temporarily locked")
        
        # Verify password
        hashed = hashlib.pbkdf2_hmac('sha256', password.encode(), self._salt, 100000)
        if hashed == self._password_hash:
            self.last_login = datetime.now()
            self._failed_attempts = 0
            self._log_activity("successful_login")
            return True
        else:
            # Handle failed attempt
            if not hasattr(self, '_failed_attempts'):
                self._failed_attempts = 0
            self._failed_attempts += 1
            self._last_attempt = datetime.now()
            self._log_activity("failed_login")
            return False
            
    def _log_activity(self, activity_type):
        """Log user activity for security monitoring."""
        # Implementation of activity logging
        pass

# DEEP STITCH REVIEW:
# - Need to implement user repository for persistence
# - Authentication system needs integration with session management
# - Password reset flow not implemented
# - Activity logging needs to connect to monitoring system
# ...etc
```

## Analysis of ASPT Implementation

The example demonstrates how ASPT improves code quality through iterative review cycles:

### Initial Generation
- Basic class structure created
- Core properties defined
- Fundamental functionality established

### Shallow Stitch Improvements
- Security vulnerability identified and fixed (plaintext password)
- Input validation added
- Documentation added for class and methods
- Proper encapsulation implemented

### Medium Stitch Improvements
- Missing imports identified and added
- Edge case handling implemented (account lockout)
- Error management improved
- Logging added for security events
- Proper exception definitions

### Deep Stitch Considerations
- System-level integrations identified
- Additional required features noted
- Future development roadmap established

## Benefits Demonstrated

This example illustrates several key benefits of ASPT:

1. **Incremental Quality Improvement**: Each review cycle raises the code quality
2. **Progressive Depth**: Reviews move from syntax to logic to architecture
3. **Issue Prevention**: Problems fixed before they propagate through the system
4. **Comprehensive Coverage**: From basic functionality to security considerations
5. **Design Evolution**: Implementation naturally evolves toward robust design

The difference between the initial implementation and the final version demonstrates how ASPT creates more robust, secure, and maintainable code through systematic review cycles.

[Back to README](../README.md)
