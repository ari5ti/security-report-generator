# security-report-generator

A small utility to automate the repetitive tasks that you shouldn’t be wasting time over, which generates a word security report by using a knowledge base(CSV) which contains a detailed list of vulnerability summary (names, description, remediation steps etc).  

## Demo

![](autogen_v2.1.1.gif)

## Goal

After testing, making a report manually consumes huge amount of time especially when we deal with same set of vulnerabilities found during other engagements.

Due to this, we have automated certain process of report making like title, description, severity, reference, remediation and poc of vulnerabilities and other generic content present in the report.

List of files required to automate the report are explained below.
- **poc**: Directory containing poc's for all vulnerabilities
- **template.docx**: A Docx template with all the contents and placeholders
- **ptkb.csv**: Compiled list of vulnerabilities with all the required details.
- **vuln.csv**: A list of our findings in csv format.
- **autogen.py**: python utility to generate the report according to our template format.

## Features

- multi image support for poc
- caption for each image in poc
- sanitise special characters in ptkb.csv

## Types

we have made 2 versions based on input type which can be found in releases.

1. txt file as input
2. csv file as input

**NOTE**: second version will be used for further developments.

## Requirements

``` pip install python-docx docxptl ```

## Try it

- choose the type of input from the release and download the zip file or for latest version do: 
```
git clone https://github.com/ari5ti/security-report-generator.git
python autogen.py
```

## Custom Usage

- choose the type of input from the release and download the zip file
- update ptkb.csv file with the list of vulnerabilities and associate ids to it.
- change template.docx(for older version - master-template.docx and vuln-template.docx) to your report format and add placeholders.
- alter code in (context) if changes have to be made to placeholder

for ex: 
    
In template.docx, if you want to add a placeholder to display document version then add {{ version }}.
In autogen.py context, add version placeholder and get value to be rendered from the user input function as shown below. 
```
context = {
        'service': service,
        'version': ver,
        }
        
def user_input():
    global ver
    ver = input("Enter document version: ")
```

- if you do not need to use certain placeholders provide blank input for autogen.py.
