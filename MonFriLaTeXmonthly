# -*- coding: utf-8 -*-
"""
Created on Fri Feb  6 18:56:16 2015
Python LaTeX monthly Mon-Fri calenadr generator. This script is able to generate A4
landscape monthly clalendar Monday to Friday using pdfLaTeX. PdfLaTeX is hence
required to run this script.
@author: Giacomo Marchioro
"""
import calendar
import os
import sys
path = os.path.abspath(os.path.dirname(sys.argv[0]))

def print_month(year,month_number):
    """ This function generate a .tex file and print a .pdf A4
    landscape monthly clalendar Monday to Friday using pdfLaTeX of a specific
    year(xxxx) and month (1-12)
    """
    week=0
    monthname=str(calendar.month_name[month_number])
    cal=calendar.Calendar()
    month=cal.itermonthdays(year,month_number)#month is an iterable generator
    first_7_element=[month.next() for i in range(7)]#this is required in case the first week is empty
    extrarowheight='85'
    tabcolsep='72'
    if first_7_element==[0,0,0,0,0,0,1]:
        if month_number==2:
            extrarowheight='110'#in this particular case we need only 4 rows so we can add some more height
            week=1
        else:
           pass
       
    elif first_7_element==[0,0,0,0,0,1,2]: #if the week starts on Saturdarday...
        if month_number in [11,4,6,10,2]:#...and the month has 30 days...
            extrarowheight='110'#...we can use only 4 rows insead of 5 and hence add more space!
            week=1
        else:
            pass
    else:
        month=cal.itermonthdays(year,month_number)#we have to re-create the object because month.next() eliminates
        #the elements
    #start writing on a .tex file
    with open(path+'/'+monthname+str(year)+'.tex','w') as f:
        f.write(r'\documentclass[landscape,a4paper]{article}'+'\n')
        f.write(r'\usepackage[landscape,margin=0.5in]{geometry}'+'\n')
        f.write(r'\usepackage{array}'+'\n')
        f.write(r'\begin{document}'+'\n')
        f.write(r'\pagestyle{empty} % Removes the page number from the bottom of the page '+'\n')
        f.write(r'\noindent'+'\n')
        f.write(r'\textsc{\LARGE %s} \textsc{\large %s}' %(monthname,str(year))+'\n')
        f.write('\n')
        f.write('\n')
        f.write(r'\setlength{\tabcolsep}{57pt}'+'\n')
        f.write(r'\begin{tabular}{c c c c c }'+'\n')
        f.write(r' Monday &  Tuesday & Wednesday  & Thursday & Friday \\'+'\n ')
        f.write(r' \end{tabular}'+'\n')
        f.write(r'\setlength{\tabcolsep}{%spt}'%(tabcolsep)+'\n')
        f.write(r'\setlength{\extrarowheight}{%spt}'%(extrarowheight)+'\n')
        f.write(r'\begin{tabular}{|r|c|c|c|c|}'+'\n')
        f.write(r'\hline     \large{')
        count=1
       
        for i in month:
            print count,i
            print 'WEEK:',week
        
            if count%6==0:
                count+=1
                print 'skipped'
            elif count%7==0:
                count=1              
                week+=1
                print 'end week'
            elif count==5 and week==4:
                print 'DONE'
                if i==0:
                    f.write(r' }\\'+'\n'+'\hline')
                    count+=1
                else:
                    f.write(str(i)+r'}\\'+'\n'+'\hline')
                    count+=1
            elif count%5==0: #new row in LaTeX
                f.write(str(i)+r'}\\'+'\n'+'\hline     \large{')
                count+=1
            else:
                if i==0:#we don't want to see zeros around the tables!!
                    f.write(' '+r'}& \large{')
                    count+=1
                else:# new element
                    f.write(str(i)+r'}& \large{')
                    count+=1      
        f.write(r'\end{tabular} '+'\n')
        f.write(r'\end{document}' +'\n')
    os.system('pdflatex '+monthname+str(year)+'.tex')

    
def print_year(year,start=1,stop=12):
    ''''
    This function simply iterate print_month() function over a specified year.
    A narrow range of months can be printed using the others two parameters.
    '''
    for i in range(start,stop):
        print_month(year,i)
