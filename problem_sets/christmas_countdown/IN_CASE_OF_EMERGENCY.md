# In-Case-Of-Emergency Guide: Christmas Countdown

Before using this guide, try to solve the problem on your own.

If you're stuck, use this guide to help you get unstuck.

## Decomposing the problem

Calculating the number of days until Christmas is a multi-step (or _composite_)
problem. Try to break it into smaller sub-problems.

### Simplify the problem and find a strategy

Before worrying about what code you'll write, think about the problem itself.

How would you'd solve this problem with only a calendar?

Start by trying to solve the simplest version of the problem. You can worry
about complications like leap years and starting from days between Christmas
and New Year's later.

Here's a pretty simple version: How would you find the number of days until
Christmas if you were starting on December 10th?

The most obvious strategy is to find December 10th on the calendar and then
count the days until you get to December 25th:

- Place your finger on December 10th
- Move your finger to December 11th and count "1 day"
- Move your finger to December 12th and count "2 days"
- ...

Or maybe you realized that, in this case, you could solve a simple subtraction
problem instead: 25 - 10 = 15 days.

That's the seed of a strategy! Starting from the start date, count days until you
get to Christmas.

### Dealing with complications

Next let's see if the strategy can be extended to deal with more complicated versions
of the problem.

It wouldn't be much harder to find the number of days until Christmas if you picked
November 10th as your starting date, would it? You wouldn't need to change your strategy.

- Place your finger on November 10th
- Move your finger to November 11th and count "1 day"
- Move your finger to November 12th and count "2 days"
- ...

Maybe you'd need to flip from November to December, but the strategy is essentially the same.

What about the subtraction shortcut? It's a little more complicated, but with a little tweak,
it still works.

days in November - 10 = days remaining in November
days reamining in November + 25 = days until Christmas

Okay, what if we started on June 10th? That'd be a lot of days to count, but we can
make good use of our shortcut:
days in June - 10 = days remaining in June
days remaining in June + days in July + days in August + days in September + days in October + days in November + 25 = days until Christmas

Are you noticing a pattern?

### Generalizing the strategy

We have a what looks like a viable strategy. Now let's figure out how to generalize it.

1. Find the number of days remaining in the current month and add it to the count
2. For each month between the current month and December, add the number of days
   in the month to the count
3. Add 25 to the count (since there are 25 days from the beginning of December to Christmas)

There are still corner cases and complications to consider, but this strategy looks like it
should work as long as we don't worry about leap years and pick a starting date that falls
before Christmas.

### Write some pseudocode

Even developers who are very comfortable with Python syntax find it helpful to start by
writing pseudocode -- a step-by-step plan for solving a problem that has the structure of
a Python program but doesn't worry about the details of Python syntax. Since you're still
getting comfortable with Python syntax, pseudocode can be especially helpful.

As you write your pseudocode, you can start to match up your problem-solving steps with
tools you know you have in your Python toolbox. For example, you might realize that you
will need to do the same or a similar calculation for each month between the starting month
and December. That sure sounds like a job for a loop!

Here's what some pseudocode might look like for our strategy:

```python
def get_days_until_christmas(day, month, year, check_leap_year=True):
    # create a variable to hold the count of days and set it to 0

    # find the number of days remaining in the current month and add it to the count

    # for each month between the current month and December,
    # add the number of days in the month to the count

    # add 25 to the count IF THE CURRENT MONTH IS NOT DECEMBER

    # return the count
```

That gives us a scaffolding for our function with room to fill in the details later.

Notice that creating the pseudocode pointed to a small problem in our strategy: we shouldn't
add 25 to the count if the current month is December. We hadn't thought of that! If we hadn't
found it now, we probably would have found it when we started testing our function.

### Fill in the code

### Try it out. Test it!

### Debug

### Handle corner cases: days after Christmas

Once you have a function that handles the common cases, it's time to rework or extend your logic to handle "corner cases".

We'll talk about leap years in the "bonus" section, below. Besides leap years, the one case
we haven't handled yet are the handful of days between Christmas and New Year's. See for
yourself. I bet if you input December 26th, your program will tell you that there are `-1` days
until Christmas. That's not untrue, but it's also not quite what we're looking for.
