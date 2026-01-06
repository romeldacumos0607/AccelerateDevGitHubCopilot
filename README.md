# Library App

## Description

Library App is a .NET 8.0 console application that implements a library management system using clean architecture principles. The application allows users to search for patrons, view their details, manage book loans, and perform various library operations through an interactive console interface.

The system is built with a layered architecture approach, separating concerns between domain logic, data access, and presentation layers. It uses JSON files for data storage and implements the Repository pattern for data access operations.

## Project Structure

* **src/**
  * **Library.ApplicationCore/**
    * **Entities/** - Domain entities (Patron, Loan, etc.)
    * **Enums/** - Domain enumerations
    * **Interfaces/** - Repository and service interfaces
    * **Services/** - Business logic services
  * **Library.Console/**
    * **Json/** - JSON data files for storage
    * ConsoleApp.cs - Main console application
    * Program.cs - Application entry point and DI configuration
    * ConsoleState.cs - State machine enumeration
    * CommonActions.cs - User action flags
    * appSettings.json - Configuration file
  * **Library.Infrastructure/**
    * **Data/** - Data access implementations
      * JsonData.cs - JSON file operations
      * JsonLoanRepository.cs - Loan data access
      * JsonPatronRepository.cs - Patron data access
* **tests/**
  * **UnitTests/** - Unit test project with test factories

## Key Classes and Interfaces

### Core Domain
- **Patron** - Represents library patrons with membership information and loan collections
- **Loan** - Represents book loan records
- **PatronService** - Contains business logic for patron operations
- **LoanService** - Contains business logic for loan operations

### Console Application
- **ConsoleApp** - Main application class implementing state machine pattern for user interactions
- **ConsoleState** - Enumeration defining application states (PatronSearch, PatronDetails, LoanDetails, etc.)
- **CommonActions** - Flags enumeration for available user actions

### Data Access
- **JsonData** - Handles JSON file operations and data management
- **JsonLoanRepository** - Implements loan repository interface for JSON storage
- **JsonPatronRepository** - Implements patron repository interface for JSON storage
- **IPatronRepository** - Interface for patron data operations
- **ILoanRepository** - Interface for loan data operations

### Business Services
- **IPatronService** - Interface for patron business operations
- **ILoanService** - Interface for loan business operations

## Usage

### Prerequisites
- .NET 8.0 SDK
- Visual Studio Code or Visual Studio

### Running the Application

1. Clone the repository
2. Navigate to the solution directory
3. Restore dependencies:
   ```bash
   dotnet restore
   ```
4. Build the solution:
   ```bash
   dotnet build
   ```
5. Run the console application:
   ```bash
   cd src/Library.Console
   dotnet run
   ```

### Application Features

The console application provides the following functionality:

- **Patron Search**: Search for library patrons by name
- **Patron Details**: View detailed patron information including membership status and active loans
- **Loan Management**: View loan details, extend due dates, and process returns
- **Membership Management**: Renew patron memberships

### Navigation

The application uses a command-based interface:
- **s** - Search for patrons
- **m** - Renew patron membership
- **e** - Extend book loan
- **r** - Return loaned book
- **q** - Quit application
- **Numbers** - Select items from lists

### Testing

Run the unit tests:
```bash
cd tests/UnitTests
dotnet test
```

The test project includes factory classes for creating test data and uses xUnit for testing framework with NSubstitute for mocking.

## License

This project is licensed under the MIT License - see the LICENSE file for details.