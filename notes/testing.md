# Testing
- https://martinfowler.com/articles/practical-test-pyramid.html
- https://docs.gitlab.com/ee/development/testing_guide/
- https://madeintandem.com/blog/five-factor-testing/
- https://www.lihaoyi.com/post/PrinciplesofAutomatedTesting.html
- https://alisterbscott.com/kb/testing-pyramids/
- Small, medium, large tests https://testing.googleblog.com/2010/12/test-sizes.html
- Ian Cooper - TDD, Where did it all go wrong? https://youtu.be/EZ05e7EMOLM

Common terminology for testing pyramid layers is:
* End to end tests
* Integration tests
* Unit tests

Key points:
- Test behaviour, not implementations.
    - Test on implementations are hard to maintain.
- Avoid anti-pattern: ice-cream cone testing.
- Write dirty code to get green, then refactor (red, green, refactor).
- Don't write new tests when refactoring internals/privates.
- Arrange, Act, Assert https://xp123.com/articles/3a-arrange-act-assert/
- Given, When, Then https://martinfowler.com/bliki/GivenWhenThen.html
