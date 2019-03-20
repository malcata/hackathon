# Landing.jobs Hackathon

## The issue
At Landing.jobs we're trying to match great jobs with the best candidates. However we're still missing a lot of information on the behavior of our users. For example, we currently have no information on why certain people apply and others don't

You have data from the past year and a selection of our users can you create a model to predict which ones would apply at '2019-03-14'? You will be evaluated using the F1 Score.

## Answer File

The submitted file should be a `.csv` that has two columns

- person_id -> With the ids of the people
- applied -> With a 1 if that person submitted an application on that day ('2019-03-14') and 0 if not.

The score should be based on the F1 score when comparing the submitted IDs with what actually happened


## Data Dictionary

You will have 6 tables availables, their contents are the following:

### Applications:
- `person_id`: ID of the candidate
- `id`: ID of the application
- `job_ad_id`: ID of the associated Job
- `submitted_at`: When the application was submitted
- `created_at`: When the application was created (They can also be drafts)

### Jobs
- `id`: ID of the job
- `company_id`: ID of the company
- `experience_level`: Experience bucket of the job
- `last_published_at`: last time the job was published
- `closed_at`: Time the job was closed at

Experience can be inside the following buckets:

- 1 - Junior - Less than 2 years of experience
- 2 - Intermediate - 2 to 6 years of experience
- 3 - Senior - More than 6 years of experience

### People
  - `user_id`: ID of the user
  - `id`: ID of the candidate
  - `country_code`: Country code
  - `experience_level`: Experience level from 0 to 10+
  - `person_created_at`: when the user was created
  - `availability`: Category of availability
  - `remote`: Category of remote

Availability categories
  - "I'm not really looking, just curious" => 0,
  - "I'm actively looking for a job" => 1,
  - "I'm currently employed, but open to a new challenge" => 2

Remote Categories
  - 'Yes' => 1,
  - 'Remote positions only' => 2,
  - 'No' => 0

### Job Skills
- `job_id`: ID of the job
- `canonical_tag_id`: ID of the skill
- `tag_name`: Name of the skill

### People Skills
- `person_id`: ID of the person
- `canonical_tag_id`: ID of the skill
- `tag_name`: Name of the skill


### Views

- `id`: ID of the view
- `time`: When the visit happened
- `page`: Page that was visited
- `user_id`: ID of the user that has visited
- `visit_id`: ID of the visit

Some information:
View -> Single page click
Visit -> Collection of views
Users -> Both people (candidates) and employees

The `page` field may not make a lot of sense but it may be in part because it's anonymized. Here are some common page strings:

- `at/:company_id/:job_id` -> Visiting a job page
- ``-> Homepage


## Some important questions

- Are all users from the views people?
- How much data do you actually need?
