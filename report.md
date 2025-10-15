# Procedure Lab Report

Author: *ArnavPallapotu*

## Security Report;
- **What I sent:** `<script>alert(1)</script>` to `/vulnerable_echo`.  
- **What happened:** Before the fix an alert textbox with "1" popped up. After the fix the script was escaped and no alert appeared.  
- **Why vulnerable / Fix applied:** The endpoint reflected raw input into HTML (XSS). I escaped input with `markupsafe.escape(name)` and added a Content-Security-Policy header

## Pytest
```bash
============================= test session starts ==============================
platform linux -- Python 3.12.3, pytest-7.4.2, pluggy-1.6.0 -- /home/rames/nighthawk/procedures-lab/venv/bin/python3.12
cachedir: .pytest_cache
rootdir: /home/rames/nighthawk/procedures-lab
configfile: pytest.ini
collecting ... collected 8 items

tests/test_endpoints.py::test_add_endpoint PASSED                        [ 12%]
tests/test_endpoints.py::test_fib_endpoint PASSED                        [ 25%]
tests/test_endpoints.py::test_item_crud PASSED                           [ 37%]
tests/test_endpoints.py::test_vulnerable_echo_reflection SKIPPED (Re...) [ 50%]
tests/test_endpoints.py::test_vulnerable_echo_fixed PASSED               [ 62%]
tests/test_utils.py::test_add_simple PASSED                              [ 75%]
tests/test_utils.py::test_fib_basic PASSED                               [ 87%]
tests/test_utils.py::test_db_crud PASSED                                 [100%]

========================= 7 passed, 1 skipped in 0.05s =========================
```