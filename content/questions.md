+++
title = "Questions, answers, and feedback"
+++

## Questions, answers and feedback

### Live notes taken during the workshop on March 17

 - I don't understand what is the difference between gitlab and github? I have also a gitlab account and could go into a Python gitlab room.
    - They are two online platforms for collaborating on code. They work quite similarly, but are owned by different companies.
    - Yes, I know :-) But I use the same git commands to push.
        + Both use git for version managment (hence the same commands), but the features are different between the two platforms (testing, actions, etc)
        - The exercise will show how to run tests automatically on the two platforms when you push changes. (Behind the scenes, git knows which repository you originally cloned, whether gitlab, github or something else. So after you clone, very little differs.)


- for the code refinery workshop it was possible to get graduate school credit (at Tu Delft). Is it possible to get a certificate for this workshop as well to get GS credit?
     - certificates can be requested via email to support@coderefinery.org
         - if credits can be given from university depends on your university
	     - great thanks!

- How does the assert function work?
    + `assert(cond, message)` checks whether the given condition evaluates to true. If it is false, the message is printed (sometimes along with the condition) and the program terminates. In case of true, the program continues.

- Is it best to include tests in the same script file or to organize specific test files ?
  - It will depend on the facilities your language offers for testing. In Python, for example, you can do both and `pytest` will be able to find and run them all. In C++, they need to be in other files. Personally, I prefer tests to be in a separate folder, regardless of the language I am using. If you're starting to work on a new project, it's very instructive to look at the tests to understand what the code does and with which functions in the codebase. If tests are in separate files in separate folders, then this exploration is much easier.

- Will we be trying mock in Python?
  - There are no explicit exercises on mocking, but we can discuss examples later on, I think.


- What does CD stand for, please? I saw CI/CD, I think.
  - Continuous integration (CI) and continuous delivery (CD). The former is running tests automatically on a regular schedule: usually, but not necessarily on every commit pushed to the remote repository. The latter is the automated deployment of the "artifacts" of your code on a regular schedule (could be on every push). The deployment might be uploading a Python package to the Python package index (PyPI) or running a new version of a web application on a server that your users interact with.

- (moved from above) If i have functions that do not perform very specific calculation, but they do operate and modify a class of inputs (i.e. high pass filter on an image), how do i test them?
    - In the test code, I would save a reference input and reference output files, run the code on the former and then check that the new output matches the reference one.
        - Consider also refactoring the original code, so that you do not modify the input but rather make a copy and return it as output. This will incidentally help the modularity and reusability of the code. However, if the resources (memory, CPU) to copy are very expensive, you might not follow this strategy.
	    - Another option is to create a very small input set where you already know the result (or can compute it yourself). For example sampling or filtering a small 2D grid. Or an image where the high pass filter returns a trivial result, like all black.

    - Can I customize the name of the test in pytest?
            - yestest?
	            - yes

- What does the pytest return exactly?
  - Each function named ``test_`` should return either ``True`` or ``False``. Running pytest aggregates the results and prints them to screen nicely.


- I had the test to fail. Function returns a-b. The test should assert add(2,3)==5. I get

  ```
    assert add(2, 3) == 5
      E       assert -1 == 5
        E         +-1
	  E         -5
  ```

   - There is a + in front of 1, not --1 as shown in the example. Same for 5.  We wondered if there is some version control in the pytest.
       - The ``+`` and ``-`` work as in a patch you obtain from version control: "I expected 5 (``-``) but found -1 (``+``)" I am not sure why it's different  in the published material.
         - I still don't understand. The `+` indicates what, please, for example?
            - The test was expecting the value ``5`` to be present, but found the value ``-1``. This means that ``-1`` was *added* to the output, hence the (``+``) by its side, while ``5`` was *removed*, hence the (``-``) in front.

- What is a good way to set the acceptable tolarance for floating point comparisons across an entire test suite? Should/could this be an external flag or part of the tests? And should one add checks to verify the precision of the interpreter running the tests?
  - That really depends on what you are testing for. By default, floating point numbers in Python are double precision, so the predefined thresholds in pytest and numpy are geared towards that.
    - I suggest against this, unless the kind of logic that computes float-point numbers is always the same. You don't want to force yourself to have very sloppy testing of numbers that are very reproducible, just because some of the other numbers are computed in a way that is less reproducible.
      - Ideally, you understand the algorithm that computes the floating-point number and can reason about what range makes sense. For example, accumulating a sum over a vector has an absolute bound on the range of results, depending on the order of accumulation, but that bound depends on the values in the vector... (But this is a big topic in its own right!)

- Why do other calculations like 0.1 + 0.4 work correctly?
    - In that case, the result (0.5) can be represented exactly as a floating-point number, and it’s possible for rounding errors in the input numbers to cancel each other out - But that can’t necessarily be relied upon (e.g. when those two numbers were stored in differently sized floating point representations first, the rounding errors might not offset each other).
        - In other cases like 0.1 + 0.3, the result actually isn’t really 0.4, but close enough that 0.4 is the shortest number that is closer to the result than to any other floating-point number. Many languages then display that number instead of converting the actual result back to the closest decimal fraction.
	    - https://floating-point-gui.de/basic/


- (from zoom chat)how do you test when you using Spyder?
    - ``!pytest -v example.py``

    - Is it the same like `!ls` in a notebook, i.e. executing a terminal command?
            - yes, same idea, to run non-python commands

- I am not able to rename myself with the group name in Zoom.
    - can you not hover over your name in the Participants list, click "More", and then "Rename"?
            - Answer: yes, thank you.
	            - Great!

- How to run tests in Jupyter notebook? Do we need to run through command prompt ?
    - you could use ``!pytest test.py`` if you have your tests in a separate script (test.py) from within a codecell in the jupyter notebook
        - there seem to also be plugins for jupyter notebooks, such as https://pypi.org/project/pytest-notebook/ (no experience with those)


**Exercise until 10:45**

- How big allocation does a repo get in terms of testing? Could too long test times be limited by Github?
  - often it's ~ 1 hour per task/workflow and often you can run several of them at the same time. if the test set takes hours, then it won't fit there but then you can connect your own test runner (can be an idle computer or some cloud computing resource) to e.g. GitLab CI and then they can be in principle arbitrary long.


- Could you comment on what Mark means with targeting different use cases by github and gitlab, please?  Thank you.
    - They're useful for the same use cases. They just are built differently by different people and the feature sets suit the people who paid for them to be built. For our purposes, they're the same.

- Not sure about pt 4: "Also browse the “Actions” tab and look at the steps there and their output."
    - There you can see what actions have run, e.g. https://github.com/mabraham/testing-workshop-mark/actions
            - Ok, I think my tests are not running, that's why I cannot see anything (see the point below)
	            - Make sure you followed the steps to enable automated testing.


- Is it possible to run the GitHub actions inside a singularity container
  - You should check the GitHub marketplace to see whether there's a pre-packaged action. It is possible to run inside a Docker container, so it should be possible to run within Singularity.


- this exercise is not working for me, it seems like I'm missing a "runner". I'm using my TU Delft gitlab account, perhaps there are no "runners" configured.
  - right. we were somehow assuming that gitlab would be gitlab.com. we need to clarify this for later workshops that other gitlab servers may not be connected to runners yet.
    - to investigate, in the left-hand menu, scrolling down to settings, then find "CI/CD" submenu under it. Then you will see if the shared runners are available.

- To allow actions in your fork of a repository on GitHub you need to activate them by clicking Actions and enabling them. What are the risks of enabling actions a forked repo under your GitHub account?
  - I don't see any risks. This can be useful if you want to test your changes automatically before sending a pull/merge request to "upstream". Note that you don't need to activate actions on the fork to get pull requests upstream automatically tested.


- Can we have more time?
    - some of us can stay a bit after the workshop, if you would like to continue this exercise (breakoutrooms will stay open)

- (moved from zoom chat) What should one consider regarding resource limitation on GitHub actions?
  - https://docs.github.com/en/actions/reference/usage-limits-billing-and-administration#usage-limits
      You have a hard 10GB limit on disk space.


- Why does a test can take hours, please?
  - a test could be an end-to-end test and test the whole code (we will see that later) and depending on the program it can take arbitrarily long. but it is good if tests only take seconds or minutes since it can make development easier

- GitLab only creates a merge request across different branches. Gives an error when the merge is from master to master. Is that right?
    - Yes, merges and pull requests only make sense between different branches (ie including a branch of the same name in a different repo)

- Pt 5 does not break the tests in my repo. My hunch is that he tests are not running because of some silly syntax mistake.
  - You should have used the "Python package" action. The one you are using is for publishing the pacakge to PyPI and will only run when you create a new release.
        - thank you, what now? can we talk?
	   - solved
	     - Thank you. I had a yml triggering every release, which is not good. Therefore I created a new workflow with of type "Python application", then the .yml file was created in the wrong place, so I had to move it to .github/workflows


- in github/workflows/python-app.yml i got n error "every step must define a `uses` or `run` key" what that means?
    - probably you made a typo, like wrong numbers of spaces in the indenting. Copy the example carefully and it will work.
       - I also had it, it was due to a dash before the `run` command

- in the background, does the testing takes place in a container? (I noticed `ubuntu-latest` in the yml file.) Would this entail all the (environmental) cost of spinning up a container?
  - yes indeed. it creates a container, runs the tests, and then destroys the container. and you can also use own containers instead. That adds a tiny amount of overhead compared with no container, but you don't have an option about that. Running automated tests does indeed have an environmental cost, as a computer somewhere is doing more work than it would otherwise have done.
    - thanks!

- If we have multiple code files in repository then we need to add line for every file including test in Github Action workflow?
  - this depends on the project language and test runner. if this is about pytest, then it can also gather all tests in a python package so it is not necessary to add one line for each file. (if i understood the question correctly)
    - For example, a C++ project using CMake with CTest would register each test binary (or python script) with CTest, which would be run by "make test." Now only that line needs to be part of the workflow .yml file, but that's your choice.




- Why does github asks me again all the time for login/password? Last week I worked on a different repo on github, now I am working on the repo for the coderefiner workshop and it has started to ask me before every push. How does git know to push to which repo when I work on several, please?
  - If you cloned using SSH (`git clone git@....`), it will use public-key authentication and *not* ask for a password. If you cloned using HTTPS (`git clone https://`), then it will ask for a password. When working on a repo that is not yours, the default is anonymous HTTPS clone.
      - Thank you. I was lazy and did `git clone https://` I did not know about the git@ prefix. Can I fix this still, please?
        - You can get your hands dirty with `git remote rm origin` and then `git remote add origin git@whatever-it-is` and then teach each local branch  which branch of the remote it should track. Much easier to just clone with `git@whatever-it-is` separately (or follow the advice below!)
           - or: `git remote set-url origin git@someaddress` which will change to `git@someaddress` from whatever it was before


**Exercise until 11:47**

Please also write here questions or surprising/interesting findings which can be good for other groups.

- Any test case to test the factorial can only test a finite sample. Testing the first few instances is prone to missing deviations at large n. I think it might make sense to test whether factorial(n+1)=(n+1)*factorial(n) where n can be a random integer greater than 1 (maybe not too large ...).
  - good approach! sometimes you have two functions that implement the same thing. a simple, obviously correct, slow function, and a more complex fast function. and then it can be useful to compare both for a random set of input values and design a test this way.
    - yes, that would be a better approach: it's called *property-based testing* and in Python you can use the Hypothesis library to help you with generating test sets.
      - sometimes you can even test exhaustively every possible input value and compare it to some source of truth (e.g. that a fast, complex, hard-to-read implementation does the same as a slow, simple, comprehensible one)

- Can I use print statements with the pytest test functions?
    - Yes. More info here: https://docs.pytest.org/en/stable/capture.html?highlight=print%20statement
        - `pytest -s myfile.py`

- When testing randomness in Python. Is there a good way to fix the seed within the function, but not change the global seed that is used for the other tests? (One idea I just had to was to extract the current seed, set a seed (1), run function, then restore the original seed?)
  - I believe you need to use an external library implementing pseudorandom generators or even use a completely different generator.
    - Refactor the function so that it does not have the external dependency on a global rng, but rather a specific one. Now you can control that in the test, while letting the normal code use the global one. (y)

- Why does pytest not find my file? Terminal output and file content below.

```
username@machine:~/pytest-example$ pytest test_yahtzee.py
==================================================================================== test session starts =====================================================================================
platform linux2 -- Python 2.7.18, pytest-4.6.9, py-1.8.1, pluggy-0.13.0
rootdir: /home/username/pytest-example
collected 0 items                                                                                                                                                  =============================================================================== no tests ran in 14.43 seconds ================================================================================
```

```python
# The following is test_yahtzee.py
###########################################################
from yahtzee_library import *

num_games = 1000000

winning_games = list(
    filter(
            lambda x: x == 5,
	            [yahtzee() for _ in range(num_games)],
		        )
			)
			#print(100 * len(winning_games)/num_games)
			assert abs(len(winning_games)/num_games - 0.046) < 1
			###########################################################
```

- it looks for functions that start with `test_` and runs them

- But the file is called test_yahtzee.py
  - inside there you need to create a function `test_something()` and move the test under that function
    - Thanks! :)

- What if the code imports external packages? Referring to "4. Function with an external dependency". What if it's not a simple value, but a complicated function
    - It's normally a good idea to wrap external packages with a layer that you control that gives you the ability to e.g. swap it for another package (or version of the same package), either for testing or actually switching packages. So if you do that, then the dependency problem is easier. Also, you can refactor the code from ``code_to_test()`` to look like ``value = get_from(dependency); code_to_test(value);``

- I read in the past that an impure function is also when, for example, the text input `mytext` is modified and the function returns `mytext`. Do you see problems with this types of functions?
  - any function which accesses the disc or keyboard or internet or database is inherently impure since the disc and keyboard and internet are "time-dependent" and will change from call to call. but functions which access files can still be tested (see one example in test design) by creating a temporary file or temporary database, run the function, verify the result, then destroy the temporary file/database. in practice i would recommend to move the I/O (file/internet/database-access) to the "outside" of your code and keep the "inside" of your code pure and stateless and easy to test.
        - but this function, which does not access the disc or anything, is it impure and potentially problematic? Notice that it modifies the input variable only inside the scope of the function and then returns it. I am asking because it is relevant to the code I am working on.
          ```
          def add_x_to_input(mytext):
              mytext = mytext + 'x'
              return mytext

          mytext='some text'
          mytext = add_x_to_input(mytext)
          ```

     - this function can be considered pure: given an input it will always produce the same output. and it does not modify any variables outside the function. although it looks like it would modify `mytext`, it modifies its copy and returns a new value which you then choose to put into the same "container" but the function itself does not modify the input `mytext` hence I would call this one pure.
        - Right, cause strings are immutable. Cool, thank you.

- How do you test functions that render file formats, such as images?
    - understand what you expect the behaviors to be
        - have a set of test images and record the results so you can compare them pixel-by-pixel in future, but you'll need a human to decide up front that those results actually are good
	    - i find this approach useful: what do you look at to decide whether the generated image is correct? now write these criteria down. can you put these criteria into code? (this is the difficult part). once you have the criteria written in any language, you have a test. i know it's not easy but defining and writing down these validation criteria can be a useful exercise.
	        - more practically: you could store the checksums of generated images for a series of input parameters and check whether you regenerate the same result by comparing the checksum.

- More on the previous question: say that my program converts some text file to a text file e.g. html. how to write tests there? For example, testing that a link in my output is written in the correct syntax and points to some paragraph in the output itself, but avoid whitespaces or whatever changes in the html syntax that are not relevant.. One could probably do this, but if you know of any syntax-aware library (for html or markdown or python) or tips let me know
  - just to make sure I understand: you are looking for a library that can validate html and markdown and check internal links?
        - Well, maybe. I am wonder how you would write tests for software that converts from one text format to another, e.g. to html (but not only). I cannot diff some reference html file vs the html output as is because, for example, some .js file in the `<head>` will change in time, I don't want line breaks or comments to make tests fail, etc. I should probably massage the html output/use regex before diff-ing. It sounds like a hassle.
	      - I discussed it with Thor and I should probably start testing on my low-level functions in my software and go from there.

- Interesting: I asked what was the difference between `master` and `main` in git.
    - It is the same, but the `main` syntax is more inclusive

- Do you have any possible answer to the section Designing an end-to-end test [here](https://coderefinery.github.io/testing/test-design/)?
  - sorry we need to create a solution and I only created the problem yesterday but in this particular case I would keep a folder with inputs and outputs and the end to end test would loop through all inputs, run the code, and compare the produced output with each reference output. in this case one could compare strings precisely, whether they are identical. if the code produced floats, one would have to compare with numerical tolerance. sometimes code produces results but also prints times and dates and timings and then one needs to do some filtering.

- How do you test functions that rely on external API calls? Maybe with a focus on API:s that may be subject to change, is that defensive programming rather than testing?
  - here my focus would be to test this often/frequently so that once things change, i notice this. one can run scheduled tests on github which are run every day/week/month. there are also tools that focus on testing API changes/degradation (i am not using them myself but only saw that they exist)
    - You'd need both. The tests help you understand what has changed. Then your code can be changed to react accordingly, e.g. support multiple versions. Key here is that you wrap the external API in a layer that you control. That lets you make observations (ie run tests) before it gets into the core components of your code. Maybe you can introduce a change in the layer that means your core components are insulated from the change to the external API.


Discussion from group 1: What are pure/impure functions in practice? Difficult to test functions that render files or rely on external API:s. Randomness is complex and inticate. We chose test-driven development.

Test-driven development is like writing specification as testing code before writing the actual implementation code. Check the written conditions/criteria and translate them into tests according to the testing framework. E.g. "takes an integer argument" -> test_int_fizzbuss(). Writing the test forces you to learn more about the problem/what the implementation needs, e.g. validation of the type of argument and raising an error, e.g. TypeError for bad arguments.


#### Quick feedback

Please write down one thing you liked and one thing you think should be improved!

Good:
- Nice overview on existing testing strategies
- Great concepts and test design sections
- Very good onboarding process. I was scared of implementing testing, now I look forward to it.
- Great intro with good pace, will join similar things in the future
- Great to have an instance to work this excercises out with others.
- Great organization, use of HackMD and instructing
- Exercises are good but sometimes get complex. A universal online environment for everyone should be identified.
- ending comments on how to get started on existing codebase were really were good. (Maybe add them to the docs?)
- Good overview about testing, gives me some inspiration for testing!
- Very nice documentation but needed to be updated for version as we were wondering if differencies were due to different versions, however very comprehensive
- Nice to have a session dedicated to testing and very interesting content !
- Very nice that you catch questions from the chat and bring them to the speaker's attention. Thanks!
- Good and quick answers to the questions asked in the HackMD.


To improve:
- CI/CD did not work for institutional gitlab accounts with no configured runners
- not Familiar with Github so struggled there
- maybe add example of test cases for one particular function (e.g. range checks for list input, invalid indices)
- did not have a helper in the room when we needed one in the difficult second part
- It was great! But (this is more of a question), will there be more advanced labs in the future (asking for a friend, who is familiar with the content of todays lesson). Also mocking, could be added, which I do not understand at all. Otherwise great, this is really needed in research!!!
-  It would be helpful to have a session on integration tests and end-to-end tests, in particular, since you recommend this as the first step
- Maybe reduce diversity of platforms/languages to focus more on testing as a concept. An instructor-led discusscion of the last segment (test-design) would have been more helpful.
- The last part on "test design" became way too rushed - try to reduce the number of exercises here, or split them over more breakout exercise sessions. A lot of attendants didn't even have time to get the examples to compile/their testing environment to work. When we finally started screen sharing an environment that worked, the time was out, and we had barely covered anything.
- too short perhaps +1
- More time for exercises+1
- I think as well, it was way to short. We also did not have a mentor, but we worked well as a team, but this slowed us down.
- There should be guided exercises in Breakout rooms and less exercises so concepts can be learned qualitatively not quantitatively.
- Perhaps have some examples of really good tests
- The exercise of Test design section needs more time. Probably double.
- No "real" mentor in our room, so felt a bit lonely to take decisions
- Would have liked more time on the last excercise since that was the most interesting one for me :)
- Is there a document or a section for feedback? I would like to write it before I forget :)
- *I will write it here. Please move it later to the appropriate place.* I had to create a Gitlab account and the instructions in the lesson on Automated testing and CI for pushing to the new repo did not match the steps needed. I suspect it was because people creating the instructions in the lesson alreay had an account. So maybe you would like to consider starting from scratch and creating a new account for those instructions.
      - thanks for this feedback. indeed this was steep learning and we need to improve this.
- Would be good to have some more detailed instructions on the setup requirements for either github or gitlab (as often people have different defaults). More guidance with the exercises would help.
- missing code repo were all groups could put their creative work
- Would it be helpful to somehow differentiate breakout rooms according to participant skill level? I understand you could be more clear about prerequisites (e.g. everyone should have done a fork/clone/pull request on someone else's repo *before* the workshop if this is expected knowledge), but differentiating groups on skill could possibly facilitate the level of instructor time or how it is allocated. Some groups with more advanced participants may want to move forward on their own, with possibility for expert support, where other groups could aim to cover the basics and have support focused on this. Understand this is always a challenge though!
- In one group I was in, the focus was a lot on just "getting done" for the first exercise, under silent and independent work. Could you perhaps clarify that participants shouldn't be afraid of asking questions, and that if you are done early, it is welcome to offer to help others who need it (if this is indeed the idea)? An ideal experience from the learner is probably to be in a group with people of the same skill level (approx), to know each other a little bit (to not be afraid to ask), and to get good help.

---

### Discussion during the hackathon on March 24


- How to make sure that a temporary files gets deleted after the tests? Using fixtures maybe?
    - one example from the testing lesson:
    - Oh, I did use the example below but it still happened that the files did not get removed. I'll try again
    

```python
import tempfile
import os

def test_count_word_occurrence_in_file():
    _, temporary_file_name = tempfile.mkstemp()
    with open(temporary_file_name, 'w') as f:
        f.write("one two one two three four")
    count = count_word_occurrence_in_file(temporary_file_name, "one")
    assert count == 2
    os.remove(temporary_file_name)
```

- Maybe the **shutil** package for file operations could be an option: https://docs.python.org/3/library/shutil.html
    One example here: https://stackoverflow.com/questions/62210497/how-to-automatically-delete-temporary-files-generated-during-pytest

    - Working example:

```python
import shutils

@pytest.fixture
def tdir():
    """Create a temporary testing dir"""
    tmpdir = tempfile.mkdtemp(prefix='test-doconce-')
    yield tmpdir
    shutil.rmtree(tmpdir)
    
def test_myprog(tdir):
    finput = 'testdoc.txt'
    #cp files to temporary directory
    shutil.copy(finput, tdir)
    #run myprog in bash
    out = subprocess.run(['myprog','arg1', 'arg2', finput, '--examples_as_exercises'],
                         cwd=tdir,
                         stdout=subprocess.PIPE,
                         stderr=subprocess.STDOUT,
                         encoding='utf8')
    print(out.stdout)
    assert out.returncode == 0
```

- hard-coded paths and adjustable parameters inside the main code make it difficult to design tests
    - one solution is to use config files. In Python, configparser library is convenient

- in Python, always use a requirements.txt or environment.yml file!

- testing Deep Learning methods is tricky!
    - DL practioners, do you test your DL workflow?
    - Fixed seed
    - Check that the model can overfit on small amount of data
    - Not really testing, but inspect the data manually (plot it)

##### team 1

We focused on the importance on having well written code which is easily portable across platforms. We implemented relative paths coding.

We learned that if you write a function thinking about "how to test it" it is much easier to write clean code.

We got familiar with python



##### team 2


- Complex code often has (a lot of) dependencies (e.g. compilers) which are hard to disentangle
- First step for regression testing is that code compiles
- pFUnit is a capable unit testing tool but has quite a lot prerequirements to run (e.g., CMAKE, ifort > 18)
- pure functions are much easier to test compared to functions/subroutines which depend on each other --> to fix this it would requires a change in the coding strategy

##### team 3

- Catch2 is a convenient unit testing framework: allows easy way for Behaviour Driven Design, incorporates well into CMake.
- One needs to make sure the input values in the tests fall within reasonable values and also test for the unreasonable inputs (the code should handle those inputs via asserts or exceptions).
- events in GUI applications can be tested:
    - either using tools for inspection of graphical events 
    - or by using a log file.

##### team 4

- Tests have several orthogonal ways of being described:
    - framework orchestrating the tests (GoogleTest, pytest, Catch2, DocTest)
    - who provides truth (regression tests assuming the old code was right (no it is for checking if something has changed), comparison tests assuming simple current code is right, oracular tests where some physical or mathematical property provides truth)
    - how much code is tested (unit, integration, end-to-end)
- Extracting dependencies can make code more testable, moves code closer to object-oriented design. However, data-driven design can be more performant, so compromises might be needed
- When proposing new science projects or code features, discuss testing up front. How will we know the observations are new science or code defect?
- Consider designing tests before a new feature is implemented.
- Support more than one compiler to get more feedback and write fewer bugs to catch in testing. Clang can compile and run CUDA code, not just nvcc. Multiple compiler support can also lead to improved code portability.
- Consider Sanitizers for memory, address, undefined behavior, leak, thread errors
- Consider AWS CodeBuild for GPU CI testing - the free tier might be enough for you to get some automated coverage
- Otherwise, free CI will at least compile GPU code if you can automate setting up the dependencies
- Do exactly what the user says. Do not do something "clever", i.e. assuming that the user wants something else than he/she told the program to do. If the user was vague, then be clever. Just don't contradict them!
- Setting up code coverage testing can give valuable high-level feedback about how the code has changed. This can be helpful when arguing for funding. But beware of spending time chasing "complete" coverage - you probably have better ways to spend time.
- Research code often has a "conflict of interest" between developers and the PIs/drivers/funders of the projects, and/or it often feels like there is too little time to do proper testing. To improve the situation, try to find a way to prioritize what to test. Test coverage and looking for coverage gaps (e.g. with Gcov) might a useful approach. Test all new code versus old code when possible. One approach can be to profile to see which functions are used the most frequently, but this doesn't necessarily mean they should have a high priority.
- Some tools that might be helpful: sanitizer toolsets, thread sanitizers, run-time vs static analyzers, valgrind, cuda-memcheck, cppcheck...
- Add tests that cover areas that are expected to change
- Remove legacy tests after considering what coverage change that makes

##### team 5

- We ended up learning a lot. Parametrized testing, regression tests (with and outout storing files) and end-to-end tests.
    - Any tip/code snippet for doing regression tests? Is it done on git or in pytest?i
    - We ran the regression tests ourselves and copy-pasted the expected results into a test function. In other cases we stored the expected result in a .npz file. Example:
        ```python
        @pytest.mark.parametrize("mean,var,expected",[
                            (2,3.5,[[8.17418321], [3.40055023]]),
                            (3.141592653589793,2.6457513110645907,[[7.80883646],[4.20030911]]),
                            (-1e-09, 1000000.0,[[1764052.34596766],[400157.20836722]]),
                            (1.7724538509055159, 0, [[1.77245385],[1.77245385]])
                        ])
        def test_Normal_sample_regression(mean,var,expected):
            rng = np.random.RandomState(0)
            samples = cuqi.distribution.Normal(mean,var).sample(2,rng=rng)
            target = np.array(expected)
            assert np.allclose(samples,target)
        ```
- Compared to zero testing one week ago, we now have a working automated test pipeline in Gitlab, with multiple unit tests and at least one end-to-end test.
- We spent a good amount of time on handling RNG and ended up with a pretty good solution thanks to Roberto!
- As a byproduct we also got to exercise collaborative git and gitlab workflows including rebases, merge request reviewing, as well as setting up a mirror repo to give access rights to Roberto.

##### team 6

- There were many existing tests, but they were run via a shell script and you needed to do manual comparison.
- We created a fixture to work on a temporary directory (see code in Q&A above)
- capture STDOUT STDERR (see my Q&A above)
- tip: run `pytest --pdb` (it opens a debugger when a test fails)
    - Thanks for this suggestion :) 
    - Aha! TIL 
- Testing shell functions is hard, because they depend on the environment.  But it can be done.
- Working directories and relative pathnames require some care to get correct

##### team 7

- Step-1: needed to find a platform to run/test code (we won't use HPC for testing the simple code). Tried google console & mybinder
- Put the code in a repository
- Installed PFunit used to test for Fortran. Used a square example to make sure we could compile Ok. Broke it and fixed it.
- started to design a test for interpolation code but still some work to do.
- Got some experience with updating the github repository, and then pulling back to the local machine
- Learnt to use HackMD
- Did not finish!

##### team 8

- Comparing different dictionaries -- deepdiff (https://github.com/seperman/deepdiff#a-few-examples)
- Dependencies within the code base
- Splitting tests into smaller units, always try to split it
- Setting up the environment, or compiling dependencies



##### team 9

- Countinous Integration tests is an indispensable tool to find issues related to target platforms.
    - Found alot of issues by having the different compilers and platforms
- UTest is a small, fast and lightweight testing framework for C and C++.
    - https://github.com/sheredom/utest.h
  - nice find! I did not know about this one. 
- Integrates nicely into Cmake CTest. (Thanks mentor! :))
- Unittests are needed!

##### team 10

- We learned about arranging tests in a hierarchical manner to match the project structure
- Learned about using pytest.fixture decorator
- Got some great advice in general, e.g. dataclasses and pathlib packages
- Discussed optimal class development
- Found a couple of bugs...


##### team 11

- Learned to make a config file
- Designed an end-to-end test
- Created a class 
- Discussed best practices in collaborative coding such as branching, pull requests etc.
- Learnt about creating environments (.yml files)
- Many suggestions about coding style
- Many suggestions about best practices in deep learning training
- Many other useful suggestions such as glob, os.path.split, context manager etc.

---

#### Feedback

Are hackathons useful? 
Would you like to attend hackathons with other themes in the future? If so, which themes? 
Any suggestions for improving the format?

- Hackathon theme suggestion: preparing your code for publication, and/or for going open source. :+1: 
- Hackathon/workshop suggestion: how to document & comment (large) software projects :+1:
- A refactoring workshop/hackathon with best practices presented, maybe some checklist what to look at/for, spaghetti code to modular code
- It was absolutely useful which helped to debug testing process when using nbdev. Thanks a lot to my mentor for clearing all our issues. 
- Absolutely useful. It motivates me to work on my project and I am inspired by your knowledge. You are a good inspiration to become better. I think a hackathon should be longer.
- Extremely time well spent. Having a chance to go through our own project with an expert is unique possibility. :+1:
- Hackathon on documentation!!! :+1::+1::+1::+1::+1:
- I can't believe this is free by the way. Great job. :+1:
- Great workshop, thanks a bunch! A bit of feedback/reflection: it was very easy for the hackathon to turn into a Q&A with little to no hacking. This is of course up to the participants and can still be very helpful. After all, each group should maybe use their mentor in the way that suits them the best. But if there is an expectation/desire to do live pair programming, maybe give more instructions to mentors, or use the short meeting with the mentor on the first day to set up a "homework" for a particular test or piece of code to go through in the second day (during the hackathon).
    - This is an impotant point! The quality of the hackathon may depend on the mentor -- so aligning the type of teaching/pair-programming may help. In our group we divided out "homework" that was then reviewed later, very useful.

- my lesson learnt:
  - old-style *vs* new-style random number generation in NumPy. One should prefer new-style (where *both* seed *and* PRNG algorithm are explicitly set), but it doesn't play well with the more well-known old-style, where the PRNG is part of the global state..
    - do you have a link/example of the new style?
      * this shows both: https://numpy.org/doc/stable/reference/random/index.html#quick-start
      * https://numpy.org/doc/stable/reference/random/new-or-different.html#new-or-different
      * New-style offers more flexibility when you need *multiple streams* for parallel applications (*e.g.* the Philox generator or PCG64/MT19937 with jump-ahead)
         - awesome. thanks!
  - utest is yet another unit test framework for C/C++. Very lightweight.

- my lessons learned:
  - one can actually automatically test jupyter notebooks
  - learned about https://nbdev.fast.ai/
  - learned how to compare Python dictionaries using https://github.com/seperman/deepdiff
  - mentoring more than 2 groups is not practical. sorry to each group that I had so little time
  - learned more about pytest fixtures: https://docs.pytest.org/en/stable/fixture.html

- my lessons learned:
    - use the standard library when possible
    - learned how to use pytest when the test func are defined in several subdirectories
    - learned that one may mimic GitHub action on my laptop https://github.com/nektos/act
    - a great oportunity to see what kind of tests are appropriate depending on the project
    - as always, Google is your best friend but it does not beat a mentor :)
    - do what works for you / your project


