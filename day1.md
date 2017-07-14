# Wednesday (Day 1)

## Talking People Down from Shiny (Tod Hansmann)

* "shiny" being flavor of the month tech. A single person or small group
  advocating for "their thing", sold as something more friendly or intuitive,
  happier, better, faster, stronger, etc.

* praticality is an issue for shiny. "everyone else is using it so we should
  too"

* shiny is not always badr, but it hasn't been functionally tested enough to be
  usable in production (ex: you wouldn't put a new linux kernel in prod an hour
  after it is released).

* How to argue with shiny without being antagonistic or "that guy" in the
  workplace:
    - Start from their perspective
    - Ask about the long term
    - Ask why they're sure it will work the way they think it will work.
    - Who eats tech debt the new thing inevitably creates?
    - Are they advocating for the project, or themselves?

* Scenarios:
    - If this is an intern, be a mentor.
    - If this is management, play hardball.
    - If this is a colleague, this is discussion time!
    - If this is the internet, ignore it.

* Learn how to do the clever things and know when to use them, but clever does
  not always work.

* Win or lose gracefully:
    - The porject can still be good if you lose.
    - You still have to work with these people, even if you quit.
    - Reputation is important, professionalism is how you earn that.
    - It is, after all, just tech.
    - Leadership accepts compromise when and where it can, and carries the
      wounded forward to joint victory.

## Building a Wrapper API: The Case for Abstraction (Aaron Mildenstein)

* For some given API actions, it takes a too many (5+) API calls to get the
  job done.

* Makes low level APIs more accessible. Essentially a high level API on top of
  a low level one (extension). Might want to catch exceptions and handle them
  differently as well.

* Plan it out:
    - build on pre-existing low level API/modules/classes
    - what behaviors are needed?
    - What does the final result need to be?
    - How do I test it (unit and/or integration).

* Speaker wrote ElasticSearch Curator.

* Explaining unit vs. integration tests and how CI works. Pretty rudimentary
  overview of TDD (not incredibly useful for me).

* You should publish docs for your API wrapper (review). Use something that will
  translate comments to docs automagically (review).

* Use readthedocs (review).

* Push to pypi (review).

**note**: `review` in the above usage just means `I've already done this, but
it's good to be teaching people about it and it is certainly important`.

## Deploying a Baremetal Cloud is not Easy (Julia Kreger)

* A baremetal cloud is not traditional IT, process and workflows are inherently
  different.
