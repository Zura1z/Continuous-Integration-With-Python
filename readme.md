## Getting Started

This repo contains a simple code for CI using Python. 
## Problem Definition
##### Imagine your team is working on a simple calculator app. Your task is to write a library of basic mathematical functions: addition, subtraction, multiplication, and division. You don’t care about the actual application, because that’s what your peers will be developing, using functions from your library.


## Tutorial

Thanks to RealPython for an amazing tutorial on Continous Integration. 

Here's the link to the tutorial: <a>https://realpython.com/python-continuous-integration/</a> 
## Follow these steps

If you want to follow this step by step, here's how you can do so:
*  Create a Repo
 1. Set Up a Working Environment
 
  ```sh
  python3 -m venv calculator
  ```
* 2. Write a Simple Python Example in file <b> calculator.py</b>

  ```python
    def add(first_term, second_term):
        return first_term + second_term

    def subtract(first_term, second_term):
        return first_term - second_term
    def multiply(first_term, second_term):
    return first_term * second_term
  ```
* 3. Commit as "Add functions for addition and subtraction"
* 4. Writing Unit tests 
    ```sh
    pip install flake8 pytest pytest-cov
    pip freeze > requirements.txt
    ```
* 5. To run your linter, execute the following:
    ```sh
    flake8 --statistics
    ```
* 6. Create a file called test_calculator.py and write following lines:
    ```python
    class TestCalculator:

    def test_addition(self):
        assert 4 == calculator.add(2, 2)

    def test_subtraction(self):
        assert 2 == calculator.subtract(4, 2)
    def test_multiplication(self):
    assert 100 == calculator.multiply(10, 10)
    ```
* 7. The following command runs your test:
    ```sh
    pytest -v --cov
    ```
* 8. Now you have to Connect to Circle. A .yml file uses a data serialization language, YAML, and it has its own specification. The goal of YAML is to be human readable and to work well with modern programming languages for common, everyday tasks. In a YAML file, there are three basic ways to represent data:
     * 1. Mappings (key-value pairs)
     * 2. Sequences (lists)
     * 3. Scalars (strings or numbers)
     * 4. It is very simple to read:

    *    Indentation may be used for structure.
Colons separate key-value pairs.
Dashes are used to create lists. Make a .circleci and a config.yml file with the following content:
    ```yml
    version: 2
    jobs:
        build:
            docker:
            - image: circleci/python:3.7

            working_directory: ~/repo

            steps:
            # Step 1: obtain repo from GitHub
            - checkout
            # Step 2: create virtual env and install dependencies
            - run:
                name: install dependencies
                command: |
                    python3 -m venv venv
                    . venv/bin/activate
                    pip install -r requirements.txt
            # Step 3: run linter and tests
            - run:
                name: run tests
                command: |
                    . venv/bin/activate
                    flake8 --exclude=venv* --statistics
                    pytest -v --cov=calculator
    ```
* 9. Now commit.
* 10. Follow the tutorial in the link above for better understanding of CI.
## Congratulations! 
### You have just learned Countinous Integrations with Python.


