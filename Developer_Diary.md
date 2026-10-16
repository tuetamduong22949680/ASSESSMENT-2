# Developer's Diary
## ISYS2001 Assessment 2 – Smart Savings & Spending Planner

> Note: I did not record the exact date of every decision at the beginning of the project. The early entries are grouped by the stage/week where I remember doing the work. From Week 9 onwards, I started coding more actively and the development became much easier to track.

---

# Before Week 9 – Planning the idea

### What I was trying to do

My original idea was actually quite similar to the final app.

I wanted the user to enter their income and spending, then the program would calculate how much money was left and whether they could reach a saving goal.

At first, I imagined something much more basic. I thought it would be similar to the exercises I had already done in Colab: enter some information, run the code, then get some text or boxes showing the result.

I did not start coding immediately because I spent a lot of time deciding what the app should actually do.

I kept thinking about things like:

- What information does the user need to enter?
- What should the app calculate?
- How should multiple goals work?
- What happens if the user does not have enough money?
- What features are actually useful?

This planning stage took much longer than I expected.

### How I used AI

At this stage I mainly used ChatGPT to discuss the idea and challenge different features before I started building them.

A lot of my prompts were basically me explaining an idea, then asking whether it made sense or what problems it could create.

### What I learned

Looking back, spending a long time planning was probably a good decision.

I realised that if I started writing code without knowing what the whole app was supposed to do, it would be very easy to end up with a lot of disconnected functions.

The main idea from this early stage stayed all the way to the final version:

**Income → Expenses → Money Remaining → Saving Goals → Financial Plan**

---

# Week 9 – Building the first working draft

### What I was trying to do

Week 9 was when I started seriously coding the project.

I did not try to build the final app immediately.

I started with the core calculations first and treated it as a draft.

I focused on things like:

- converting income and expenses into weekly amounts
- calculating usable income
- calculating total expenses
- calculating how much money was left
- calculating how much could go towards saving goals
- calculating the minimum saving required for each goal

Once one part worked, I added another part.

### AI collaboration

For most of the calculation logic, I already had an idea of how I wanted the functions to be divided.

AI helped me turn the idea into Python, check problems and suggest some extra cases that I had not considered.

One thing I tried to keep consistent was:

**Python should do the actual financial calculations.**

I did not want Gemini to calculate important values because I wanted the results to be predictable and testable.

### Earlier draft

I kept an earlier notebook because it shows what the project looked like before the final UI and later improvements.

[View my earlier project draft](ISYS2001_Assessment2_Finance_Assistant_Draft.ipynb)

At this point, most of the project was still functions, calculations and outputs inside Colab.

The final user interface did not exist yet.

---

# Week 9 / Early Development – Gemini was much harder than I expected

### What I was trying to do

One of the main ideas of my app was letting users describe their finances naturally instead of forcing them to fill in many separate fields.

For example, someone could say something like:

> I earn $900 every week and my partner contributes $300.

Gemini would extract the useful information and Python would calculate the financial plan.

### The problem

This worked quite well when the input was simple.

The problem started when the user wrote something longer, unclear or slightly complicated.

Gemini sometimes:

- misunderstood the amount
- used the wrong frequency
- missed information
- guessed information that was not provided
- returned data in an unexpected format

This was probably one of the most frustrating parts of the whole project.

I realised very quickly that just saying "extract the financial information" was not enough.

### How I worked with AI

I kept going back and making the Gemini instructions more specific.

I added rules for things like:

- expected JSON structure
- allowed frequency values
- goal priority
- date format
- not inventing missing information

I had to be much more specific than I originally expected.

Even connecting Gemini itself caused problems for me. At one point I could not get the API to work properly and eventually had to use another account before it worked.

### Reflection

This was one of the first times in the project where I realised that AI does not automatically understand exactly what I mean.

If my instructions are unclear, the result can also be unclear.

I became much more careful with how I wrote prompts after this.

---

# Early to Mid October – The project started getting much bigger

### What happened

Once the core version started working, the project expanded very quickly.

I kept seeing things that could be improved.

The project grew from a basic income/spending calculator into something with:

- multiple saving goals
- goal priorities
- goal management
- transaction tracking
- CSV uploads
- weekly summaries
- saving suggestions
- an AI finance assistant
- save/load
- charts
- a full Gradio interface

This was good because the app became much more useful, but it also caused a lot of stress.

Every time I added one feature, it could affect another part of the app.

### One weakness I noticed

I definitely have a habit of thinking:

> "This feature is possible, so maybe I should add it."

That caused some scope creep.

Near the end I had to become more careful and ask whether a feature actually improved the app enough to justify the extra complexity.

---

# Mid October – Removing currency conversion

### What I originally wanted

Currency conversion was one feature I genuinely wanted.

As an international student, I liked the idea of being able to work with AUD and another currency such as VND.

It felt personally useful to me.

### Why I changed my mind

Once I thought through the actual user flow, I realised it would make the app much more complicated.

The user would have to provide extra information about currency, and the project would also need additional conversion logic or another API.

For a budgeting and saving app, I did not think the extra complexity was worth it.

So I decided to make the final app AUD-only.

### Reflection

This was a useful lesson because removing a feature does not always mean the project is worse.

Sometimes keeping a feature simple is more useful than adding another feature just because it is technically possible.

---

# Mid October – I disagreed with AI about Manage Saving Goals

### What I was trying to do

As the interface became bigger, I asked AI to help me simplify it.

One suggestion was to reduce or remove the Manage Saving Goals section from the UI because it was making the app larger.

I did not agree with this.

For me, goal management was one of the key features.

If the user's situation changes, they should be able to change their saving goal instead of creating a completely new plan.

### AI interaction

AI originally suggested simplifying it:

> "Manage Saving Goals → bỏ luôn. Core add/edit/pause vẫn còn trong Step 5 nhưng UI không cần nhét hết mọi feature vào."

I pushed back and asked:

> "ủa cái mange ok mà, nhưng mà k sài được, kiểu ngta đổi ý muốn adjust cái goal thì sao"

After that discussion, the solution changed.

Instead of removing the feature, the UI was redesigned so that a user could:

- select an existing goal
- Edit
- Pause
- Resume
- Cancel
- Add a new goal

The plan then recalculates after the change.

### Screenshot

![AI suggestion to simplify Manage Saving Goals](<ChatGPT Image Oct 16, 2026, 11_31_38 AM.png>)

![My feedback and revised Manage Saving Goals design](<ChatGPT Image Oct 16, 2026, 11_31_57 AM.png>)

### Reflection

I think this is a good example of how I used AI in this project.

I did not accept a suggestion just because it would make the code easier.

I thought about what I wanted the app to do and kept the feature because I considered it part of the main idea.

---

# Mid October – Building the UI

### What I was trying to do

The UI was not part of my original plan at this level.

Originally, I thought the final project would still look mostly like a Colab notebook.

Once the core logic worked, I realised I still had time and I had AI support available.

I did not want to set my own standard too low just because the UI was harder.

I had already spent a semester learning programming, so I wanted to see how far I could take the project while still understanding what was happening.

### How AI helped

This is probably the area where AI helped me the most.

Gradio layout, event connections and UI code felt much more advanced to me than the normal Python functions.

AI helped me create and debug the interface while I decided how I wanted the user flow to work.

The final flow became:

**About You → Budget → Final Check → My Plan → Tracking → Assistant → Save**

### What I actually liked most

The visual design was nice, but the thing that made me feel like the app was finally working was not the colour or styling.

It was the **flow**.

When I could enter income and expenses, create goals, generate the plan and then get a clean summary that actually made sense, that was the point where I felt:

> "Okay, this actually works like the app I imagined."

That part felt much more like my own achievement because the flow came from the idea I had from the beginning.

---

# Mid October – Adding something I learned in class

### What I was trying to do

While working on the tracking section, I remembered that we had worked with charts during the unit.

The app already had a table comparing planned spending and actual spending.

I thought a chart could make the result easier to understand and also connect the project to something I had learned in class.

### AI interaction

I asked:

> "thầy có chỉ làm cái biểu đồ ấy... có cho vào được k"

AI suggested using a real **Planned vs Actual bar chart** with Matplotlib instead of only using an icon or decorative visual.

### Screenshot

![Discussion about adding Planned vs Actual chart](<ChatGPT Image Oct 16, 2026, 11_32_06 AM.png>)

### What I did

I decided to add the chart.

I kept both the table and the chart because they serve different purposes:

- the table shows exact numbers
- the chart makes differences easier to see quickly

### Reflection

I like this feature because it did not come from AI randomly suggesting another feature.

I remembered something from class and then used AI to help me integrate it into my own project.

---

# Mid October – Tracking actual spending

### What I was trying to do

I did not want the app to stop after creating a financial plan.

A plan can look good at the beginning of the week, but the user's actual spending can be completely different.

So I added transaction tracking.

Users can:

- enter transactions manually
- upload transactions using CSV
- compare planned and actual spending
- see overspending by category
- see how overspending affects their saving goals

### A small issue I noticed

One status originally said:

`under budget`

when the user had spent less than the planned amount.

The problem is that if the week is not finished, saying "under budget" sounds like a final conclusion.

For example, if the grocery budget is $180 and the user has spent $120 on Wednesday, they are not necessarily under budget for the whole week yet.

So the status was changed to:

`within budget so far`

while the period is still active.

After the week is complete, it can correctly say:

`under budget`.

### Reflection

This was a small change, but I think it made the result more honest and easier for a normal user to understand.

It also taught me that testing is not only about whether the number is mathematically correct.

The wording and meaning of the result also matter.

---

# Mid October – AI Finance Assistant

### What I was trying to do

The assessment required a conversational assistant using a real LLM.

I did not want the assistant to give completely generic finance advice.

I wanted it to understand the user's actual plan.

### What I decided

Python calculates the financial plan first.

Then the calculated information is passed to Gemini as context.

This includes things such as:

- income
- expenses
- available money
- saving goals
- minimum weekly savings
- goal priorities

Gemini can then explain the situation or answer questions based on that information.

For example, I tested a hypothetical question about cancelling one of the saving goals.

The assistant could discuss the effect using the current plan without permanently changing the saved data.

### Reflection

I prefer this structure because Gemini is good at conversation, but I do not want it to be responsible for the important financial calculations.

---

# 16 October 2026 – Restarting Colab exposed hidden problems

### What happened

One of the more stressful problems happened when code that had worked before suddenly stopped working after I restarted Colab.

The first time this happened, I honestly panicked a little because I could not understand how code could work before I closed the session and then fail when I opened it again.

Eventually I understood that some test code was depending on variables that were still stored in the old runtime memory.

After restarting, those variables no longer existed.

### What I changed

I changed the tracking test so that it creates all of its own test data inside the test.

It no longer depends on variables created somewhere else in the notebook.

After fixing this, I could restart the runtime and run the notebook much more reliably.

### Reflection

After I experienced this a few times, this type of problem became much less scary.

I started understanding the difference between:

**"The code works in my current session"**

and:

**"The notebook works properly from a clean start."**

That was a useful lesson.

---

# 16 October 2026 – Final testing and cleanup

### What I was trying to do

Near the end, I stopped adding major new ideas and focused on making sure the parts already in the app worked together.

I checked things such as:

- normal calculation tests
- invalid inputs
- edge cases
- goal calculations
- weekly tracking
- CSV input
- save/load
- Gradio button outputs
- the spending chart
- Gemini assistant responses

One problem I found was that after adding the chart, one Gradio function was returning fewer outputs than the button event expected.

The code had to be updated so the function also returned the chart.

This was the kind of bug caused by adding a new feature to an existing system.

---

# Final Reflection

This project became much bigger than I originally expected.

At the beginning I thought I was making a relatively simple finance calculator.

The main idea stayed the same, but the final version became a complete flow from entering financial information to planning, tracking and asking questions about the plan.

The biggest thing I learned was probably not how to manually write hundreds or thousands of lines of Python.

I learned how to use AI much more effectively.

At the start, I sometimes expected AI to understand what I meant without explaining every detail.

This project showed me that I need to be very specific.

I also learned that AI can suggest something that is technically easier but not necessarily right for my project.

There were times when I followed its suggestions, times when I modified them, and times when I disagreed completely.

I also understand much more about how an application is planned.

Instead of seeing the project as one huge piece of code, I now think about:

**idea → requirements → core logic → functions → testing → integration → UI → final testing**

I still think one of my weaknesses is that I keep wanting to add more features when I realise something is possible.

That made the final stage more stressful than it needed to be.

For my next programming project, I would try to freeze the main scope earlier and keep a stable version before adding optional features.

Even though AI helped me a lot, especially with the UI and debugging, I feel like the final app still represents the idea I originally wanted to build.

The part I am happiest with is the full financial flow.

The user can enter their situation, the app calculates it, turns it into a readable plan, lets them track what actually happens, and then helps them understand the result.

That was the idea I had at the beginning, and seeing that flow actually work was probably the most satisfying part of the project.
