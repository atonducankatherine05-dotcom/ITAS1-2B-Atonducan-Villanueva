q# ITAS1-2B-Villanueva-Atonducan
Study Circle LAN Chat - Shared question queue and live group poll for classmates reviewing a subject.

## Members
- Katherine Atonducan
- Timothy Villanueva
- Section: ITAS1-2B

## Concept Proposal
Study Circle is for classmates reviewing a subject together on the same LAN / WiFi without internet.

Problem: In a group review, questions get buried in chat and the group cannot decide what topic to review next.

Solution: A LAN chat app with 2 distinct features:
1. Shared Question Queue - questions are saved in order, not lost in chat.
2. Group Poll with Live Results - the group votes for the next topic and sees results instantly.

This is not a tutorial chat. It is built for study groups, with commands for asking, answering, and voting.

## Distinct Features

### 1. Shared Question Queue
- `/ask <question>` - Add a question to the queue. Example: `/ask What is the formula for subnetting?`
- `/queue` - Show all unanswered questions with numbers.
- `/done <number>` - Mark a question as answered. Example: `/done 1`
- `/answer <number> <answer>` - Answer a question and remove it from queue.

Everyone sees the same queue in real time.

### 2. Group Poll with Live Results
- `/poll <question> | Option A | Option B | Option C` - Start a poll. Example: `/poll Which topic to review? | TCP | UDP | IP Addressing`
- `/vote <number>` - Vote for an option. Example: `/vote 1`
- `/result` - Show live vote counts.
- `/endpoll` - End the poll and show the winner.

Votes update for all connected clients immediately.

### 3. Normal LAN Chat
- Normal messages work as regular chat.
- Nickname, join / leave messages, and disconnect support.

## Architecture
- Language: Java Swing + Sockets (TCP)
- Server: `ChatServer.java` - accepts multiple clients, holds question queue and current poll, broadcasts queue / poll updates to all clients.
- Client: `ChatClient.java` - GUI with IP, Port, Nickname, Chat area, Message box. Default IP: `127.0.0.1`, Port: `5000`.
- Protocol: Plain text over Socket. Commands start with `/`. Server parses commands and broadcasts formatted messages to all clients.

## How to Run
1. Open project in NetBeans / IntelliJ.
2. Run `ChatServer` first.
3. Run `ChatClient` - open 2 or more clients to test.
4. In each Client: Set IP `127.0.0.1`, Port `5000`, Nickname `Katherine` / `Timothy`, click Connect.
5. Try in chat:
