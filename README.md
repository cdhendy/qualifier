Module 2 - Challenge 2 : Loan Qualifier
=======================================

## Purpose

This application was designed with the goal of determining what loans are available to a prospective loan customer. 

---

## Technologies

This application was programmed in Python, and utilized the Fire and Questionary libraries. The Pytest framework was used for testing.   

---

## Installation Guide


You'll need to install some libraries before you can start using the application, specifically [Fire](https://google.github.io/python-fire/) and [Questionary](https://pypi.org/project/questionary/). 

To install Fire type the following in your terminal:

```python
pip install fire
```
To install Fire with conda:

```python
conda install fire -c conda-forge
```



To install Questionary type the following in your terminal:

```python
pip install questionary
```

This should satisfy the libraries required to run the application. 


---

## Examples


The block of code below demonstrates loading the daily rate sheet:

```python
def load_bank_data():

    csvpath = questionary.text("Enter a file path to a rate-sheet (.csv):").ask()
    csvpath = Path(csvpath)
    if not csvpath.exists():
        sys.exit(f"Oops! Can't find this path: {csvpath}")

    return load_csv(csvpath)
```

The below block of code demonstrates the line of questioning that should filter out the daily rate sheet:

```python
    credit_score = questionary.text("What's your credit score?").ask()
    debt = questionary.text("What's your current amount of monthly debt?").ask()
    income = questionary.text("What's your total monthly income?").ask()
    loan_amount = questionary.text("What's your desired loan amount?").ask()
    home_value = questionary.text("What's your home value?").ask()
```

The below block of code then saves the list of loans to a new csv:

```python
    if len(qualifying_loans) == 0: 
        sys.exit("You do not have any qualifying loans. The program will now close.") 

    csvpath = questionary.confirm("Would you like to save the qualifying loans to a CSV file?").ask()
    if csvpath:
        questionary.confirm("Are you sure?").ask() ## confirmation for saving the file
        csvpath = questionary.text("Please enter the file path including the name of your file to save your CSV file:").ask()
        csvpath = Path(csvpath)
        save_csv(csvpath, qualifying_loans)
```

---

## Usage

Open your terminal and navigate to the folder conntaining `app.py`, then enter:

```python
python app.py
```

Follow the command promps as shown on the screen. 


---

## Contributors

Created by: Chris Henderson

Email: cdhendy@gmail.com

[LinkedIn](https://www.linkedin.com/in/chris-henderson123/)

---

## License

(c) Copyright 2021 Chris Henderson

Licensed under the MIT license:

    http://www.opensource.org/licenses/mit-license.php

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in
all copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN
THE SOFTWARE.
