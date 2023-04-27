## Tech Excellence

* [Martin Fowler – What Does Tech Excellence Look Like? | TW Live Australia 2016 ](https://www.youtube.com/watch?v=Avs70dZ3Vlk)
* [Making Architecture Matter - Martin Fowler Keynote ](https://www.youtube.com/watch?v=DngAZyWMGR0)
* [Garbage language](https://www.vulture.com/2020/02/spread-of-corporate-speak.html)
* [Linkedin bullshit](https://divinations.substack.com/p/linkedins-alternate-universe)
* [A NTIPATTERNS, Laplante, Neill](https://www.amazon.com/Antipatterns-Identification-Refactoring-Management-Engineering/dp/0849329949)

## My thoughts about Clean Coder

* Learn to say no and negotiate
* Providing too much detail can be an invitation for micro-management. (I provided many details than necessary, but I
  was always asked for "concrete" solutions )
* play for the team not on the team (saying it's slow team needs micromanagement)
* people like to keep their jobs, that's why they bend, and that's exactly what happened when team backed down on their
  original decisions to split the team
* I thought of sacrificing my principles and go with the flow, but I've tried this many times, and it didn't work. I can
  only learn from negotiations and open-minded discussions and hopefully not Mistakes!.
* Passive aggressive team leads, "he will finish 10 weeks from now!"
* "Do or don't , there is no trying " Yoda
* The promise to try is an admission that you’ve been holding back, that you have a reservoir of extra effort that you
  can apply. The promise to try is an admission that the goal is attainable through the application of this extra
  effort; moreover, it is a commitment to apply that extra effort to achieve the goal.
* The moment I noticed I'm not interested in business I should have left the team
* Professionals are not required to say yes to everything that is asked of them.However, they should work hard to find
  creative ways to make “yes” possible. When professionals say yes, they use the language of commitment so that there is
  no doubt about what they’ve promised.
* The key to mastery is confidence and error-sense.
* TDD:
    * The tests you write first are offense. After-the-fact tests are written by someone who is already vested in the
      code and already knows how the problem was solved. There’s just no way those tests can be anywhere near as
      incisive as tests written first.
* Acceptance Testing:
    * QA typically writes the "unhappy path” tests, the boundary conditions, exceptions, and corner cases. This is
      because QA’s job is to help think about what can go wrong.

## Test Automation Pyramid

* **Exploratory -Manual- 5%**
    * The goal is not coverage.the goal is to ensure that the system behaves well under human operation and to
      creatively find as many “peculiarities” as possible.
* **System Tests - GUI- 10%**
    * The Ultimate integration tests. Almost same as Integrations tests but for UI
* **Integration Tests - API- 20%**
    * These tests only have meaning for larger systems that have many components.
    * these tests assemble groups of components and test how well they communicate with each other.
    * Integration tests are choreography tests. They do not test business rules. Rather,they test how well the assembly
      of components dances together. They are **plumbing** tests that make sure that the components are properly
      connected and can clearly communicate with each other.
    * Integration tests are typically written by the system architects, or lead designers, of the system. The tests
      ensure that the architectural structure of the system is sound. It is at this level that we might see performance
      and throughput tests.
    * Integration tests are typically written by the system architects, or lead designers, of the system. The tests
      ensure that the architectural structure of the system is sound.
    * It is at this level that we might see performance and throughput tests.
    * They are typically not executed as part of the Continuous Integration suite, because they often have longer
      runtimes.
* **Component Test -API- 50%**
    * Generally they are written against individual components of the system. The components of the system encapsulate
      the business rules, so the tests for those components are the acceptance tests for those business rules.
    * It passes input data into the component and gathers output data from it. It tests that the output matches the
      input. Any other system components are decoupled from the test using appropriate mocking and test-doubling
      techniques.
    * Component tests are written by QA and Business with assistance from development. They are composed in a
      component-testing environment such as FitNesse, JBehave, or Cucumber. (GUI components are tested with GUI testing
      environ-ments such as Selenium or Watir.)
    * They are directed more towards happy-path situations and very obvious corner, boundary, and alternate-path cases.
      The vast majority of unhappy-path cases are covered by unit tests and are meaningless at the level of component
      tests.
* **Unit Tests 100%**
    * written by programmers, for programmers, in the programming language of the system.
    * They are executed as part of Continuous Integration to ensure that the intent of the programmers’ is upheld.

## Time Management

### Standup Meetings

> One Minute per Person, to answer each question in 20 seconds

1. What did I do yesterday?
2. What am I going to do today?
3. What’s in my way?

### Iteration Planning Meetings

> Iteration planning meetings are meant to select the backlog items that will be executed in the next iteration.

* **Estimates** should already be done for the candidate items.
* **Assessment** of business value should already be done.
* In really good organizations the **acceptance/component** tests will already be written, or at least sketched out.
* Meeting should take no more than 5% for one Week iteration (40 hours) meeting should take 2 Hours

### Iteration Retrospective and Demo

* These meetings are conducted at the end of each iteration. Team members discuss what went right and what went wrong.
* Stakeholders see a demo of the newly working features.
* 20 minutes for retrospective and 25 minutes for the demo.

### Arguments and Agreements

> “Any argument that can’t be settled in five minutes can’t be settled by arguing." Kent Beck- Creator of XP

* Technical disagreements, should be backed with DATA
* Some folks will be passive-aggressive. They’ll agree just to end the argument, and then sabotage the result by
  refusing to engage in the solution. These are the worst, if you agree then you must engage.
* If an argument must truly be settled, then ask each of the arguers to present their case to the team in five minutes
  or less. Then have the team vote.

### Focus

* Physical Exercises
* Pomodoro Technique is that 25-minute window of productive time that you aggressively defend against all interruptions.

### Set priorities to avoid procrastination

### Blind Alleys

The Rule of Holes: When you are in one, stop digging.

### Messes

Messes are worse than blind alleys because you can always see the way forward, and it always looks shorter than the way
back (but it isn’t).

### Estimation Using PERT

O: Optimistic Estimate. N: Nominal Estimate. This is the estimate with the greatest chance of success. P: Pessimistic
Estimate. Once again this is wildly pessimistic.

* M (mean | Expected time)=(O + 4 N + P )/ 6
    * μ is the expected duration of the task.
* Sigma (Standard Deviation) = P-O / 6
    * is the standard deviation 4 of the probability distribution for the task. It is a measure of how uncertain the
      task is. When this number is large, the uncertainty is large too.

* Probability distribution for the entire set of tasks is **Mu= Sum{Mues}**
* The standard deviation of the sequence is the square root of the sum of the squares of the standard deviations of the
  tasks: **Sigma=Sqrt(Sum(sigma^2,sigma^2, ....))**
* Standard Deviation Rules:
    * 68% fall between 1Sigma
    * 96% fall 2Sigma
    * 99% fall under 3 Sigma
* Estimation then goes through 1Sigma, 2 or even 3.

### Standard Deviation in general

x ---- x' ---- x-x' ---- (x-x')^2 Then => Sqrt( mean of (x-x')^2 points) is equal 1 Sigma

### Tasks Estimation (Wideband Delphi inspired)

* Flying Fingers
    * 1 - 5 fingers, if all say 4 and one says 1, then they should talk, if all 3-4 then it's good
    * scale is needed of course
* Planning poker
* Affinity Estimation
    * No discussion allowed until arrangement is finished
    * Cards put randomly on table
    * longer tasks put to the right, lesser to the left
    * any member can rearrange a card even after it was moved
    * A card that is moved around
    * then put the tasks into Five buckets in a Fibonacci sequence (1, 2, 3, 5, 8) is traditional.

After any of the previous **Trivariate Estimates** meaning do it in three times for P, O, N, to get the probability
distribution.

[The Law of large numbers](http://en.wikipedia.org/wiki/Law_of_large_numbers) : Break tasks into smaller pieces for more
accurate estimates

## Handling Pressure

Choose disciplines that you feel comfortable following in a crisis. Then follow them all the time. Following these
disciplines is the best way to avoid getting into a crisis.(don't drop TDD in crisis, or start pairing in it)

Communicate, rely on your disciplines, get help

## Teams and Projects

* Professional development organizations allocate projects to existing gelled teams, they don’t form teams around
  projects.

## Tools

* RobotFX, Green Pepper, Fitness, Cucumber, JBehave
