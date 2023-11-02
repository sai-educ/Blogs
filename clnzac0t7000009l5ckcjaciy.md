---
title: "Techniques for Automated Data Cleaning and Analysis"
datePublished: Sat Oct 21 2023 00:11:52 GMT+0000 (Coordinated Universal Time)
cuid: clnzac0t7000009l5ckcjaciy
slug: techniques-for-automated-data-cleaning-and-analysis
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1697846266662/94b529cd-f70e-4b4e-a71a-d5f8c5be6c73.png
tags: parse, data-analysis, formatting, data-integrity

---

Data integrity and cleanliness cannot be overstated. Every dataset, especially educational datasets with live student performance reports, contains noise, discrepancies, or formatting issues. Addressing these problems manually can be a time-consuming and error-prone process. Here, I discuss simple techniques and methods to streamline the process of cleaning, formatting, and understanding data without the need for intensive manual intervention.

The main steps include:

Organizing the directory, encoding and parsing, then perform cleaning and save the processed data to the predefined directory. For demonstration purposes, I supplied a zip of an existing dataset, which contains adult learner assessment records from the [Massachusetts Adult Proficiency Tests – College and Career Readiness (MAPT-CCR)](https://blogs.umass.edu/aclstesthelp/files/2019/05/MAPT_SR_Reading_InterpGuide_V3.pdf), which is being spearheaded and maintained by UMass Amherst EDUC Distinguished Professor [Stephen Sireci](https://www.umass.edu/education/about/directory/stephen-sireci) and Research Professor [April Zenisky](https://www.umass.edu/education/about/directory/april-zenisky) from the department of Research, Educational Measurement, & Psychometrics ([EPRA](https://www.umass.edu/education/department-educational-policy-research-administration-epra)).

In simpler terms, the records are pivotal in understanding the proficiency and readiness of adult learners for college and career opportunities, as they can sometimes contain inconsistencies due to the vast number of entries and the diverse sources from which they are collated. Utilizing my technique could ensure that the records are accurate, consistent, and ready for in-depth analysis.

First, we will clean the database labels.

```python
import os
import pandas as pd

def clean_report_files(directory):
    # Create a new "Cleaned" folder inside the specified directory
    cleaned_directory = os.path.join(directory, "Cleaned")
    if not os.path.exists(cleaned_directory):
        os.makedirs(cleaned_directory)
    
    # Listing all files in the dir
    files = [f for f in os.listdir(directory) if os.path.isfile(os.path.join(directory, f)) and "Report" in f and f.endswith('.tsv')]
    
    # Process each "Report" file
    for file in files:
        file_path = os.path.join(directory, file)
        
        # Attempting to read
        try:
            df = pd.read_csv(file_path, sep="\t", encoding="utf-8", skiprows=5)
        except Exception as utf8_err:
            # Another attempt, using another encoding. If the one above fails, this should do the trick
            try:
                df = pd.read_csv(file_path, sep="\t", encoding="ISO-8859-1", skiprows=5)
            except Exception as iso_err:
                print(f"Error parsing file: {file}. UTF-8 error: {utf8_err}. ISO-8859-1 error: {iso_err}. Skipping...")
                continue

        # Save the cleaned data to a new folder
        cleaned_file_path = os.path.join(cleaned_directory, file)
        df.to_csv(cleaned_file_path, sep="\t", index=False)

directory = "location"
clean_report_files(directory)
```

Stage 2 is validation, where I show file meta for manual verification. Upon real human validation of file structure, the next steps can be taken for further processing.

```python

def list_files_and_sizes(directory):
    # To ensure the location exists
    if not os.path.exists(directory):
        print(f"The directory {directory} does not exist.")
        return

    # Listing all files - for manual validation
    files = [f for f in os.listdir(directory) if os.path.isfile(os.path.join(directory, f))]
    
    # verify the counting vs human counting
    print(f"Total number of files: {len(files)}\n")
    
    # Print file names and their sizes
    for file in files:
        file_path = os.path.join(directory, file)
        size = os.path.getsize(file_path)
        print(f"File: {file}\tSize: {size} bytes")

directory = "path/Cleaned"
list_files_and_sizes(directory)
```

Until next time.