AZ-104 Exam 
Microsoft Learn
Notes

## Azure Administration Tools Overview

Azure provides three main administration tools for managing resources:

1. **Azure Portal**
    - Graphical User Interface (GUI).
    - Allows resource creation, configuration, and management.
    - Provides wizards and tooltips for complex tasks.
    - Not suitable for automating repetitive tasks.
    
2. **Azure CLI (Command-Line Interface)**
    - Cross-platform command-line program.
    - Executes administrative commands on Azure resources.
    - Supports interactive usage and script automation.
    - Available via Azure Cloud Shell or local installation.
    
3. **Azure PowerShell**
    - PowerShell module for Azure resource management.
    - Requires PowerShell.
    - Offers Azure-specific commands (Azure Az module).
    - Supports interactive usage and script automation.
    - Available via Azure Cloud Shell or local installation.

## Choosing an Administrative Tool

When deciding on an administrative tool, consider the following factors:

- **Automation:** If you require automation of complex or repetitive tasks, use Azure PowerShell or Azure CLI.
- **Learning Curve:** Azure Portal is syntax-free; Azure PowerShell and Azure CLI require command knowledge.
- **Team Skillset:** Leverage existing expertise; if your team is familiar with PowerShell, Azure PowerShell is advantageous.

## PowerShell Scripting Essentials

PowerShell scripting entails creating text files with sets of commands in the PowerShell language to automate recurring tasks. This is particularly useful after gaining experience with PowerShell and identifying repetitive actions. Automating these tasks makes them reusable and efficient.

Key scripting elements include:

- **Variables:** Store and manipulate values; they can be used as command inputs.
- **Functions:** Named sequences of commands that produce outputs; they can be integrated into other commands.
- **Flow Control:** Manage execution paths using constructs like `If`, `ElseIf`, and `Else`.
- **Loops:** Perform iterative operations on arrays; conditional looping with `Do-While` loops.
- **Error Handling:** Create robust scripts that handle various error types using `Try` and `Catch`.
- **Expressions:** Vital for custom columns, sorting, and value representation.
- **.NET Integration:** PowerShell integrates powerfully with .NET and .NET Core.

PowerShell scripting empowers efficient task automation and system state management.

> **Note:** Advanced concepts like error handling and deeper integration are covered in later parts of the module.


# Notes 
## Bicep
Bicep provides **automatic dependency management**
