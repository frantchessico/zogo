# Zogo - Custom Validation Library for Go

Zogo is a custom validation library for Go that allows you to define and apply various validation rules to your data. It is inspired by Zod's validation.

## Features

- Define custom validation rules for different types of data.
- Easily validate fields using predefined or custom validation functions.
- Intuitive and flexible way to validate complex data structures.

## Installation

To use Zogo in your Go project, you can install it using the `go get` command:

```sh
go get github.com/frantchessico/zogo

```
## Usage
Here's an example of how you can use Zogo to define and validate data:


```go

package main

import (
    "fmt"
    "github.com/frantchessico/zogo"
)

func main() {
    validator := zogo.NewRuleValidator()

    validator.AddRule("age", validation.MinValueValidator(18))
    validator.AddRule("name", validation.StringNotEmptyValidator)
    validator.AddRule("email", validation.EmailSchema)
    validator.AddRule("password", validation.MinValueValidator(4))

    data := map[string]interface{}{
        "age":     25,
        "name":    "John Doe",
        "email":   "john@example.com",
        "password": "secretpw",
    }

    err := validator.Validate(data)
    if err != nil {
        fmt.Println("Validation failed:", err)
    } else {
        fmt.Println("Validation successful!")
    }
}
```

## Available Validation Rules

Zogo provides the following validation rules that you can use to validate your data fields:

- `validation.MinValueValidator(minValue int)`: Validates that a numeric value is greater than or equal to the specified minimum value.
- `validation.StringNotEmptyValidator(value interface{})`: Validates that a string value is not empty.
- `validation.EmailSchema(value interface{})`: Validates that a string value is a valid email address.
- `validation.BooleanSchema(value interface{})`: Validates boolean values (true or false).
- `validation.StringSchema(value interface{})`: Validates string values.
- `validation.NumberSchema(value interface{})`: Validates numeric values.


## Author

This library is authored by Francisco Inoque.
