# Quickstart

## Introduction
The **Data Joy Specification (DJS)** provides a standardized way to describe **tabular data assets** using **JSON or YAML**.

## Basic Structure
A **DJS document** defines a **Table Object**, containing metadata about the dataset and its **columns**.

### Example (YAML):
```yaml
djs: "1.0.0"
name: "Employee"
domain: "Human Resources"
physicalName: "EMPL"
columns:
  - name: "EmployeeID"
    datatype: "INT"
    physicalName: "ID"
    physicalType: "INTEGER"
    primaryKey: true
  - name: "FirstName"
    datatype: "STRING"
    physicalName: "FNAME"
    physicalType: "VARCHAR(100)"
  - name: "LastName"
    datatype: "STRING"
    physicalName: "LNAME"
    physicalType: "VARCHAR(100)"
  - name: "Salary"
    datatype: "FLOAT"
    physicalName: "SALARY"
    physicalType: "NUMERIC(10, 3)"
  - name: "DepartmentID"
    datatype: "INT"
    physicalName: "DEPID"
    physicalType: "INTEGER"
    partitionKey: true
``` 

## Core Elements

### Table Object (Root Object)
| Field Name | Type   | Description |
|------------|--------|-------------|
| `djs` | string (version) | **REQUIRED**. Specifies the DJS version. |
| `name` | string | **REQUIRED**. Name of the tabular data asset. |
| `columns` | array of Column Objects | **REQUIRED**. List of columns in the dataset. |

### Column Object
Each column is defined with the following attributes:

| Field Name | Type   | Description |
|------------|--------|-------------|
| `name` | string | **REQUIRED**. Column name. |
| `datatype` | string | **REQUIRED**. Logical type: `BOOLEAN`, `INT`, `FLOAT`, `STRING`, `DATE`. |


## Metadata Annotations
DJS provides two **annotation vocabularies**:

### Logical Metadata
| Annotation | Applies To | Type | Description |
|------------|------------|------|-------------|
| `domain` | Table | string | Specifies the domain of the data asset. |
| `primaryKey` | Column | boolean | Marks a column as a **primary key** (default: `false`). |

### Physical Metadata
| Annotation | Applies To | Type | Description |
|------------|------------|------|-------------|
| `physicalName` | Table, Column | string | Name of the element in the source datastore. |
| `physicalType` | Table, Column | string | Type in the source datastore (`TABLE`, `VIEW`, `VARCHAR`, etc.). |
| `partitionKey` | Column | boolean | Marks a column as a **partition key** (default: `false`). |

## Versioning
DJS follows **Semantic Versioning 2.0.0**, ensuring backward compatibility for minor versions (e.g., `1.0.x`).

## Get Started
1. **Define** your tabular data asset using **JSON or YAML**.
2. **Annotate** columns with **logical and physical metadata**.
3. **Validate** your schema using the [json schema](..schemas/1.0.0/schema.json) associated with DJS.

For more details, check the full [Data Joy Specification](../versions/1.0.0.md)!

