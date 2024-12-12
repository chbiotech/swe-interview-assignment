# Puzzle Pieces
Thank you for your interest in joining the CH Biotech team!

This assignment is intended to evaluate your ability to design and implement an algorithm to solve a given task.

## Requirements
- Your solution should be written to run on Python 3; if you prefer to use another language, please discuss with us first.
- Your project should be based on an algorithm that you designed and implemented. 
- You may use standard libraries, but it should be clear that you wrote the algorithm itself and you should be able to explain why you chose the libraries that you chose.
- You should be able to clearly explain how every step of your algorithm works and why you made each design choice; your answer shouldn't simply be "I passed the input to a library/API".
- You may not use AI tools such as ChatGPT or Copilot for this assignment.

## Deliverables
- Please share a link to a Github repository containing everything needed to build/run your solution (including a `requirements.txt`)
- Your Github repository should also contain a folder with your program's output for both test cases.
- Your repository should contain a README.md file containing instructions on how to use your project, as well as a brief introduction of the algorithm used.
- Please set your repository as a private repository shared with Github user @chbiotech.
- During your interview, you will be asked to demonstrate and explain your solution as well as a discussion of the design of your algorithm. Please bring a laptop and anything else you think you might need.

## Task Statement
The `.chbt` file format includes string fragments in the following format:
```>string_1
CDEFCDEFCDEFCDEFCDEFCDEFCDEFCDEFCDEF
BCDEBCDEBCDEBCDEBCDEBCDEBCDEBCDEBCDE
SOMESTRINGFRAGMENTSOMESTRINGFRAGMENT
SOMESTRINGFRAGMENTSOMESTRINGFRAGMENT
SAMESTRINGFRAGMENTSOMESTRINGFRAGMENT
SBMESTRINGFRAGMENTSOMESTRINGFRAGMENT
EFGHEFGHEFGHEFGHEFGHEFGHEFGHEFGHEFGH
>string_2
SAMESTRINGFRAGMENTSOMESTRINGFRAGMENT
SBMESTRINGFRAGMENTSOMESTRINGFRAGMENT
EFGHEFGHEFGHEFGHEFGHEFGHEFGHEFGHEFGH
SOMESTRINGFRAGMENTSOMESTRINGFRAGMENT
SOMESTRINGFRAGMENTSOMESTRINGFRAGMENT
SZMESTRINGFRAGMENTSOMESTRINGFRAGMENT
GHIJGHIJGHIJGHIJGHIJGHIJGHIJGHIJGHIJ
>string_3
ABCDABCDABCDABCDABCDABCDABCDABCDABCD
SOMESTRINGFRAGMENTSOMESTRINGFRAGMENT
SOMESTRINGFRAGMENTSOMESTRINGFRAGMENT
CDEFCDEFCDEFCDEFCDEFCDEFCDEFCDEFCDEF
BCDEBCDEBCDEBCDEBCDEBCDEBCDEBCDEBCDE
>owtu
GHJKGHJKGHJKGHJKGHJKGHJKGHJKGHJKGHJK
SOMESTRINGFRAGMENTSOMESTRINGFRAGMENT
YUIOYUIOYUIOYUIOYUIOYUIOYUIOYUIOYUIO
>456
SOMESTRINGFRAGMENTSOMESTRINGFRAGMENT
SRMESTRINGFRAGMENTSOMESTRINGFRAGMENT
QWERQWERQWERQWERQWERQWERQWERQWERQWER
SOMESTRINGFRAGMENTSOMESTRINGFRAGMENT
SOMESTRINGFRAGMENTSOMESTRINGFRAGMENT
SOMESTRINGFRAGMENTSOMESTRINGFRAGMENT
POIUPOIUPOIUPOIUPOIUPOIUPOIUPOIUPOIU
>789
SZMESTRINGFRAGMENTSOMESTRINGFRAGMENT
GHIJGHIJGHIJGHIJGHIJGHIJGHIJGHIJGHIJ
SOMESTRINGFRAGMENTSOMESTRINGFRAGMENT
SOMESTRINGFRAGMENTSOMESTRINGFRAGMENT
SRMESTRINGFRAGMENTSOMESTRINGFRAGMENT
QWERQWERQWERQWERQWERQWERQWERQWERQWER
...
```

Each string fragment starts with a header that begins with a `>` character followed by an ID such as `string_1` which identifies that fragment. Following that is the string fragment itself, which continues until the next string fragment header is found.

In each string fragment, only letters are considered; line breaks, spaces, and other characters are ignored. For example, the file in the above example could be parsed as:

| String ID | String fragment |
| --------- | --------------- |
| `string_1` | `**CDEFCDEFCDEFCDEFCDEFCDEFCDEFCDEFCDEFBCDEBCDEBCDEBCDEBCDEBCDEBCDEBCDEBCDE**SOMESTRINGFRAGMENTSOMESTRINGFRAGMENTSOMESTRINGFRAGMENTSOMESTRINGFRAGMENTSAMESTRINGFRAGMENTSOMESTRINGFRAGMENTSBMESTRINGFRAGMENTSOMESTRINGFRAGMENTEFGHEFGHEFGHEFGHEFGHEFGHEFGHEFGHEFGH` |
| `string_2` | `SAMESTRINGFRAGMENTSOMESTRINGFRAGMENTSBMESTRINGFRAGMENTSOMESTRINGFRAGMENTEFGHEFGHEFGHEFGHEFGHEFGHEFGHEFGHEFGHSOMESTRINGFRAGMENTSOMESTRINGFRAGMENTSOMESTRINGFRAGMENTSOMESTRINGFRAGMENTSZMESTRINGFRAGMENTSOMESTRINGFRAGMENTGHIJGHIJGHIJGHIJGHIJGHIJGHIJGHIJGHIJ` |
| `string_3` | `ABCDABCDABCDABCDABCDABCDABCDABCDABCDSOMESTRINGFRAGMENTSOMESTRINGFRAGMENTSOMESTRINGFRAGMENTSOMESTRINGFRAGMENT**CDEFCDEFCDEFCDEFCDEFCDEFCDEFCDEFCDEFBCDEBCDEBCDEBCDEBCDEBCDEBCDEBCDEBCDE**` |
| `owtu` | `GHJKGHJKGHJKGHJKGHJKGHJKGHJKGHJKGHJKSOMESTRINGFRAGMENTSOMESTRINGFRAGMENTYUIOYUIOYUIOYUIOYUIOYUIOYUIOYUIOYUIO` |
| `456` | `SOMESTRINGFRAGMENTSOMESTRINGFRAGMENTSRMESTRINGFRAGMENTSOMESTRINGFRAGMENTQWERQWERQWERQWERQWERQWERQWERQWERQWERSOMESTRINGFRAGMENTSOMESTRINGFRAGMENTSOMESTRINGFRAGMENTSOMESTRINGFRAGMENTSOMESTRINGFRAGMENTSOMESTRINGFRAGMENTPOIUPOIUPOIUPOIUPOIUPOIUPOIUPOIUPOIU` |
| `789` | `SZMESTRINGFRAGMENTSOMESTRINGFRAGMENTGHIJGHIJGHIJGHIJGHIJGHIJGHIJGHIJGHIJSOMESTRINGFRAGMENTSOMESTRINGFRAGMENTSOMESTRINGFRAGMENTSOMESTRINGFRAGMENTSRMESTRINGFRAGMENTSOMESTRINGFRAGMENTQWERQWERQWERQWERQWERQWERQWERQWERQWER` |

Most of the string fragments in this file are a substring of a longer string. If they are a substring, they will have some overlap with another piece (where the length of the overlap is random). This overlap, if it exists, is normally unique.

For example, `string_1` begins with `CDEFCDEFCDEFCDEFCDEFCDEFCDEFCDEFCDEFBCDEBCDEBCDEBCDEBCDEBCDEBCDEBCDEBCDE`, and `string_3` ends with the same (see bolded section in the above table).

Your task is to write a program which, given an input `.chbt` file, can give:
- The complete string assembled from the string fragments that have overlaps
- The correct sequence of string fragment IDs
- A list of string fragment IDs that were not apart of the complete string (an overlap couldn't be found).

Given the above example, the complete assembled string (with line breaks added for readability) would be:
```
ABCDABCDABCDABCDABCDABCDABCDABCDABCD
SOMESTRINGFRAGMENTSOMESTRINGFRAGMENT
SOMESTRINGFRAGMENTSOMESTRINGFRAGMENT
CDEFCDEFCDEFCDEFCDEFCDEFCDEFCDEFCDEF
BCDEBCDEBCDEBCDEBCDEBCDEBCDEBCDEBCDE
SOMESTRINGFRAGMENTSOMESTRINGFRAGMENT
SOMESTRINGFRAGMENTSOMESTRINGFRAGMENT
SAMESTRINGFRAGMENTSOMESTRINGFRAGMENT
SBMESTRINGFRAGMENTSOMESTRINGFRAGMENT
EFGHEFGHEFGHEFGHEFGHEFGHEFGHEFGHEFGH
SOMESTRINGFRAGMENTSOMESTRINGFRAGMENT
SOMESTRINGFRAGMENTSOMESTRINGFRAGMENT
SZMESTRINGFRAGMENTSOMESTRINGFRAGMENT
GHIJGHIJGHIJGHIJGHIJGHIJGHIJGHIJGHIJ
SOMESTRINGFRAGMENTSOMESTRINGFRAGMENT
SOMESTRINGFRAGMENTSOMESTRINGFRAGMENT
SRMESTRINGFRAGMENTSOMESTRINGFRAGMENT
QWERQWERQWERQWERQWERQWERQWERQWERQWER
SOMESTRINGFRAGMENTSOMESTRINGFRAGMENT
SRMESTRINGFRAGMENTSOMESTRINGFRAGMENT
QWERQWERQWERQWERQWERQWERQWERQWERQWER
SOMESTRINGFRAGMENTSOMESTRINGFRAGMENT
SOMESTRINGFRAGMENTSOMESTRINGFRAGMENT
SOMESTRINGFRAGMENTSOMESTRINGFRAGMENT
POIUPOIUPOIUPOIUPOIUPOIUPOIUPOIUPOIU
```

The correct sequence of string fragment IDs would be:
```
string_3, string_1, string_2, 789, 456
```

The string fragment ID `owtu` is not apart of the assembled string.

The above examples are provided in the `example` folder.

We have also provided a `unknown.chbt` file containing a much larger example for which the solution is not shared. Along with your code, you should submit the above outputs for your program on `unknown.chbt`.

## Evaluation criteria
Your solution will be evaluated according to these criteria:
- Correctness: Does your code give the correct results?
- Error handling: Does your code handle edge cases or errors/exceptions gracefully?
- Optimization: We often deal with large datasets. How well optimized is your solution? Can you explain why you made various design choices in the interests of optimization?
- Code cleanliness: How clean and easy to read is the code? Is the code easily maintainable? 
- Best practices: How well does your code follow best practices for the language that you chose? 
- Documentation: Do you appropriately and sufficiently document your code (eg, with comments)?
- Demonstrated mastery of algorithms and data structures: Does your solution demonstrate a mastery of algorithm design and appropriate use of data structures?
- Defense: How well can you explain your project and the design choices you've made? Are you able to defend your choices if they are challenged? How well can you explain it to an audience without a background in software engineering?

## Due date
Your solution should be submitted at least 24 hours before your scheduled interview.
