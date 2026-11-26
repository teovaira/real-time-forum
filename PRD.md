# Product requirements: real-time-forum

A forum delivered as a single-page application, with private messages in real time.

## Constraints

- Backend in Go, data in SQLite, frontend in JavaScript, HTML and CSS.
- Exactly one HTML file; every page change happens in JavaScript.
- Go dependencies: the standard library, Gorilla websocket, sqlite3, bcrypt, and
  gofrs/uuid or google/uuid.
- No frontend libraries or frameworks.

## Registration

**Behavior:** a visitor fills a register form with nickname, age, gender, first name,
last name, e-mail and password.

**Acceptance criteria:**

- The form asks for all seven fields.
- A visitor who is not logged in sees only the registration or login page.

## Login and logout

**Behavior:** a user logs in with the nickname or the e-mail, combined with the password,
and can log out from any page.

**Acceptance criteria:**

- Both nickname and e-mail work as the login name.
- A registered user can log in.
- Logout is available on every page.

**Edge cases:** an unregistered user cannot get in.

## Posts

**Behavior:** a logged-in user creates posts with categories, as in the first forum, and
sees posts in a feed.

**Acceptance criteria:**

- A user can create a post.
- The post is visible again on a later login.

## Comments

**Behavior:** a logged-in user comments on a post.

**Acceptance criteria:**

- Comments are shown only after clicking on the post.
- A user can see the comment they created.

## Online and offline users

**Behavior:** a section shows who is online and offline and able to talk.

**Acceptance criteria:**

- The section is visible at all times.
- Users are ordered by the last message sent.

**Edge cases:** users with no messages are ordered alphabetically, for example for a
newly registered user.

## Private messages

**Behavior:** a user can send private messages to users who are online. Clicking a user
opens the conversation with its past messages.

**Acceptance criteria:**

- Each message shows the sender's user name and the date it was sent.
- The recipient receives the message and a notification without refreshing the page,
  over WebSockets.

## Message history

**Behavior:** opening a conversation loads the last 10 messages; scrolling up loads
10 more.

**Acceptance criteria:**

- Only the last 10 messages are shown at first.
- Loading more is driven by the scroll event and does not spam it (throttle or debounce).

**Edge cases:** conversations with more than 10 and more than 20 messages.

## Optional (bonus)

- User profiles.
- Images in private messages.
- Fast, with no unnecessary data requests.
- Good code practices.
- Promises, goroutines and channels used to improve performance.
