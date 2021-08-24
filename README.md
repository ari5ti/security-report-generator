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
