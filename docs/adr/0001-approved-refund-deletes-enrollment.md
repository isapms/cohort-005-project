# Approving a Refund Request deletes the enrollment, but keeps progress

When an Admin approves a Refund Request, we delete the learner's enrollment in that course, rather than marking it as ended. Access across the app already means "an enrollment exists", and around 18 places read enrollments directly. A "revoked" flag would need every one of them to filter it, and a missed one would leak access or inflate counts. The history isn't lost: the purchase and the Approved Refund Request still record that the learner had the course and gave it back.

## Consequences

- Lesson progress, watch history and quiz attempts are deliberately **not** deleted. If the learner buys the course again, their progress reappears.
- Because watch history survives, the refund limits (2 hours watched, 50% of lessons completed) count across every purchase of the course. A learner cannot reset them by buying again.
- The original enrolled date is lost when the enrollment is deleted. The purchase date is the record of when they first had the course.
