# security-report-generator

A small utility to automate the repetitive tasks that you shouldn’t be wasting time over, which generates a word security report by using a knowledge base(CSV) which contains a detailed list of vulnerability summary (names, description, remediation steps etc).  

## Goal

After testing, making a report manually consumes huge amount of time especially when we deal with same set of vulnerabilities found during other engagements.

Due to this, we have automated certain process of report making like title, description, severity, reference, remediation and poc of vulnerabilities and other generic content present in the report.

List of files required to automate the report are explained below.
- **poc**: Directory containing poc's for all vulnerabilities
- **master-template.docx**: A Docx template with all the contents and placeholders
- **ptkb.csv**: Compiled list of vulnerabilities with all the required details.
- **vuln-template.docx**: A Docx template with the vulnerability format. 
- **vulns.txt/vuln.csv**: A list of our findings in txt / csv format.
- **autogen.py**: python utility to generate the report according to our template format.

## Features

- multi image support for poc
- caption for each image in poc
- sanitise special characters in ptkb.csv

## Types

we have made 3 versions based on input type.

1. txt file as input
2. csv file as input
3. csv file as input with sanitization

### Txt file as input

txt file must contain a list of vulnerability IDs (from ptkb.csv) of findings that goes in the report, Here POC of vulnerabilities needs to added manually.

**Note:** autogen can only add a single image as POC for each vulnerability.

### CSV file as input

CSV file must contain 2 columns, in 1st colum--a list of vulnerability IDs (from ptkb.csv) of findings that goes in the report and 2nd column-- An Image name of POC.

### CSV file as input with sanitize

Same as above, this is needed in case when ptkb.csv contains vulnerability details with special characters such as '<' '>' '&'.

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
- change master-template.docx and vuln-template.docx to your report format and add placeholders.
- alter code in (context) if changes have to be made to placeholder

for ex: 
    
In master-template.docx, if you want to add a placeholder to display document version then add {{ version }}.
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

## Demo

![](autogen_v2.1.1.gif)
