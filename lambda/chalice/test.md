# Test Chalice

### Requirement/Dependencies

    pip install pytest

### Files
create a new `tests/` directory and create a `tests/__init__.py` and a `tests/test_app.py` file.

    mkdir tests
    touch tests/{__init__.py,test_app.py}

### Run

    py.test tests/test_app.py

### Run test with print/logs using flag `-s`

		py.test tests/test_app.py -s
