## 2025-05-13 - Memoizing Security Policy Checks
**Learning:** `SSRFPolicy` is a `frozen=True` dataclass, making it safe to use as a cache key in `functools.lru_cache`. Memoizing the IP range validation check (`_ip_in_blocked_networks`) provides a ~3x speedup on a hot path that performs multiple linear scans over blocked network lists.
**Action:** Always look for frozen dataclasses or immutable structures in hot paths that can be easily memoized with `lru_cache`.
