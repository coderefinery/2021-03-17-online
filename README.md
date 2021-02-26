# CodeRefinery software testing hackathon

### List of important links
- [Preparation meeting note](https://hackmd.io/n365TXt7QIOfBHBvOqfgjg?view)
- [Lesson materials](https://coderefinery.github.io/testing/)
- [Lesson repository at CR](https://github.com/coderefinery/testing)
- [Lesson repository at ENCCS](https://github.com/ENCCS/testing)
- [Indico event management page (CR-only)](https://indico.neic.no/event/179/manage/)

### Schedule planning

Hackathon roles and self-assignment:

- **Host:** Manage zoom meeting, breakout rooms, timekeeping and breaks,
   zoom chat, general attendee communication.
   - Name1
- **Hackmd:** watches hackmd, answers questions, organizes it, brings questions up in main lecture.
   - Samantha
   - Name3
- **Mentors:** get paired with a few participants on day 1 and answer questions by email in the period until day 2.
   Also work as helpers in breakout rooms on day 1.
   - Anne Fouilloux
   - Diana Iusan
   - Emilia Lipponen
   - Johan Hellsvik
   - Mark Abraham
   - Qiang Li
   - Radovan Bast
   - Roberto Di Remigio
   - Thor Wikfeldt

- **Instructors:** Teach the lesson on day 1

| Time  | Duration | Episode                               | Instructor  |
| ----- | -------- | ------------------------------------- | ----------- |
| 9:15  | 10 min   | Motivation                            | Naoe & Thor |
| 9:25  | 10 min   | Concepts                              | Naoe & Thor |
| 9:35  | 25 min   | Testing locally                       | Diana       |
| 10:00 | 10 min   | Break                                 |             |
| 10:20 | 0        | Tools                                 | moved to last as reference |
| 10:10 | 40 min   | Automatic testing with GitHub Actions | Roberto?    |
| 10:10 | 40 min   | Automatic testing with GitLab CI      | Mark        |
| 10:50 | 10 min   |  Break                                |             |
| 11:00 | 55 min   | Test design                           | Johan+Radovan          |
| 11:55 | 5 min    | Conclusions and recommendations       | TBD         |


### Changing the status of the registration button

Registration is not yet open:
```html
<a class="btn btn-info disabled" href="#" data-mode="1" target="_blank">Registration will open soon</a>
```

Registration is open (adjust the `href`):
```html
<a class="btn btn-success" href="#" data-mode="1" target="_blank">Register here</a>
```

Registration is closed:
```html
<a class="btn btn-danger disabled" href="#" data-mode="1" target="_blank">Registration is closed</a>
```
