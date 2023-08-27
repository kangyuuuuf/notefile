# Prairielearn Development

This content is used for CS 519 course development and future CS 357 development. Here is the [Information website](https://prairielearn.readthedocs.io/en/latest/). Mostly, I will focus on [Create content in the browser](https://prairielearn.readthedocs.io/en/latest/getStarted/) and [PrairieLearn Workshop](https://prairielearn.readthedocs.io/en/latest/workshop/). 

### Creating questions from scratch

To add a new question, go to the `Questions` tab and click on `Add Question` button, and remember to `change QID` to change the question ID name. `info.json` contains 3 parts:

**title:** the name of the question, help students to understand.

**topic:** the course topic that is related to this question. 

**tags:** for the filter purpose. Adding more tags will help other developers find this question.

#### question.html

The `question.html` is a template used to render the question to the student. A complete `question.html` example looks like:

```html
<pl-question-panel>
  <p>
    A particle of mass $m = {{params.m}}\rm\ kg$ is observed to have acceleration $a =
    {{params.a}}\rm\ m/s^2$.
  </p>
  <p>What is the total force $F$ currently acting on the particle?</p>
</pl-question-panel>

<p>
  <pl-number-input
    answers-name="F"
    comparison="sigfig"
    digits="2"
    label="$F =$"
    suffix="$\rm m/s^2$"
  ></pl-number-input>
</p>
```

The variable that is within the text content is given by `{{variable}}`. The variable will be replaced by the real value.  

#### server.py

Basically, it is the backend of the question. It contains the following functions:

| Function     | Return object                            | modifiable `data` keys                                       | unmodifiable `data` keys                                     | Description                                                  |
| ------------ | ---------------------------------------- | ------------------------------------------------------------ | ------------------------------------------------------------ | ------------------------------------------------------------ |
| `generate()` |                                          | `correct_answers`, `params`                                  | `options`, `variant_seed`                                    | Generate the parameter and true answers for a new random question variant. Set `data["params"][name]` and `data["correct_answers"][name]` for any variables as needed. Modify the `data` dictionary in-place. |
| `prepare()`  |                                          | `correct_answers`, `params`                                  | `options`, `variant_seed`                                    | Final question preparation after element code has run. Can modify data as necessary. Modify the `data` dictionary in-place. |
| `render()`   | `html` (string)                          |                                                              | `correct_answers`, `editable`, `feedback`, `format_errors`, `options`, `panel`, `params`, `partial_scores`, `raw_submitted_answers`, `score`, `submitted_answers`, `variant_seed`, `num_valid_submissions` | Render the HTML for one panel and return it as a string.     |
| `parse()`    |                                          | `format_errors`, `submitted_answers`                         | `correct_answers`, `options`, `params`, `raw_submitted_answers`, `variant_seed` | Parse the `data["submitted_answers"][var]` data entered by the student, modifying this variable. Modify the `data` dictionary in-place. |
| `grade()`    |                                          | `correct_answers`, `feedback`, `format_errors`, `params`, `partial_scores`, `score`, `submitted_answers` | `options`, `raw_submitted_answers`, `variant_seed`           | Grade `data["submitted_answers"][var]` to determine a score. Store the score and any feedback in `data["partial_scores"][var]["score"]` and `data["partial_scores"][var]["feedback"]`. Modify the `data` dictionary in-place. |
| `file()`     | `object` (string, bytes-like, file-like) |                                                              | `correct_answers`, `filename`, `options`, `params`, `variant_seed` | Generate a file object dynamically in lieu of a physical file. Trigger via `type="dynamic"` in the question element (e.g., `pl-figure`, `pl-file-download`). Access the requested filename via `data['filename']`. If `file()` returns nothing, an empty string will be used. |

### PrairieLearn Elements

We can use the elements inside Prairielearn to modify our HTML file. The information is from [PrairieLearn Elements](https://prairielearn.readthedocs.io/en/latest/elements/). Some important elements will be stored in this file:

