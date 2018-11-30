# verif_temps3
NOTE: this following text is a copy of the beginning of my program 
which is called "verif_temps3_for_mooc.py". 
I explain you the context and I tried to summarize what each function does.
The program really starts with line "# Different imports:"


# Preamble:
"""
This is a cleaned version of my program to show you my code because I'm sure
it can be improved (maybe with classes?).
I already removed many 'global' variables and I reduced pieces of this code.
I modified this code by learning from the excellent MOOC on Python :-)

Please don't hesitate to criticize/review this code and ask for everything
you find weird !
"""


# To explain you the context:
"""
I'm working in a chemical laboratory of the CNRS as engineer assistant,
my colleague and I manage 2 diffractometers in our scientific service.
Many samples are analyzed on one of them.
Each day: people prepare samples in holders, then we check them and put them
inside the diffractometer. We program them on the driving software and analyses
are done during the night (thanks to the autochanger, a robot that puts samples
in position under the X-ray beam).

We use different small "house" programs to check the existence of files,
send results files by email, print results (with a network printer),
translate files, copy files on a server... All these programs were coded
in Fortran by a retired researcher and I need to adapt them in Python (I really
don't want to learn how to use Fortran).

I already did a first program to automatically send results files to people,
by typing their trigram (3 letters), because everybody in my lab has a trigram
and an email address (with the same string after the '@').
It works but it can be improved too, I will modify it later.
"""


# Concerning this program:
"""
Now I'm doing a house program to check that sample numbers have not been
analyzed before, because if it appends we'll lose lot of time to manage
our database (we keep all diffractograms from 1999).
So the aim of this program is to check sample numbers, trigrams, unwanted
characters, each sample number must respect a format, the existence of 'bsml'
files which are created by our driving software, and at the end we want to know
when all analyses are finished. We also want to know when there is an error.

This program contains 12 functions and only the 2 first are launched at the end
because other functions are launched from the second one.
I don't know if it's the best solution in terms of bit-efficiency, but in the
first version of this program I launched all functions at the end.

Each function is documented (I hope enough) but I need to add that 'xjob' file
is an XML file containing all information typed in the driving software among:
sample position, number and description, 'bsml' experiment filename,
sample-holder, username and user group. One 'xjob' file can contain between 1
and N programmed samples (often less than 30).
Brut data files are saved with 'brml' extensions, but they are converted into
'raw' files with another program.
The only way to open 'bsml' experiment files when we don't have the driving
software on our computer is to replace 'bsml' extension by 'zip'. We can find
XML files inside the 'zip' where we get the duration of each 'bsml' file.
"""


# 12 functions:
"""
- First function only displays last modification of this file
- In second one we ask user to type 'xjob' filename without its extension and
we start counting duration of the program
- Then third function checks the existence of this 'xjob' filename
- 4th function opens this file and cleans lines
- Functions 5, 6 and 7 check unwanted characters, sample numbers formats and
trigrams
- Functions 8 and 9 check the existence of these numbers in our database and
'bsml' experiment files
- Function 10 fix an error when 'bsml' filename has a space, copy 'bsml' files
in a folder and convert them into 'zip' files. There are 2 conditions because
if the folder is empty (at the beginning) it doesn't work.
- Function 11 calculates durations of each program, adds them with constants
to current date and time to determine the estimated end date & time
of all analyses.
- Function 12 is used to display the result of last function under format:
"Fin des analyses prévue le: dd/mm/yyyy, vers HH:MM:SS"
with minutes and seconds on 2 digits, because I had only 1 digit
when minutes or seconds were lower than 10. I don't mind for hours.
I know this can be improved with hour formats but I don't know exactly how.
- At the end: programs counts and displays its duration (between 1.5 and
2 seconds) on my computer

I will add a display of my program when it's well-executed (with errors).
"""
