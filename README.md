# security-report-generator

A small utility to generate a word security report by using a knowledge base(CSV) which contains a detailed list of vulnerability summary (names, description, remediation steps etc).  

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

## Types

we have made 3 versions based on input type.

1. txt file as input
2. csv file as input
3. csv file as input with sanitization

### Txt file as input

txt file contains a list of **ids** associated with found vulnerabilities which need to be added to the report will be passed to the autogen due to which poc has to be added manually.

### CSV file as input

csv file contains a list of **ids** associated with found vulnerabilities and poc in different columns which need to be added to the report will be passed to the autogen(1 image as poc/vuln).

### CSV file as input with sanitize

csv file contains a list of **ids** associated with found vulnerabilities and poc in different columns which need to be added to the report will be passed to the autogen(1 image as poc/vuln) and sanitization of some special characters if not done may cause trouble opening the docx file.

## Usage

    - git clone https://github.com/ari5ti/security-report-generator.git
    - update ptkb.csv file with the list of vulns and associate ids to it.
    - change **master-template.docx** and **vuln-template.docx** to your report format and add placeholders.
    - choose the type of input to use and replace **autogen.py** and **vuln.csv/vuln.txt** accordingly.
    - alter code if changes have to be made to placeholders or give empty input to omit.
    - python autogen.py 
