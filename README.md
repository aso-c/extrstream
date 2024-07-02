# extrstream

iostream library extras:

- tiny implementation of format string output similar as boost::format or fmt(ex-cppformat, [https://fmt.dev/latest/index.html](https://fmt.dev/latest/index.html)) and  pprintpp ([https://github.com/tfc/pprintpp](https://github.com/tfc/pprintpp)).
- conversion istream, ostream, ifstream, ofstream to stdio.h pure C type FILE* (GCC extention);
- implicit conversion from std::string to const char* if used in aso::format() only;
  or combined with operator % () in output expression.


for generating r-value temporary object of
  the class template aso::Formatter

# Usage Description
Object of the variadic template class aso::Formatter provides C-style printf() output formatting.
There are two ways to create a temporary aso::Formatter object in an ostream output expression:

- procedure aso::format("format_string", ...) only with madatory format string and
  any number of parameters for output;
- procedure aso::format("format_string") as above, combined with with an expression
  consisting of a some number of %() statements with output parameters.

Both of this methods generate temporary object of the variadic template class aso::Formatter
with imlicit conversion std::string to const char*.
Direct creating object of aso::Formatter class is not provide this conversion!

## Usage example

Source:
```
    std::string str2 = "Test_str2";

cout << format("Example output: output%i: %s, output%i: %s", 1, "Test_str1") % 2 % str2 << endl;
```

Output:
```
Example output: output1: Test_str1, output2: Test_str2
```
