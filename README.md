# Banking System: Project Documentation


## SimpleBankingSystemDiagram
![SimpleBankingSystemDiagram](https://github.com/ZhichenLiang/BankingSystem/assets/80897467/abd474a6-63fe-420e-b928-16410f02059c)

## Overview
The project provides a simple, thread-safe banking system with functionality to perform common banking operations like account creation, balance checks, and transactions. It features an abstract Account class, a Bank class for managing multiple accounts, and unit tests to validate the functionality.

## Key Features

### Abstract Account Class
The Account class is abstract because it may contain some shared logic, but at the same time, it may not be a complete implementation, requiring subclasses to provide any missing implementations.

Thread-Safety
* ReentrantReadWriteLock: This lock allows multiple threads to read data simultaneously while ensuring that only one thread can write data at a time. This is an advantage over synchronized methods as it provides better scalability.

Note
* Balance: The balance is maintained as a double, which is a floating-point data type. For financial calculations, it's advisable to use BigDecimal to avoid rounding errors.

### Bank Class
The Bank class manages multiple accounts and provides methods for account creation (openCommercialAccount, openConsumerAccount), account validation (authenticateUser), and transactions (credit, debit).

Thread-Safety
* LinkedHashMap: Account details are stored in a synchronized LinkedHashMap. For better performance in a highly concurrent environment, ConcurrentHashMap can be used.

* AtomicLong: Used for generating unique account numbers. Ensures that multiple threads can update the value concurrently without conflicts.

## Unit Tests

### SampleTest
Basic unit tests are included to check the account creation, debit, and credit functionalities.

### ConcurrentTest
This test suite includes tests for validating the thread-safety of the bank system.

## Security Considerations

* PIN Encryption: The PIN used for account validation should be encrypted for security reasons.

* Authorization Tools: In addition to PIN, other authentication & authorization tools like Spring Security, OAuth2 can also be used.

## Future Enhancements

* Error Handling: The application could include better error handling, for example, throwing a custom InsufficientFundsException in the debit function.

* Caching: If frequent access to the same accounts is expected, a caching layer could be introduced.

* BigDecimal: Replace the balance's double data type with BigDecimal for more accurate financial calculations.

## Conclusion
This project aims to provide a thread-safe, scalable, and extensible banking system. With minor enhancements, it can be adapted for more complex and high-concurrency environments.
