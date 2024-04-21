## Corrsy Technical Assessment

At Corrsy, we are building educational mobile applications to help high school students study and practice using modern learning methodologies.

This usually involves taking short lessons (using text, image or video format) followed immediately by quizzes that verify students have acquired the necessary knowledge before moving forward.

Before starting this assessment, consider downloading the Corrsy app ([iOS](https://apps.apple.com/us/app/corrsy/id1587328977) or [Android](https://play.google.com/store/apps/details?id=com.corrsy)) to learn more about the app and its functionalities.

The Corrsy learning ecosystem is divided into the following hierarchies:
* **Grades**: describes the grade a student is currently enrolled in (e.g. Grade 9)
* **Subject**: represents the subject from the grade that the student is studying (e.g. Chemistry)
* **Chapter**: represents a chapter within the selected subject (e.g. Organic Compounds)
* **Lesson**: represents a lesson within a chapter from the selected subject within the selected grade
* **Widget**: this is the lowest-level of hierarchy, where a Lesson is made up of multiple Widgets. A Widget can be of three types: `textAndImages`, `video` or `multipleChoice` (i.e. a quiz). Think of Widgets as a page in a book

### User Stories and Functional Requirements
Your task is to build a small app that allows users to do the following:
* Select a Subject from the list of Subjects available for the Grade they're currently enrolled in
* View the Chapters and Lessons of a given Subject
* Open a Lesson and begin studying the content (video, text, image, or quiz). Usually, opening a Lesson means you're beginning to browser through the Widgets of the Lesson, where each Widget is displayed on a single screen
* Exit a Lesson halfway and return to it later, with the progress being saved and displayed in the UI on the home screen
  * The progress of a Lesson is determined by the percentage of Widgets that have been completed inside that Lesson
  * There is no need to persist progress to the backend. However, progress MUST be persisted in the device such that it's not lost when the app is closed and opened again
* Take a quiz and get feedback about whether the answer is correct or not

### Non-functional Requirements
* Your code should be written in React Native, using solid principles of software engineering and a robust state management framework
  * You must follow the best practices of React Native in your codebase
* You must use a shared/central state (implemented by a framework like Redux, Mobx, Zustand, etc) 
  * Your app cannot only rely on the use of `useState` or `useContext`. This may seem unnecessary for a small application like this, but it's important to demonstrate your ability to work with state management frameworks.
  * The state management should be designed in a way that allows the app to expand and grow to include more complex features, without becoming laggy or buggy
* Your work should be developed in a similar fashion to the industry standards and lifecycle of software development. You shouldn't just have a single commit with all the code in it. Your commits should be made just like you would if you're building this in the real world, with commits having well-defined boundaries and scope, meaningful commit messages, and so on
  * We will not have a code review process like the real world, but imagine that each commit should be like a PR that one of your colleagues would have reviewed if you were working in the real world

### Non-requirements
Things you don't need to worry about in this task:
* User session management (i.e. login, log out, sign up)
* Persisting anything to the backend (treat the backend as read-only)

### Bonus
Other (optional) things you can do:
* Show off your UI skills by building beautiful interfaces
* Create animations
* Add support for internationalization
* Anything else you'd like to show off
  * This is an opportunity to show your strengths, so if there is a feature or a functionality you want to build to demonstrate your skills, please do so.

### UI/UX Requirements
Below are some mocks and sample screenshots to help you visualize the UI. Feel free to change things up and use your own styles and UI if you have a different taste; this is only a sample.

If you're low on time, do not worry too much about making the UI super beautiful. It's more important that the requested features are built well instead of focusing on just UI and looks of the app. Only show off your UI skills after you have completed the basic requirements and functionalities of the app.

<table>
  <tbody>
    <tr>
      <td>
        <img src="https://i.imgur.com/hS7zESD.png" width="250">
        <br />
        List of Lessons within a Chapter
      </td>
      <td>
        <img src="https://i.imgur.com/KOZ1jOa.png" width="250">
        <br />
        Lesson list with partial progress
      </td>
      <td>
        <img src="https://i.imgur.com/JO3g28t.png" width="250">
        <br />
        Lesson with image and text Widget
      </td>
    </tr>
    <tr>
      <td>
        <img src="https://i.imgur.com/9UJdMwd.png" width="250">
        <br />
        Multiple choice question quiz
      </td>
      <td>
        <img src="https://i.imgur.com/eNJkrPe.png" width="250">
        <br />
        Quiz screen with a selected answer
      </td>
      <td>
        <img src="https://i.imgur.com/LVLGSKY.png" width="250">
        <br />
        Wrong answer
      </td>
    </tr>
  </tbody>
</table>

### APIs
In order to complete this task, you can use the following hardcoded values when communicating with the backend:
```
userId: 65edc62cc1aa0078000f9c01
gradeId: 6625514923f87505231c8f89
token: eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJfaWQiOiI2NWVkYzYyY2MxYWEwMDc4MDAwZjljMDEiLCJpYXQiOjE3MTM3MzQxOTh9.2ZIPdqfGIEbm0t6iSE14HTQw1ASehe_hijG_iEnWFJU
```

You will also need the following API endpoints to fetch the data (please do not hardcode API responses in the code, but make sure you're actually fetching the data dynamically inside the app):

#### /courseregistration/${userId}/${gradeId}
<details>
<summary>Returns the list of Subjects for a given Grade.</summary>

```
> curl https://lessonapi.educationforalliraqis.com/courseregistration/65edc62cc1aa0078000f9c01/6625514923f87505231c8f89 -H "Authorization: Bearer $token"

{
  "data": [
    {
      "_id": "6625599323f87505231c960c",
      "subject": {
        "_id": "6625599323f87505231c960c",
        "subject_price": 1000,
        "isActive": true,
        "Subject_name": "Math",
        "subject_icon": "https://corrsy-image-bucket.s3.me-south-1.amazonaws.com/MicrosoftTeams-image%20%284%29-1640072810081.png",
        "grade": "6625514923f87505231c8f89",
        "uniCode": "Math",
        "createdAt": "2024-04-21T18:23:15.652Z",
        "updatedAt": "2024-04-21T18:23:15.652Z",
        "__v": 0
      },
      "registeredCourseID": "66255a257fcbf291ce661e57",
      "grade": "6625514923f87505231c8f89",
      "isPurchase": false
    },
    {
      "_id": "662551e523f87505231c9000",
      "subject": {
        "_id": "662551e523f87505231c9000",
        "subject_price": 1000,
        "isActive": true,
        "Subject_name": "English",
        "subject_icon": "https://corrsy-image-bucket.s3.me-south-1.amazonaws.com/MicrosoftTeams-image%20%284%29-1640072810081.png",
        "grade": "6625514923f87505231c8f89",
        "uniCode": "ENG",
        "createdAt": "2024-04-21T17:50:29.582Z",
        "updatedAt": "2024-04-21T17:50:29.582Z",
        "__v": 0
      },
      "registeredCourseID": "662557b67fcbf291ce661e46",
      "grade": "6625514923f87505231c8f89",
      "isPurchase": false
    }
  ],
  "message": "Record found"
}
```
</details>

#### /lessons/subject/${subjectId}
<details>
  <summary>Returns the list of Chapters for a given Subject.</summary>

```
> curl https://lessonapi.educationforalliraqis.com/lessons/subject/662551e523f87505231c9000/ -H "Authorization: Bearer $token"

{
  "totalChapter": 1,
  "data": [
    {
      "_id": {
        "_id": "662551ff23f87505231c9036",
        "isActive": true,
        "price": 7000,
        "chapter_name": "Pronouns",
        "chapter_icon": "https://corrsy-image-bucket.s3.me-south-1.amazonaws.com/math-1-1660209535120.png",
        "chapter_number": 1
      },
      "chapter": [
        {
          "chapterID": "662551ff23f87505231c9036",
          "chapter_name": "Pronouns",
          "chapter_icon": "https://corrsy-image-bucket.s3.me-south-1.amazonaws.com/math-1-1660209535120.png",
          "isActive": true,
          "chapter_number": 1,
          "price": 7000,
          "isHidden": false
        }
      ],
      "lessons": [
        {
          "_id": "662552c241ce1ef8be9a0fa1",
          "title": "He, she, it",
          "subject": "662551e523f87505231c9000",
          "grade": "6625514923f87505231c8f89",
          "level": "intermediate",
          "shortDescription": "The meaning of he, she, it",
          "longDescription": "Why do pronouns matter?",
          "realLifeScenario": "Talking to people",
          "isActive": true,
          "lessonIcon": "https://corrsy-image-bucket.s3.me-south-1.amazonaws.com/math-1-1660209535120.png",
          "isPaid": false,
          "price": 2000,
          "lessonNumber": 1
        },
      ]
    }
  ],
  "length": 1,
  "message": "Lessons record found"
}
```
</details>

#### /lessons?\_id=${lessonId}
<details>
  <summary>Returns the details of a given Lesson, including a list of all its Widgets.</summary>

  ```
> curl https://lessonapi.educationforalliraqis.com/lessons?_id=6625580e41ce1ef8be9a1e3c -H "Authorization: Bearer $token"

  {
    "data": [
      {
        "_id": "6625580e41ce1ef8be9a1e3c",
        "title": "Summary",
        "shortDescription": "Summary",
        "longDescription": "Summary",
        "realLifeScenario": "Summary",
        "lessonIcon": "",
        "level": "beginner",
        "grade": "6625514923f87505231c8f89",
        "subject": "662551e523f87505231c9000",
        "chapter": "662551ff23f87505231c9036",
        "isActive": true,
        "widgets": [
          {
            "widgetType": "video",
            "videoWidgetContent": {
              "title": "Summary",
              "videoType": "youtube",
              "videoUrl": "https://www.youtube.com/watch?v=h_GnSOIfWf4",
              "transcript": "https://assets.corrsy.com/Untitled%20document-1694715519687-1713723501156.pdf",
              "voiceOverUrl": "",
              "introduction": "Summary",
              "exercise": "Summary",
              "example": "Summary",
              "summary": "Summary",
              "theory": "Summary",
              "whatNext": "Summary",
              "application": "Summary",
              "questions": []
            },
            "isActive": true,
            "_id": "662558b241ce1ef8be9a1f34"
          }
        ],
        "isPaid": false,
        "price": 2000,
        "lessonNumber": 4,
        "createdAt": "2024-04-21T18:16:46.483Z",
        "updatedAt": "2024-04-21T18:19:30.541Z",
        "__v": 0
      }
    ],
    "message": "Lessons record found"
  }
```
</details>

## Submission Instructions
Upload your work to a public Github repo. Your repo should have a `README.md` file that includes the following:
* Instructions on how to run the app from scratch
* Screenshots of the views you created. Video demo is a bonus
* Any assumptions you made to be able to complete this task
* A summary of the technical choices you made in building the app and an explanation for why you did them
* Future plans or things you would do differently or add if you had more time
* Any stretch goals or bonus features you attempted
* Any shortcuts you took or compromises you made
* The total amount of time spent on this assessment
* Any resources, tools, frameworks, technologies you utilized in your solution
* Anything else you'd like to share with us

Commit your code to a public repo and provide the link using this form:
https://airtable.com/app3mLcaYNihmV5D0/pagDKGekHT7Lm5Wn3/form

Please submit all your work by **Monday, Apr 29th at 8am UTC**.

## Evaluation Criteria
The purpose of this assessment is to simulate the real world as much as possible. That's why we are trying to only ask for things that are relevant in the real-world implementation of the applications and services we are building.

Overall, we will look for the following things to assess submissions:
* Code quality and cleanliness
* Utilization of good software design principles
* Completeness of features/requirements
* Incremental changes and meaningful commit history
* Quality of requested documentation (via README.md file)
* Stretch goals or bonus features attempted

## Final thoughts
This task includes some intentionally ambiguous components that are not very explicitly outlined. For those, we are leaving it up to you to decide any missing details. Please use your own judgement, and document any assumptions you made in your README.md. Problems in the real world are full of uncertainties and ambiguities, and we are trying to make this assessment as close to the real world as possible.

In order to be fair and have a consistent process, we ask that you find answers to your questions, or make up the answer yourself instead of asking us. If you do so, please document that as well.

There are many opportunities to take this assessment in multiple directions that are open-ended. Feel free to do so and put your own personal touch to the solution you develop.

It might also seem like this assessment is asking for too much. You can treat the requirements as a superset or a master list of all the requirements the application needs, and if you are only able to achieve some of them, use your own judgement to decide what to prioritize and include in an MVP. We don't want you to spend too much time on this, so whatever you can fit in **a single complete working day** is what we ask you to give for this exercise.