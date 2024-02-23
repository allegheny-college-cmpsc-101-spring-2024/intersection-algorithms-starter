
# Intersection Algorithms

[![build](../../actions/workflows/build.yml/badge.svg)](../../actions/)
![Platforms: Linux, MacOS, Windows](https://img.shields.io/badge/Platform-Linux%20%7C%20MacOS%20%7C%20Windows-blue.svg)
[![Language: Python](https://img.shields.io/badge/Language-Python-blue.svg)](https://www.python.org/)
[![Code Style: Black](https://img.shields.io/badge/Code%20Style-Black-blue.svg)](https://github.com/psf/black)
[![Commits: Conventional](https://img.shields.io/badge/Commits-Conventional-blue.svg)](https://www.conventionalcommits.org/en/v1.0.0/)
[![Discord](https://img.shields.io/discord/872320492936257537?logo=discord)](https://discord.gg/kjah8MFYbR)

## Introduction

- Due date: Check Discord or the
  [Course Materials Schedule](https://github.com/allegheny-college-cmpsc-101-spring-2024/course-materials/blob/main/Schedule.md)
- This assignment is graded as
  described in the syllabus section for
  [Assignment Evaluation](https://github.com/allegheny-college-cmpsc-101-spring-2024/course-materials?tab=readme-ov-file#assignment-evaluation)
- Submit this assignment on GitHub following the expectations in the syllabus on
  [Assignment Submission](https://github.com/allegheny-college-cmpsc-101-spring-2024/course-materials#assignment-submission).
- To begin, read this `README` based on the Proactive Programmers' project
  [instructions](https://proactiveprogrammers.com/data-abstraction/engineering-efforts/intersection-algorithms/)
- This project has been adapted from Proactive Programmers' material, thus discrepancies are possible.
- Post to the #data-structures Discord channel for questions and clarifications.
- For reference, check the
  [starter repo](https://github.com/allegheny-college-cmpsc-101-spring-2024/intersection-algorithms-starter)

## Learning Objectives

1. Run an empirical experiment
2. Understand trade-offs between data types
3. Use ruff instead of black, isort, flake8, pylint, pydocstyle
4. Write clearly about the programming concepts in this assignment.

## Seeking Assistance

Please review the course expectations on the syllabus about
[Seeking Assistance](https://github.com/allegheny-college-cmpsc-101-spring-2024/course-materials#seeking-assistance).
Students are reminded to uphold the Honor Code. Cloning the assignment repository is a
commitment to the latter.

For this assignment, you may use class materials, textbooks, notes, and the
internet. Ensure that your writing is original and based on your own understanding
of the concepts.

To claim that work is your own, it is essential to craft the logic and the
writing together without copying or using the logical structure of another
source. The honor code holds everyone to this standard.

If outside of lab you have questions, the #data-structures Discord channel,
TL office hours, instructor office hours, and GitHub Issues can be utilized.

## Project Overview

After cloning this repository to your computer, please take the following
steps:

- Change into the program directory by typing `cd intersection`.
- Install the dependencies for the project by typing `poetry install`.
- Run the program in with both algorithms by typing:
  - `poetry run intersection --numelems 1000 --maximum 25 --profile --approach TupleSingle`
  - `poetry run intersection --numelems 1000 --maximum 25 --profile --approach TupleDouble`
  - `poetry run intersection --numelems 1000 --maximum 25 --profile --approach ListSingle`
  - `poetry run intersection --numelems 1000 --maximum 25 --profile --approach ListDouble`
  - Please note that these are not the only configurations you should try for your experiment
  - Please note that the program will not work unless you add the required source code
  - Please refer to the `writing/reflection.md` file for all ways to run the program
  - Please refer to the course web site for more details about this project's configurations
- Confirm that the program is producing the expected output described
  below and on the Proactive Programmers web site.
- Run the automated grading checks by typing
  `gatorgrade --config config/gatorgrade.yml`.
- You may also review the output from running GatorGrader in GitHub Actions.
- Don't forget to provide all of the required responses to the technical writing
  prompts in the `writing/reflection.md` file.
- Please make sure that you completely delete the `TODO` markers and their
  labels from all of the provided source code.
- Please make sure that you also completely delete the `TODO` markers and their
  labels from every line of the `writing/reflection.md` file.

## Project Details

This assignment invites you to implement a program that features multiple
algorithms for computing the intersection between a data container.
Specifically, you will implement and experimentally evaluate the following
intersection algorithms: (i) a `list`-based approach with a single `for` loop,
(ii) a `list`-based approach with a double `for` loop, (iii) a `tuple`-based
approach with a single `for` loop, and (iv) a `tuple`-based approach with a
double `for` loop. In addition to adding source code to the provided Python
files, you will conduct an experiment to determine which algorithm is the
fastest and estimate by how much it is faster.

## Expected Output

This project invites you to implement a data container intersection problem
called `intersection`. After you finish a correct implementation of all the
program's features, running it with the command `poetry run intersection
--number 10000 --maximum 25 --profile --approach ListDouble` will produce output
like the following. This output shows that it took approximately `2.210` seconds
to compute the intersection of two `list`s that each contain `10,000` randomly
generated values with the maximum value in each `list` being `25`. Importantly,
this invocation of the `intersection` program configures it to run the
`ListDouble` algorithm that uses a doubly-nested `for` loop to compute the
intersection of the `list`s. Did you notice that this program produces profiling
data about how long it took to run the `intersection` program with the
`ListDouble` algorithm? This is because of the fact that it uses the
[Pyinstrument](https://github.com/joerick/pyinstrument) package to collect
execution traces and efficiency information about the program.

```cmd
🔬 Here's profiling data from computing an intersection with random data
containers of 10000!

  _     ._   __/__   _ _  _  _ _/_   Recorded: 14:01:19  Samples:  2207
 /_//_/// /_\ / //_// / //_'/ //     Duration: 2.211     CPU time: 2.203
/   _/                      v4.0.3

Program: intersection --number 10000 --maximum 25 --profile --approach ListDouble

2.210 intersection  intersection/main.py:99
└─ 2.210 compute_intersection_list_double  intersection/main.py:53
   ├─ 2.051 [self]
   └─ 0.159 list.append  <built-in>:0
         [2 frames hidden]  <built-in>
```

It is worth noting that you do not have to run `intersection` in the `profile`
mode that uses Pyinstrument. For instance, running the program with `poetry run
intersection --number 10 --maximum 25 --display --approach ListDouble` would run
the program with the `ListDouble` algorithm and perform the same computation
without collecting the performance data. When run with this command,
`intersection` would produce output like the following. Note that when the
program is run with the `--display` flag and without the `--profile` flag it
shows the two input data containers and their computed intersection &mdash;
without reporting any details about the efficiency of the algorithm. This mode
is ideal when you want to confirm that your implementation of `intersection` is
perform the correct computation and less useful when you are running experiments
to study the program's performance.

```cmd
✨ Here are the details about the intersection computation!

Performed intersection with:
---> the first data container: [22, 10, 21, 11, 2, 7, 4, 16, 22, 23]
---> the second data container: [16, 17, 23, 24, 12, 4, 21, 1, 18, 19]
Computed the intersection as the data container: [21, 4, 16, 23]
```

Don't forget that you can display `intersection`'s help menu and learn more
about its features by typing `poetry run intersection --help` to display the
following:

```cmd
Usage: intersection [OPTIONS]

  Compute the intersection of data containers.

Options:
  --number INTEGER                [default: 5]
  --maximum INTEGER               [default: 25]
  --profile / --no-profile        [default: False]
  --display / --no-display        [default: False]
  --approach [ListSingle|TupleSingle|ListDouble|TupleDouble]
                                  [default: TupleSingle]
  --install-completion            Install completion for the current
                                  shell.

  --show-completion               Show completion for the current shell,
                                  to copy it or customize the
                                  installation.

  --help                          Show this message and exit.
```

Continue reading to understand what functionality to add to the source code.

>Don't forget that if you want to run the `intersection` program you must use
>your terminal window to first go into the GitHub repository containing this
>project and then go into the `intersection` directory that contains the
>project's source code. Finally, remember that before running the program you
>must run `poetry install` to add its dependencies, such as Pyinstrument,
>Pytest, and Rich.

## Adding Functionality

If you study the file `intersection/intersection/main.py` you will see that it
has many `TODO` markers that designate the parts of the program that you need to
implement before `intersection` will produce correct output. To ensure that the
program works correctly, you must implement all of these functions before you
start to run the experiments.

- `def generate_random_container(size: int, maximum: int, make_tuple: bool = False) -> Union[List[int], Tuple[int, ...]]`
- `def compute_intersection_list_double(input_one: List[Any], input_two: List[Any]) -> List[Any]`
- `def compute_intersection_list_single(input_one: List[Any], input_two: List[Any]) -> List[Any]`

The function called `generate_random_container` should automatically create
either a `tuple` or a `list` of the specified `size` and only containing values
that are less than or equal to the `maximum`. The function called
`compute_intersection_list_single` should follow the implementation strategy of
its counterpart function called `compute_intersection_tuple_single` while still
using the functions appropriate for the `list` structured type. Moreover, the
`compute_intersection_list_double` should follow the implementation of
`compute_intersection_tuple_double` except for the fact that it should populate
an `list` through the use of a doubly-nested `for` loop. As a reference, here is
the source code for the `compute_intersection_tuple_single` function:

```python linenums="1"
def compute_intersection_tuple_single(
    input_one: Tuple[Any, ...], input_two: Tuple[Any, ...]
) -> Tuple[Any, ...]:
    """Compute the intersection of two provided tuples."""
    result: Tuple[Any, ...] = ()
    for element in input_one:
        if element in input_two:
            result += (element,)
    return result
```

According to the type signature of this function on lines `1` and `2`, the
`compute_intersection_tuple_single` function accepts as input two `tuples` that
can contain `Any` type of data and be of an arbitrary size. Lines `6` through
`8` of this function show that it uses the combination of a `for` loop and an
`if` statement to compute the intersection of the `tuple`s called `input_one`
and `input_two`. After finding those elements that these `tuple`s contain in
common, `compute_intersection_tuple_single` returns the `result` on line `9`.
Since this function processes `tuple`s it is possible that the intersection of
the input parameters will be a `result` that contains a value more than once. It
is also worth noting that, since the `tuple` structured type is immutable, this
function uses the `+=` operator on line `8` to create a new `tuple` each time
that it adds data to the `result` variable. You will empirically study the
efficiency of this approach!

After finishing your implementation of `intersection` you should conduct an
experiment to evaluate the efficiency of the different algorithms that it
provides. You should refer to the `writing/reflection.md` file for more details
about the experiment that you should conduct and how you must configure the
`intersection` program to collect data. Ultimately, you need to answer the
following three research questions:

- Is the intersection of two data containers faster with a `list` or a `tuple`?
- Is the intersection of two data containers faster with a double or single `for` loop?
- Overall, what is the fastest approach for computing the intersection of two
  data containers?

## Running Checks

If you study the source code in the `pyproject.toml` file you will see that it
includes the following section that specifies different executable tasks like
`ruff`. If you are in the `intersection` directory that contains the
`pyproject.toml` file and the `poetry.lock` file, the tasks in this section
make it easy to run commands like `poetry run task ruff` to automatically run
the ruff linter designed to check the Python source code in your program and
its test suite to confirm that your source code adheres to the industry-standard.
You can also use the command `poetry run task fix` to automatically reformat the
source code. `poetry run task ruffdetails` will print out detailed linting errors
that point to exactly what ruff views as a linting error. Make sure to examine
the `pyproject.toml` file for other convenient tasks that you can use to both
check and improve your project!

Along with running tasks like `poetry run task ruff`, you can run the command
`gatorgrade --config config/gatorgrade.yml` to check your work. If your work
meets the baseline requirements and adheres to the best practices that proactive
programmers adopt you will see that all the checks pass when you run
`gatorgrade`. You can study the `config/gatorgrade.yml` file in your repository
to learn how the :material-github:
[GatorGrade](https://github.com/GatorEducator/gatorgrade) program runs
:material-github: [GatorGrader](https://github.com/GatorEducator/gatorgrader) to
automatically check your program and technical writing. If your program has all
of the anticipated functionality, you can run the command `poetry run task test`
and see that the test suite produces output like the following. Can you add
comments to the test suite to explain how the test cases work?

```text
collected 4 items

tests/test_intersection.py .......
```

This project comes with other tasks that you can run once you have used Poetry
to install all of the dependencies. For instance, You
can also run commands like `poetry run task mypy` to check the program's use of
data types and `poetry run task markdownlint` to ensure that your source code
and writing adhere to other established conventions.

>Don't forget that when you commit source code or technical writing to your
>GitHub repository for this project, it will trigger the run of a GitHub
>Actions workflow. If you are a student at Allegheny College, then running
>this workflow consumes build minutes for the course's organization! As such,
>you should only commit to your repository once you have made substantive
>changes to your project and you are ready to confirm its correctness. Before
>you commit to your GitHub repository, you can still run checks on your own
>computer by using Poetry and GatorGrader.

## Project Reflection

Once you have finished both of the previous technical tasks, you can use a text
editor to answer all of the questions in the `writing/reflection.md` file. For
instance, you should provide the output of the Python program in a fenced code
block, explain the meaning of the Python source code segments that you
implemented, and answer all of the other questions about your experiences in
completing this project. A specific goal of the reflection for this project is
to evaluate the efficiency of the different algorithms and data containers
implemented as part of the `intersection` program. When you are writing your
performance evaluation make sure that you both explain what performance trends
are evident and why you think the algorithms yield these trends. Finally, you
should reflect on how the experimental evaluation of a program's performance is
more nuanced than you might have initially expected before starting to work on
this project.

## Project Assessment

Since this project is an engineering effort, it is aligned with the
**evaluating** and **creating** levels of [Bloom's
taxonomy](/proactive-learning/blooms-taxonomy/). You can learn more about how a
proactive programming expert will assess your work by examining the [assessment
strategy](/proactive-learning/assessment-strategy/). From the start to the end
of this project you may make an unlimited number of reattempts at submitting
source code and technical writing that meet all aspects of the project's
specification.
