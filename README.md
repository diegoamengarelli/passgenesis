
# SafePassGen

![Python](https://img.shields.io/badge/Python-3.7%2B-blue)
![License](https://img.shields.io/badge/License-MIT-green)

**SafePassGen** is a Python package for generating secure, customizable passwords with various constraints. It also includes functionality to check the strength and vulnerability of passwords, making it a comprehensive tool for managing password security.

## Features

- Generate passwords with specific requirements:
  - Include or exclude numbers, lowercase, uppercase, and symbols.
  - Option to start passwords with a letter.
  - Avoid sequential characters.
  - Avoid duplicate characters.
  - Generate multiple passwords at once.
- Check password strength and vulnerability:
  - Evaluate password length and character variety.
  - Check against a list of common passwords and dictionary.
  - Identify sequential or repeated characters.

## Installation

You can install **SafePassGen** via pip:

\`\`\`bash
pip install SafePassGen
\`\`\`

Or clone the repository and install manually:

\`\`\`bash
git clone https://github.com/diegoamengarelli/passgenesis.git
cd secure_password
pip install .
\`\`\`

## Usage

### CLI Example

secure_password --quantity 1 --length 16 --uppercase  --lowercase --numbers --symbols --check-strength

w-ykR7?hcz^|><Xd

Strength: Strong

### Basic Usage

\`\`\`python
from securepassword import PasswordGenerator

# Create a password generator instance
generator = PasswordGenerator(length=12, include_numbers=True, include_lowercase=True,
                              include_uppercase=True, include_symbols=True,
                              no_duplicates=True, is_sequential=True, begin_with_letter=True, quantity=1)

# Generate a password
passwords = generator.generate_passwords()
print(passwords)  # ['A1b2C3d4E5!']
\`\`\`

### Advanced Usage

\`\`\`python
# Generate multiple passwords with specific constraints
generator = PasswordGenerator(length=16, include_numbers=True, include_lowercase=True,
                              include_uppercase=True, include_symbols=True, 
                              no_duplicates=False, begin_with_letter=False, quantity=5)

passwords = generator.generate_passwords()
print(passwords)  
\`\`\`

### Checking Password Strength

\`\`\`python
from securepassword import PasswordStrengthChecker

checker = PasswordStrengthChecker(common_passwords=["password", "123456"])
password = "A1b2C3d4E5!"
result = checker.check_strength(password)

print(result)
Output:
{
    "strength": "Strong",
    "score": 5,
    "suggestions": []
}
\`\`\`

## Configuration Options

### \`PasswordGenerator\`

- **length**: Length of the password(s) to be generated.
- **include_numbers**: Include numbers in the password.
- **include_lowercase**: Include lowercase characters in the password.
- **include_uppercase**: Include uppercase characters in the password.secure_password
- **include_symbols**: Include symbols in the password.
- **no_duplicates**: Ensure no duplicate characters within the password.
- **begin_with_letter**: Ensure the password starts with a letter.
- **only_numbers**: Generate passwords containing only numbers.
- **quantity**: Number of passwords to generate.

### \`PasswordStrengthChecker\`

- **common_passwords**: List of common passwords to check against. (Default: 10000 most common passwords)
- **min_length**: Minimum length required for a password to be considered strong. (Default: 10 chars)
- **dictionary_words**: List of dictionary words to check against for potential vulnerability. (Default: English dictionary)

## Testing

To run the tests, you can use:

\`\`\`bash
python -m unittest discover -s tests
\`\`\`

Make sure all tests pass before using the package in a production environment.

## Contributing

We welcome contributions to enhance the functionality and usability of **SafePassGen**. To contribute:

1. Fork the repository.
2. Create a new branch (\`git checkout -b feature-branch\`).
3. Make your changes.
4. Commit your changes (\`git commit -m 'Add new feature'\`).
5. Push to the branch (\`git push origin feature-branch\`).
6. Open a Pull Request.

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

