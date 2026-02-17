# Explanation

## What was the bug?

When `api=true` and `oauth2Token` was a plain object instead of an `OAuth2Token` instance, the client did not refresh the token. As a result, the Authorization header wasn't set, even though the token was invalid.

## Why did it happen?

The implementation relied on a truthiness check and an `instanceof OAuth2Token` condition.  
A plain object is true but not an instance of `OAuth2Token`, so the refresh logic was skipped. Since it was also not an instance of `OAuth2Token`, no Authorization header was added.

## Why does the fix solve it?

The fix treats any non-`OAuth2Token` value as invalid and forces a refresh before proceeding. This guarantees that the token is always a valid `OAuth2Token` instance before setting the Authorization header.

The change is minimal and does not refactor unrelated or other logic.

## One realistic edge case not covered

The current tests do not cover concurrent requests where multiple calls might trigger token refresh at the same time. In real world systems, this could require additional synchronization or caching logic.
