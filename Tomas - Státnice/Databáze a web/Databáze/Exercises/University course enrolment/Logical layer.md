---
tags:
  - databaze
  - databaze_a_web
dg-publish: true
---
Person(***personId,*** email, phoneNumber, name, DOB)
Instructor(***instructorNumber***) instructorNumber $\subseteq$  Person.personId
Student(***studentNumber***) studentNumber $\subseteq$  Person.personId

Course(***courseNumber***, name)

Enrolment(***enrolmentId***, ***studentNumber***, ***courseNumber***, grade) studentNumber $\subseteq$  Student.studentNumber, courseNumber $\subseteq$ Course.courseNumber

Teaches(***instructorNumber***, ***courseNumber***) instructorNumber $\subseteq$ Instructor.instructorNumber, courseNumber $\subseteq$ Course.courseNumber