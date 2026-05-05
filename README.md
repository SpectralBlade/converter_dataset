# CSON Converter - Test Datasets

## Overview

This repository contains comprehensive datasets used for automated mass testing of the conversion service inside CSON web application. The datasets are designed to validate conversions between CSV, JSON, and XML formats, both with and without the application of data modification patterns.

The repository is divided into two primary directories:
* **1. Basic Conversion**: Contains 40 raw CSV files alongside their exact JSON and XML equivalents. These are used to test standard, uninterrupted conversion paths.
* **2. Conversion With Patterns**: Contains 40 raw CSV files, corresponding modification pattern configurations (stored as JSON arrays), and the expected JSON and XML outputs after applying the patterns.

## Prerequisites

* A Java Spring Boot project containing the backend logic.
* JUnit 5 configured for parameterized testing within the project.
* Git installed on your local machine.

## Installation and Setup

### Step 1: Clone the Repository

Open your terminal or command prompt and clone this repository to your local machine:
```bash
git clone https://github.com/SpectralBlade/converter_dataset
```

### Step 2: Transfer Files to Your Project

Navigate into the cloned repository. You will find two folders: `1. Basic Conversion` and `2. Conversion With Patterns`.
Copy both of these folders and paste them into the test resources directory of the CSON backend project.

The exact target path must be:
`src/test/resources/`

### Step 3: Verify the Directory Structure

For the test suite to locate the files dynamically, your project's file tree must match the following structure exactly:
```text
backend/
└── src/
    └── test/
        └── resources/
            └── test_files/
                ├── 1. Basic Conversion/
                │   ├── csv/
                │   ├── json/
                │   └── xml/
                └── 2. Conversion With Patterns/
                    ├── csv/
                    ├── json/
                    ├── patterns/
                    └── xml/
```

## Running the Tests

Once the datasets are correctly placed in the `src/test/resources/` directory, they will be automatically detected by the parameterized test suite (class named `ConversionFrontendMassTest`).

You can execute the mass tests  with the other logic tests or separately from your Integrated Development Environment (IDE) such as IntelliJ IDEA or Eclipse, or by using your build tool via the command line.

**Using Maven:**
```bash
mvn test -Dtest=ConversionFrontendMassTest
```

### Test Execution

When the test suite runs, it will process the files as follows:
* **Basic Dataset**: The suite iterates through files 1 to 40 and tests all 6 possible conversion directions (e.g., CSV to JSON, JSON to CSV, XML to JSON, etc.), assuming no data loss.
* **Patterns Dataset**: The suite applies the corresponding modification rules from the `patterns/` directory. It strictly tests the forward conversion paths (CSV to JSON and CSV to XML).