# Git Procedures
In order to assure maximum work flow and proper backups of data, please adhear to these git procedures

## Branches:
Branches are used to split code of the main branch.
Consistently every project should have at least 2 branches
-Main (current build used by platform and loader)
-Beta (Next working build for beta users

## Commits:
Developers on the project should be commiting to branches at least once every 3 hours of working
to have historical records of working or almost working versions.

 ***Commits that are not working and are not from either of the two main working branches above should be commited 
to a new branch*** that is titled after the feature or main feature they are working on, and on a working iteraion of that branch should be join with beta
then after testing staged onto the main branch.

## Tags:
Tags will be used to mark known working builds of different features and build versions
For example if you merge a branch with master or beta, it should then be tagged with the feature name that was added or modifed in that branch with todays date

## Issues:
All bugs or additional features should be added to the issues tab and reported with as much detail as possible as well as the name of the user who found the bug
This will allow easer tracking and fixing of various issues with the products

# Code Style Guide 

This document outlines the C++ code style that our project uses. These standards help us maintain readability and consistency in our codebase.

## Table of Contents

- [Indentation and Bracing](#indentation-and-bracing)
- [Function Naming](#function-naming)
- [Variable Naming](#variable-naming)
- [Class Naming](#class-naming)
- [Single Include Header](#single-include-header)

### Indentation and Bracing

We use the Allman style for indentation and bracing, where each brace (`{` or `}`) occupies a separate line:

```cpp
void Some_Function()
{
    // Function body
}
```

### Function Naming

Function names use PascalCase with underscores (`_`) separating words. Here is an example:

```cpp
void My_Function_Name()
{
    // Function body
}
```

### Variable Naming

Variable names are prefixed with a lower-case abbreviation of the type, followed by the variable name in PascalCase. 

Variable names should clearly express the intention or the data that they hold. If a variable is used to hold a count of apples, a good name might be `iAppleCount`, not `iCount` or `iApples`.

- Integer: `i`
- Float: `fl`
- Character: `c`
- String: `str`
- Pointer: `p`

We use an underscore (`_`) between words in the function name, but not in the variable name. Here are some examples:

```cpp
int i_AppleCount = 10;
float fl_AppleWeight = 1.5;
char c_FirstLetter = 'a';
std::string str_AppleType = "Granny Smith";
```

### Class Naming

Class names use PascalCase with underscores (`_`) separating words:

```cpp
class My_Class_Name
{
    // Class body
}
```

### Single Include Header

For better structure and to avoid redundancy, we use a single include header file that contains all other header files. This single file is included in every file rather than having multiple includes in different files. This approach, known as a Precompiled Header or a "Master" Header, can significantly reduce compilation times and keeps the project structure clean.

Here's how you might set up such a header:

```cpp
// precompiled.h
#pragma once

#include <iostream>
#include <string>
// ... other includes
```

And this is how you include it in every .cpp file:

```cpp
// my_file.cpp
#include "precompiled.h"

void My_Function_Name()
{
    // Function body
}
```

By following this guide, we can ensure that our codebase remains consistent, which in turn aids readability and maintainability. Thank you for adhering to these guidelines.
Here is a large code snippet:
```cpp
// game.h
#pragma once

#include <iostream>
#include <ctime>
#include <cstdlib>

class Number_Guess_Game
{
public:
    void Start_Game();
private:
    int Generate_Random_Number();
    void Process_Guess(int i_Guess);
    bool Check_Guess(int i_Guess, int i_CorrectNumber);
};

// game.cpp
#include "game.h"

void Number_Guess_Game::Start_Game()
{
    srand(time(0)); // Initialize random seed
    int i_CorrectNumber = Generate_Random_Number();

    std::cout << "Welcome to the Number Guessing Game!\n";
    std::cout << "Guess a number between 1 and 100:\n";

    int i_Guess;
    do
    {
        std::cin >> i_Guess;
        Process_Guess(i_Guess);
    } while (!Check_Guess(i_Guess, i_CorrectNumber));

    std::cout << "Congratulations! You've correctly guessed the number: " << i_CorrectNumber << "\n";
}

int Number_Guess_Game::Generate_Random_Number()
{
    return rand() % 100 + 1; // Generate random number between 1 and 100
}

void Number_Guess_Game::Process_Guess(int i_Guess)
{
    std::cout << "You've guessed: " << i_Guess << "\n";
}

bool Number_Guess_Game::Check_Guess(int i_Guess, int i_CorrectNumber)
{
    if(i_Guess < i_CorrectNumber)
    {
        std::cout << "Too low! Try again.\n";
        return false;
    }
    else if(i_Guess > i_CorrectNumber)
    {
        std::cout << "Too high! Try again.\n";
        return false;
    }
    else
    {
        return true;
    }
}

// main.cpp
#include "game.h"

int main()
{
    Number_Guess_Game Game_Instance;
    Game_Instance.Start_Game();
    return 0;
}

```
