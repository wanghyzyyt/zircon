# zx_futex_wait

## NAME

futex_wait - Wait on a futex.

## SYNOPSIS

```
#include <zircon/syscalls.h>

zx_status_t zx_futex_wait(zx_futex_t* value_ptr, int current_value,
                          zx_time_t deadline);
```

## DESCRIPTION

Waiting on a futex (or acquiring it) causes a thread to sleep until
the futex is made available by a call to `zx_futex_wake`. Optionally,
the thread can also be woken up after the *deadline* (with respect
to **ZX_CLOCK_MONOTONIC**) passes.

## RETURN VALUE

**futex_wait**() returns **ZX_OK** on success.

## ERRORS

**ZX_ERR_INVALID_ARGS**  *value_ptr* is not a valid userspace pointer, or
*value_ptr* is not aligned.

**ZX_ERR_BAD_STATE**  *current_value* does not match the value at *value_ptr*.

**ZX_ERR_TIMED_OUT**  The thread was not woken before *deadline* passed.

## SEE ALSO

[futex_requeue](futex_requeue.md),
[futex_wake](futex_wake.md).
