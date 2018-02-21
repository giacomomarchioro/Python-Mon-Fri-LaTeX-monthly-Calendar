# Python-Mon-Fri-LaTeX-monthly-Calendar
Python LaTeX monthly Mon-Fri calenadr generator. This script is able to generate A4 landscape monthly clalendar Monday to Friday using pdfLaTeX. 

![result](https://photos-5.dropbox.com/t/2/AAB_35W6dtf0GPBteiNGfAmG0WkskAfVgHHiPnDMhMBJ3A/12/71424109/jpeg/32x32/3/1519239600/0/2/April2015.jpg/ENvswzcYkA4gAigC/gHZsNPtX6CdoQERvB3Hu9dwp5vCo56h9uKLCIOQPRKE?dl=0&size=1280x960&size_mode=3)

## Important Note
> #### **To run this script [pdfLaTeX](http://en.wikipedia.org/wiki/PdfTeX) is required**

## How it works.
Inside the script there are two functions `print_month` and `print_year` simply pass the prameters to these two functions and they will produce a .tex file and a .pdf.
Here an example.

### Print a .pfd of one month
If you want to print the .pdf for instance of February 2016,open terminal in the same folder of the script. And call Python. Import the function and pass to print_month the year and the month in numbers.

```shell
user@user: path$ python
Python 2.7.6 (default, Mar 22 2014, 22:59:38) 
[GCC 4.8.2] on linux2
Type "help", "copyright", "credits" or "license" for more information.
```
```python
>>> from monfrical import print_month
>>> print_month(2016,2)
```

### Print a .pfd of one month for every month of a specific year
If you want to print the .pfd of one month for every month of a specific year for instance 2015, open terminal in the same folder of the script. Call Python. Import the function and pass to print_year the year  in numbers.
```
user@user: path$ python
```
````python
Python 2.7.6 (default, Mar 22 2014, 22:59:38) 
[GCC 4.8.2] on linux2
Type "help", "copyright", "credits" or "license" for more information.
>>> from monfrical import print_month
>>> print_year(2015)
```
