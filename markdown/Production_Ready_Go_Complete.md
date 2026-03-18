# Production-Ready Go  
## Patterns and Practices for Shipping Reliable Software


<b>Author:</b> Sean R. Merriam<br>
<b>Edition:</b> First Edition<br>
<b>Publication Year:</b> 2026<br>
<b>Language:</b> English<br>
<b>Format:</b> PDF<br>









### Copyright
#### © 2026 Sean R. Merriam <br> 

All rights reserved.


No part of this publication may be reproduced, stored in a retrieval system, or transmitted in any form or by any means—electronic, mechanical, photocopying, recording, or otherwise—without the prior written permission of the author, except for brief quotations in reviews.



#### Disclaimer

The information in this book is provided “as is,” without warranty of any kind. While the author has made every effort to ensure accuracy, the techniques and practices described may not be suitable for all systems or environments. Software development involves trade-offs. The author assumes no responsibility for errors, omissions, or for damages resulting from the use of the information contained herein.
<br>
<br>
If you find any errors in this book, please <a href="sean@cssit.co">email me</a>.

</div>






# Introduction: Building Software That Lasts


Most software does not fail because developers are careless. It fails because teams ship under pressure without enough guardrails for correctness, security, performance, and change. A feature works in local development, then breaks under real traffic. An endpoint passes happy-path tests, then fails on malformed inputs. A deployment succeeds technically, then degrades user experience because observability and rollback were treated as afterthoughts.

This book is about closing that gap between code that works once and software that keeps working over time.

Production-ready software development is not about perfection. It is about repeatable engineering discipline: test-first design, explicit error handling, secure defaults, clear architecture boundaries, and operational feedback loops that catch problems early. These practices do not eliminate risk, but they turn risk into something visible and manageable.

By the end of this book, you should not only know how to write correct code. You should know how to ship and operate software confidently in environments where failures are expensive and trust is hard to rebuild.

  

## Why Production Readiness Matters

Every production bug has a cost beyond the defect itself. There is the immediate fix, but also context switching, emergency coordination, deployment risk, regression risk, and user impact. If incidents repeat, teams lose delivery momentum and users lose trust.

The same pattern appears in security, reliability, and maintainability:

- Security issues are rarely one-line mistakes. They are usually the result of missing validation, inconsistent policy enforcement, and insufficient defense-in-depth.
- Reliability issues are rarely caused by one component alone. They emerge from interactions across API design, database behavior, concurrency, and deployment conditions.
- Maintainability issues are rarely visible in week one. They accumulate as architecture boundaries blur and every change touches too many layers.

Production readiness is how you prevent these failure modes from becoming normal. It is not a final checklist. It is a development approach that influences every decision, from function signatures to release strategy.



## The Core Philosophy: Test First, Think in Systems

The throughline of this book is simple: treat testing as design, not cleanup.

When you write tests first, you define expected behavior before implementation details. This forces clearer interfaces, better naming, and more realistic edge-case thinking. The Red-Green-Refactor cycle keeps development incremental and grounded in evidence instead of intuition.

But testing alone is not enough. Production software is a system, not a set of isolated functions. You must reason about how components interact under stress, failure, and change:

- input validation and security controls at API boundaries
- data integrity and transaction correctness in persistence layers
- error propagation and logging consistency across service layers
- concurrency safety and cancellation behavior in asynchronous work
- deployment, monitoring, and rollback in real environments

This is why the book combines coding practices with architecture and operations. Reliable software emerges from aligned decisions across the whole lifecycle.



## Why Go Is the Right Language for This Journey

Go is especially well-suited for learning and applying production engineering discipline.

Its design encourages explicitness:

- errors are returned and handled directly
- package boundaries are clear and enforceable
- the standard testing tools are built in and easy to adopt
- concurrency primitives are powerful but explicit enough to reason about

Go does not hide complexity behind heavy framework conventions. That makes it easier to understand how systems actually behave in production. You can trace control flow, inspect dependencies, and test behavior without fighting abstraction layers that obscure important details.

In short, Go is a practical language for building software that must be understandable, maintainable, and reliable under real-world conditions.



## The Capstone CMS You Will Build

This book is structured around a complete content management system (CMS) implementation. The CMS is not a toy project and not just a collection of disconnected examples. It is a cohesive application used to apply the patterns from each chapter in context.

You will build and harden features such as:

- user registration, authentication, and authorization
- post creation, editing, publishing, and archival workflows
- category and tag taxonomy management
- REST API contracts with middleware and error standards
- a React + TypeScript frontend that consumes backend contracts safely
- deployment, monitoring, and maintenance workflows for production operation

A CMS is an effective teaching vehicle because it combines common real-world concerns in one system: identity, security, persistence, API design, frontend state, performance, and operations.

Throughout the book, the intent is to show not just how to make features work, but how to make them safe to change and safe to run.



## How the Book Is Organized

The content is organized as a progression from foundations to full production operation.

**Part One: Testing and Reliability Foundations (Chapter 0 + Chapters 1-4)**

You begin with a testing primer in Chapter 0, then move into the test-everything mindset, practical Go testing skills, advanced test strategies, and security-first development habits. This part establishes the engineering posture used in every later chapter.

**Part Two: Backend Foundations (Chapters 5-9)**

You build backend reliability through data-layer design, HTTP/API patterns, error handling, logging, concurrency, and project structure. By the end of this part, you have the architectural and operational foundations required for full application development.

**Part Three: CMS Implementation (Chapters 10-14)**

You implement the CMS in full: architecture setup, user management and authentication, content workflows, API layer and middleware, and frontend integration using a framework-agnostic baseline plus an optional React + TypeScript reference track.

**Part Four: Production Operation (Chapter 15)**

You complete the journey with deployment strategy, CI/CD, observability, incident response, and ongoing maintenance planning.

Each chapter includes objectives, practical implementation guidance, verification patterns, and exercises to reinforce applied understanding.

## Companion Repository and Chapter Tags

To get full value from this book, use a companion code repository that mirrors chapter progression. The repository should expose stable checkpoints so you can inspect a known-good state for each chapter, compare your work to the reference state, and recover quickly if your local branch drifts.

Use chapter tags rather than one long mutable branch. Tag names should be predictable and sequential so you can jump across the learning path without ambiguity.

Recommended tag naming convention:

- `ch00-testing-primer`
- `ch01-test-everything-mindset`
- `ch02-go-reliability-patterns`
- ...continue one tag per chapter through `ch15-production-operations`

Recommended workflow:

- start each chapter from the previous chapter tag
- implement exercises and examples on your own branch
- compare against the next chapter tag only after finishing your attempt
- keep personal notes in commit messages so your reasoning history remains searchable

This workflow keeps learning active and makes revision easier. It also models real production work where change history, reproducibility, and rollback points are part of engineering quality.

## Reading Paths

This book supports multiple learning tracks depending on your current goals. You do not need to read every chapter at the same speed.

Core Backend Path:

- Chapter 0, then Chapters 1-13, then Chapter 15
- Use this path if your primary goal is reliable Go backend development

Full-Stack Path:

- Chapter 0, Chapters 1-13, Chapter 14 mainline, Appendix I (optional depth), then Chapter 15
- Use this path if you need backend reliability plus frontend integration patterns

Operations Path:

- Chapter 0, Chapters 1, 5, 7, 8, 9, 10, 13, and 15
- Use this path if you are focused on deployment safety, observability, and long-term service operation

If you are newer to Go, follow the Core Backend Path first and return to optional tracks on a second pass. This keeps cognitive load manageable while preserving the book's reliability-first throughline.



## How to Use This Book for Maximum Value

Treat this as a hands-on engineering guide, not passive reading.

Recommended approach:

- run the code and tests as you go instead of only reading snippets
- pause at design decisions and predict failure modes before reading the solution
- complete exercises, especially the ones that target error paths and operational scenarios
- keep notes on patterns you want to apply immediately in your own projects
- revisit summary and best-practice sections when designing new features

You will get the most value by practicing the discipline repeatedly, not by rushing to the end.

## Reliability Throughline Across the Book

This book is intentionally cumulative. Part One establishes verification discipline, Part Two turns that discipline into backend design habits, Part Three applies both to end-to-end product delivery, and Part Four operationalizes the system for real production environments.

Each major chapter should be read as both a local implementation guide and a reliability pattern that carries forward. For example, error modeling from Chapter 7 should directly shape API contracts in Chapter 13 and observability practices in Chapter 15, while data and state modeling choices in Chapters 5 and 12 should influence incident response and rollback confidence later.

If you apply chapters in this sequence, you are not just learning features; you are building a durable engineering system. The goal is that after finishing the book, you can repeatedly design software that is testable, diagnosable, secure by default, and safe to evolve over multi-year lifecycles.



## Prerequisites and Environment Expectations

You do not need prior expert-level Go experience, but you should be comfortable with basic programming concepts such as functions, data structures, control flow, and HTTP fundamentals.

This is not a complete-beginner programming book. If you are brand new to software development or still learning core concepts like functions, loops, and basic data structures, this text will likely feel too fast.

You should ideally have at least one of the following before starting:

- prior experience in another language (for example Python, Java, JavaScript, C#, or Rust)
- familiarity with command-line workflows, package management, and running automated tests
- basic understanding of API requests/responses and relational database concepts

You should be ready to work with a typical modern development setup:

- Go (recent stable version)
- PostgreSQL
- Docker
- Node.js (for the optional React frontend reference track)
- Git and a CI platform workflow mindset

If some tools are new, that is fine. The book focuses on practical use in context rather than tool theory.

If you are newer to Go itself, use Chapter 0 as a required on-ramp before Chapter 1.

All code in this book has been tested with Go 1.24 and later. Go maintains strong backward compatibility, so the patterns in this manuscript should continue to work on newer Go releases. If you see version-specific behavior in a newer release, check the companion repository for updated examples.



## Who This Book Is For

This book is written for developers who want to move from “I can build features” to “I can ship and run reliable systems.”

It is best suited for early-career to senior developers who already know at least one programming language and want to adopt production-grade Go practices. It is intentionally opinionated and operationally focused rather than introductory language training.

It is especially useful for:

- backend or full-stack developers who want stronger production engineering habits
- Go developers who want to deepen testing, architecture, and operational rigor
- engineers transitioning from framework-heavy stacks who want explicit system control
- team leads and senior engineers establishing quality and reliability standards

If you have ever fixed a production bug and thought “we should have caught this earlier,” this book is for you.



## What You Should Leave With

By the time you finish, you should be able to:

- design testable components and verify behavior before implementation drift occurs
- build secure API boundaries and enforce authorization policies consistently
- implement backend and frontend layers that evolve without fragile coupling
- release changes through controlled pipelines with measurable risk
- operate services with clear observability, incident response, and maintenance workflows

Most importantly, you should leave with a repeatable way of thinking about software quality: not as a final phase, but as a continuous engineering responsibility from first commit to long-term operation.

Turn to Chapter 0 first, then begin Chapter 1 with that foundation in place.



# Chapter 0: Testing Primer for Go Learners

## Learning Objectives

- Understand what software testing is and what it is not
- Distinguish unit, integration, end-to-end, fuzz, and benchmark testing
- Evaluate strengths and weaknesses of each test type
- Understand why this book uses a test-first development style
- Learn a practical workflow for studying Go and testing together
- Avoid cargo-cult testing by tying each pattern to a concrete purpose

## Introduction: Why This Chapter Exists

Several readers correctly identified a real learning challenge: this book teaches production-grade Go practices, and those practices assume some prior engineering maturity. If someone is learning both Go and modern testing discipline at the same time, cognitive load rises quickly.

This chapter exists to reduce that load. Before writing table-driven tests, mocks, fuzz cases, and benchmark suites, you should have a clear mental model of what testing is for, what kinds of tests exist, and what each style can and cannot tell you.

The goal is not to turn testing into theory. The goal is to give you a map so later chapters feel intentional rather than overwhelming. When you understand why a technique is used, learning how to use it becomes significantly easier.

If you already have strong testing foundations, you can skim this chapter. If you are newer to testing, treat it as mandatory because it will make every subsequent chapter easier to absorb.



## Section 1: What Testing Actually Is

Testing is a method for reducing uncertainty in software behavior. It is not ceremony, and it is not a checkbox. Each test is a claim about behavior under specific conditions.

### Testing as Executable Specification

A good test specifies behavior in executable form. Instead of saying "this should return a validation error," the test sets up input, runs the function, and verifies the exact error behavior. That specification is living documentation because it is continuously re-verified by automation.

Executable specifications are valuable in long-lived systems because comments and wiki pages drift, while tests fail when behavior changes. This is one reason production teams trust test suites more than static documentation when assessing change risk.

When writing tests, the key question is: what contract am I specifying? If the contract is unclear, the test often becomes brittle. If the contract is clear, the test becomes a durable tool for design and maintenance.

### Testing as Risk Management

Testing is fundamentally risk management. You cannot test every possible execution path in a non-trivial system, so you choose where failure would be costly and verify those behaviors first.

For a CMS, high-risk areas include authentication, authorization, content-state transitions, and error handling boundaries. Bugs in these paths cause real user harm, security exposure, or operational incidents, so these areas deserve denser tests than low-risk display utilities.

Thinking in risk terms also prevents cargo-cult testing. Instead of asking "do I have enough tests," ask "which failures matter most and are currently unverified."

### Testing Is Not Proof of Perfection

A passing test suite does not mean software is perfect. It means behavior is verified for the scenarios your tests cover. Untested assumptions can still fail in production.

This limitation is healthy to acknowledge early because it shapes better engineering behavior. Teams that treat tests as evidence, not guarantees, combine testing with observability, staged rollouts, and incident-ready operations.

Your objective in this book is not to eliminate all defects. Your objective is to build systems that fail less often, fail more safely, and are easier to repair when failures occur.



## Section 2: Testing Types and Their Tradeoffs

Different test types answer different questions. Using one test type for every problem is inefficient and often misleading.

### Unit Tests

Unit tests verify small slices of behavior in isolation. They are usually the fastest tests to run and the easiest to debug when they fail.

Their strength is rapid feedback during development and refactoring. Their weakness is limited realism: external systems such as databases, networks, and runtime wiring are often mocked or absent.

Use unit tests heavily for domain logic, validation rules, and deterministic transformations where speed and precision matter.

### Integration Tests

Integration tests verify behavior across component boundaries, such as service-to-repository calls against a real database or HTTP handlers executing with real middleware stacks.

Their strength is confidence in wiring and runtime behavior that unit tests cannot provide. Their weakness is that they are slower and often more expensive to maintain.

Use integration tests for the contracts that matter most in production: persistence behavior, auth boundaries, and API envelope consistency.

### End-to-End Tests

End-to-end tests exercise complete user or system workflows through externally visible interfaces. They answer the question "does the system work as deployed from the user's perspective?"

Their strength is high realism. Their weakness is speed, flakiness risk, and longer diagnosis cycles because many layers are involved.

Use E2E tests sparingly for the most critical workflows, not as your primary testing layer.

### Fuzz and Property-Oriented Testing

Fuzz testing generates many inputs automatically to discover edge cases and crashes that humans may not think of. It is particularly useful for parsers, validators, and input-heavy code paths.

Its strength is breadth across unexpected inputs. Its weakness is that failures may require extra analysis to understand root cause and acceptable behavior boundaries.

Use fuzzing after deterministic tests establish expected behavior, not as a replacement for clear example-based test cases.

### Benchmark and Performance Testing

Benchmarks measure runtime and allocation behavior to detect regressions and validate performance assumptions. They answer "how fast" and "how costly" rather than "is it logically correct."

Their strength is objective performance data. Their weakness is potential misinterpretation when benchmark scenarios are unrealistic or unstable.

Use benchmarks for hot paths and capacity-sensitive operations, and track trends over time rather than reacting to one-off numbers.



## Section 3: Why This Book Uses a Test-First Style

This book uses test-first sequencing because it reinforces design clarity. Writing a test before implementation forces you to define expected behavior, edge cases, and failure semantics before code structure hardens.

### What Test-First Gives You

Test-first development surfaces API design issues earlier. If a function is hard to test, it is often hard to reason about, which is usually a sign the design can be improved.

It also improves learning quality. When you read a concept and immediately encode expected behavior in tests, you are actively modeling the idea instead of passively consuming examples.

In production contexts, this pattern reduces regression risk and increases refactor confidence, both of which are central themes throughout this book.

### When to Relax Strict Red-Green-Refactor

Strict cycle discipline is useful, but real engineering sometimes requires pragmatic ordering. For exploratory spikes, performance prototyping, or external integration discovery, you may write provisional code first and tests shortly after.

The important principle is not dogma. The principle is that behavior should be specified and verified early enough to guide implementation and protect future changes.

Throughout this book, you should treat test-first as the default and deliberate deviations as explicit exceptions.



## Section 4: How to Learn Go and Testing Together

If you are learning Go and testing simultaneously, use a two-pass workflow to reduce overload:

1. First pass: read and run the example as written to understand the mechanics.
2. Second pass: restate the behavior in your own words and modify one case.
3. Third pass: add one failure path test and explain why it matters.

This process prevents "copy and run" behavior and builds ownership of the pattern.

### Study Checkpoints Before Advancing

Before moving from one chapter to the next, verify three checkpoints:

- you can explain the core behavior in plain language
- you can modify one test case without breaking unrelated behavior
- you can identify at least one production failure the pattern would prevent

If any checkpoint fails, pause and reinforce before moving on. This pacing is faster long term than rushing forward with weak foundations.

### Getting Unstuck Without Cargo-Culting

When you feel lost, avoid adding more patterns immediately. Instead:

- simplify the example to the smallest working case
- remove abstractions until behavior is obvious
- reintroduce one abstraction at a time with a test proving its value

This method keeps learning causal: every abstraction must earn its place by improving correctness, clarity, or maintainability.

## Best Practices Summary

- Treat tests as executable contracts, not ritual
- Choose test type based on risk and feedback speed
- Use unit tests for fast precision and integration tests for runtime confidence
- Keep E2E scope narrow and high-value
- Use fuzzing to expand input coverage after deterministic tests
- Treat benchmark results as decision support, not vanity output
- Apply test-first by default, with explicit pragmatic exceptions
- Use a staged study workflow when learning language and testing together

## Exercises

### Exercise 0.1: Classify Test Scenarios by Type

Given five scenarios (password validation, login API, full publish workflow, JSON parser robustness, and post-list performance), assign each to primary and secondary test types. Explain your choice in one paragraph per scenario.

### Exercise 0.2: Convert Behavior Notes into Tests

Write three behavior statements for a simple function, then convert each statement into a test case. Include at least one failure-path assertion.

### Exercise 0.3: Build a Personal Study Loop

Create your own chapter-by-chapter learning loop with checkpoints you will use throughout this book. Keep it short enough to use consistently.

## Further Reading

- Go testing package docs: https://pkg.go.dev/testing
- Go blog on fuzzing: https://go.dev/blog/fuzz-beta
- Practical guide to test doubles and seams: https://martinfowler.com/articles/mocksArentStubs.html
- Google SRE testing and reliability mindset: https://sre.google/sre-book/testing-reliability/

## Chapter Summary

This chapter established the learning and reliability foundation for the rest of the book. You now have a practical model for what tests do, what they do not do, and how different test types complement each other.

You also have a concrete strategy for learning Go and testing together without losing conceptual ownership. That strategy should make later chapters feel challenging but navigable instead of overwhelming.

With this baseline in place, Chapter 1 can focus on the test-everything mindset and implementation discipline with far less ambiguity.



# Chapter 1: The Test-Everything Mindset

## Learning Objectives

- Understand the fundamental philosophy behind test-driven development and why it matters for producing reliable software
- Recognize the economic and quality benefits of comprehensive testing compared to debugging and hotfixes
- Set up a complete Go testing environment with industry-standard tools
- Write your first meaningful test in Go using the testing package
- Understand the Red-Green-Refactor cycle and how it guides software development
- Appreciate how testing first leads to better API design and more maintainable code



## Introduction: Why Testing Changes Everything

Software development has evolved dramatically over the past five decades, yet one truth remains constant: bugs in production systems cost far more to fix than bugs caught during development. The difference isn't just monetary—it's about customer trust, developer morale, and the ability to iterate quickly. When you ship code that breaks in production, you're not just fixing a defect; you're recovering from a crisis. Teams spend hours diagnosing issues in production logs, emergency deployments disrupt schedules, and the pressure of a live outage leads to more mistakes.

Test-driven development flips this equation entirely. By writing tests before you write implementation code, you create a safety net that catches problems immediately. The moment you introduce a regression, your tests fail. The moment your understanding of a requirement was incorrect, your tests fail. Tests become your living documentation, your API contract, and your confidence to refactor. They transform the question "does this work?" from a nervous gamble into a deterministic answer.

Consider the alternative: manual testing. Every time you modify code, you must manually verify that existing functionality still works. This becomes impossible at scale—complex systems have millions of possible execution paths, and human testers cannot exercise them all consistently. Even worse, manual testing is boring and error-prone. Developers rush through it, skip edge cases, and develop blind spots for the very areas they're most likely to break.

The test-everything mindset isn't about achieving perfection; it's about building confidence. When your test suite runs green, you know exactly what your code does and doesn't do. When you need to change behavior, you know precisely which tests to update. When a bug report comes in, you write a test that reproduces it, fix the code, and prevent regression. Testing becomes less about finding bugs and more about proving correctness.

Go was designed with testing as a first-class citizen. The language includes a comprehensive testing package in its standard library, making it trivial to write and run tests. Go's philosophy of simplicity and clarity extends to its testing approach: no complex frameworks required, no magic annotations, just straightforward code that verifies behavior. This book will teach you to leverage Go's testing capabilities to build software that works, stays working, and earns the trust of everyone who depends on it.

  

## Section 1: The True Cost of Bugs

Understanding the economics of software bugs provides the foundation for embracing test-driven development. When you truly internalize how expensive bugs are, testing becomes not just a good practice but an economic necessity.

### Direct Costs of Production Bugs

The most obvious cost is the time spent fixing defects. Studies consistently show that finding and fixing a bug in production takes 10 to 25 times longer than catching it during development. A bug that takes 30 minutes to identify and fix during initial development might consume an entire day when discovered in production—assuming you're lucky enough to catch it quickly. If the bug causes data corruption or security vulnerabilities, the remediation effort multiplies further.

Consider a realistic scenario: a middleware component in an e-commerce platform has a race condition that occasionally double-charges customers. The bug manifests once in every 10,000 transactions, making it nearly impossible to reproduce in testing. Customer support starts receiving complaints, the billing team investigates, engineers spend days analyzing logs, and eventually someone identifies the root cause. The fix itself might take 30 minutes, but the total cost includes hundreds of person-hours of investigation plus the reputational damage and customer churn.

Security vulnerabilities represent the extreme end of bug costs. A SQL injection flaw that allows data exfiltration might cost millions in regulatory fines, breach notification requirements, and loss of customer trust. The Equifax breach of 2017, caused by an unpatched known vulnerability, resulted in $575 million in settlement costs and incalculable damage to brand reputation. Even "minor" security issues can trigger expensive incident response procedures.

### Indirect Costs and Opportunity Costs

Beyond direct remediation costs, production bugs impose significant indirect costs. Every hour spent firefighting is an hour not spent building new features, improving architecture, or reducing technical debt. Teams that constantly fight production fires accumulate technical debt at alarming rates—they patch symptoms rather than addressing root causes, and they lose the cognitive bandwidth needed for thoughtful design.

The opportunity cost extends to developer experience. Nothing demoralizes a development team more than feeling like they're constantly putting out fires. When bugs keep reaching production, developers lose confidence in their code, second-guess their abilities, and become reluctant to make necessary changes. This defensive coding approach leads to more complexity, not less—the very opposite of what teams need to ship quickly.

Customer trust is perhaps the most valuable asset that bugs erode. Every production incident damages the relationship between your team and your users. They begin to question whether you can be trusted with their data, their business, their livelihoods. Rebuilding that trust requires sustained reliability over months or years, and some customers will never return.

### The Testing Investment

Writing comprehensive tests requires an upfront investment. Industry benchmarks suggest that well-tested code takes 30 to 50 percent longer to write initially. However, this investment pays dividends throughout the software lifecycle. Every bug caught by a test before it reaches production saves the enormous cost of production remediation. Every confident refactor enabled by a test suite accelerates the improvement of your codebase. Every new developer who reads passing tests to understand existing behavior reduces onboarding time.

The return on investment becomes particularly dramatic for long-lived systems. A feature that ships with tests will continue to be verified by those tests for years. Every subsequent developer who touches the code benefits from the safety net. The initial testing investment compounds—it's not just the original author who benefits, but everyone who ever works on that code.

Studies of software projects consistently find that the cost of finding and fixing defects increases exponentially as the defect moves later in the development lifecycle. Catching a bug at design time might cost 1 unit; catching it during coding costs 10 units; catching it in code review costs 20 units; catching it in manual testing costs 50 units; and catching it in production costs 100 units or more. Tests allow you to catch bugs as early as possible—ideally before the bug even exists, because you've defined the expected behavior in tests first.

  

## Section 2: The Go Testing Ecosystem

Go's creators understood that testing needed to be simple, fast, and built into the language itself. Rather than requiring external frameworks or complex configuration, Go includes comprehensive testing capabilities in its standard library. This design philosophy reflects Go's broader commitment to simplicity and developer productivity.

### The testing Package

Go's standard testing package gives teams a stable baseline that survives tool churn and framework preferences. Because it ships with the language, tests stay portable across environments and over time, which is exactly what long-shelf-life software needs.


At the heart of Go's testing ecosystem is the `testing` package, available automatically to every Go module. This package provides the fundamental building blocks: the `T` type for managing test state, the `B` type for benchmarks, the `testing.M` type for testMain functions, and the `testing.TB` interface that both share. Understanding these types is essential for writing effective tests.

The `testing.T` type manages individual test execution. It tracks whether the test is currently passing, provides methods for reporting failures, and offers control over test execution through methods like `Skip`, `SkipNow`, and `Parallel`. When a test fails, the testing framework captures the failure without immediately terminating the entire test suite—this allows other tests to run and report their status, giving you comprehensive feedback.

Go's testing philosophy emphasizes simplicity over magic. Unlike frameworks in other languages that require decorators, annotations, or special compilation modes, Go tests are just Go code in files ending with `_test.go`. The `go test` command automatically discovers and runs these tests. This approach means you can use all of Go's features in your tests: interfaces, goroutines, channels, reflection, and even testing itself.

### Running Tests Effectively

Test execution strategy determines feedback speed and developer behavior. Fast, targeted test runs encourage frequent verification during development, while slower broad runs remain valuable for release confidence; reliable teams use both intentionally.


The `go test` command provides extensive options for controlling test execution. The basic command runs all tests in the current package, but Go provides powerful options for more targeted testing. The `-run` flag accepts a regular expression to select specific tests; `-v` enables verbose output showing each test's name and result; `-cover` calculates and displays code coverage; and `-race` enables the race detector to find data races in concurrent code.

Understanding these flags is essential for effective testing workflows. During development, you'll frequently use `-v` to see exactly which tests are running and why. Before commits, you'll run with `-race` to catch concurrency issues. When refactoring, you'll use coverage reports to identify untested code paths.

### Test Organization and Conventions

Naming and structure conventions reduce cognitive load in large suites. When tests are predictable to navigate and interpret, review quality rises and regressions are diagnosed faster, which directly improves team throughput.


Go enforces clear conventions for test organization that promote consistency across projects. Test files must end with `_test.go` to be recognized by the test runner. Within test files, test functions must start with `Test` (capital T) and accept a `*testing.T` parameter. This convention allows the test runner to automatically discover tests without configuration.

```bash
# Run all tests in the current package
go test

# Run tests matching a pattern
go test -run "TestUser"

# Run with verbose output
go test -v -run "TestUser"

# Run with coverage
go test -cover -coverprofile=coverage.out

# Run with race detector
go test -race ./...

# Run benchmarks
go test -bench=. -benchmem

# Run fuzz tests
go test -fuzz=.
```

Tests in the same package have access to unexported functions and fields, enabling thorough unit testing. For black-box testing of public APIs, tests can reside in separate packages using the `package name_test` convention. Both approaches have merit: internal tests provide more thorough coverage, while external tests verify that APIs behave correctly from a user's perspective.

Go's table-driven testing pattern, which we'll explore in depth, provides an elegant way to organize multiple test cases. Rather than writing separate functions for each scenario, you define a slice of test cases and iterate over them. This approach reduces boilerplate, makes it easy to add new test cases, and clearly documents the various scenarios being verified.

### Example: Your First Go Test

First examples shape habits. If early tests model clear inputs, expected outcomes, and explicit failure messages, learners carry those practices into larger systems where clarity determines whether tests remain trusted documentation or become noise.


Let's write our first test to establish the pattern we'll use throughout this book. We'll create a simple function that adds two integers, then verify its behavior comprehensively.

  

```go
// internal/math/calculator_test.go
package math

import (
	"testing"
)

// TestAdd verifies the Add function with various inputs.
func TestAdd(t *testing.T) {
	tests := []struct {
		name     string
		a        int
		b        int
		expected int
	}{
		{
			name:     "positive numbers",
			a:        5,
			b:        3,
			expected: 8,
		},
		{
			name:     "negative numbers",
			a:        -5,
			b:        -3,
			expected: -8,
		},
		{
			name:     "mixed signs",
			a:        10,
			b:        -4,
			expected: 6,
		},
		{
			name:     "zero operands",
			a:        0,
			b:        0,
			expected: 0,
		},
		{
			name:     "large numbers",
			a:        1000000,
			b:        500000,
			expected: 1500000,
		},
	}

	for _, tt := range tests {
		t.Run(tt.name, func(t *testing.T) {
			result := Add(tt.a, tt.b)
			if result != tt.expected {
				t.Errorf("Add(%d, %d) = %d; want %d", tt.a, tt.b, result, tt.expected)
			}
		})
	}
}
```

Now let's implement the Add function to make these tests pass:

```go
// internal/math/calculator.go
package math

// Add returns the sum of two integers.
func Add(a, b int) int {
	return a + b
}
```

This simple example demonstrates several key principles. First, we defined our expected behavior in tests before implementing the function. Second, we used table-driven testing to cover multiple scenarios concisely. Third, we named our test cases descriptively so that test output is meaningful. Fourth, we verified both positive and edge cases.

Running the tests confirms everything works:

```bash
$ go test -v ./internal/math/
=== RUN   TestAdd
=== RUN   TestAdd/positive_numbers
=== RUN   TestAdd/negative_numbers
=== RUN   TestAdd/mixed_signs
=== RUN   TestAdd/zero_operands
=== RUN   TestAdd/large_numbers
--- PASS: TestAdd (0.00s)
    --- PASS: TestAdd/positive_numbers (0.00s)
    --- PASS: TestAdd/negative_numbers (0.00s)
    --- PASS: TestAdd/mixed_signs (0.00s)
    --- PASS: TestAdd/zero_operands (0.00s)
    --- PASS: TestAdd/large_numbers (0.00s)
PASS
ok      github.com/bulletproof-software/internal/math    0.001s
```

  

## Section 3: The Red-Green-Refactor Cycle

The Red-Green-Refactor cycle is the heartbeat of test-driven development. It provides a disciplined rhythm that guides software construction, ensuring that every line of code serves a tested purpose. Understanding and internalizing this cycle is essential for effective TDD practice.

### Red: Write a Failing Test

Writing the failing test first proves the test can detect the intended behavior gap. This prevents false confidence from tests that only pass because they never exercised the real requirement.


The cycle begins with a failing test—the "red" state. You write a test that describes the behavior you want, but the test fails because the implementation doesn't exist yet. This failure isn't a problem; it's the entire point. By starting with a failing test, you clarify your intent before writing code.

Writing the test first forces you to think about the API from the caller's perspective. What function do you need? What parameters should it accept? What should it return? What errors might occur? These questions are easier to answer before you've committed to an implementation. The test becomes a specification written in executable code.

The failing test also provides immediate feedback. When you run `go test` and see the failure, you know exactly what needs to be built. There's no ambiguity about whether the feature is complete—you'll see the test pass, and that test defines completeness.

Here's an example of starting with a failing test. Suppose we need a function that calculates Fibonacci numbers. We begin by writing the test, knowing it will fail:

  

```go
// internal/fibonacci/fibonacci_test.go
package fibonacci

import (
	"testing"
)

func TestFibonacci(t *testing.T) {
	tests := []struct {
		name     string
		n        int
		expected uint64
		wantErr  bool
	}{
		{
			name:     "Fibonacci of 0",
			n:        0,
			expected: 0,
			wantErr:  false,
		},
		{
			name:     "Fibonacci of 1",
			n:        1,
			expected: 1,
			wantErr:  false,
		},
		{
			name:     "Fibonacci of 10",
			n:        10,
			expected: 55,
			wantErr:  false,
		},
		{
			name:     "negative input",
			n:        -1,
			expected: 0,
			wantErr:  true,
		},
		{
			name:     "overflow input",
			n:        94,
			expected: 0,
			wantErr:  true,
		},
	}

	for _, tt := range tests {
		t.Run(tt.name, func(t *testing.T) {
			result, err := Fibonacci(tt.n)

			if tt.wantErr {
				if err == nil {
					t.Errorf("Fibonacci(%d) expected error, got nil", tt.n)
				}
				return
			}

			if err != nil {
				t.Errorf("Fibonacci(%d) unexpected error: %v", tt.n, err)
				return
			}

			if result != tt.expected {
				t.Errorf("Fibonacci(%d) = %d; want %d", tt.n, result, tt.expected)
			}
		})
	}
}
```

### Green: Make the Test Pass

The green step encourages minimum viable correctness before optimization. This sequence limits overengineering and keeps each change set small, which reduces risk and simplifies debugging.


Once you have a failing test, your goal is to make it pass with the simplest possible implementation. Don't worry about elegance or optimization at this stage—the goal is to get to green as quickly as reasonable. You can always refactor later, but first you need a working solution.

For the Fibonacci example, a simple recursive implementation makes the tests pass:

```go
// internal/fibonacci/fibonacci.go
package fibonacci

import (
	"errors"
)

// Fibonacci returns the nth Fibonacci number.
// Negative inputs return an error.
func Fibonacci(n int) (uint64, error) {
	if n < 0 {
		return 0, errors.New("Fibonacci: negative input not allowed")
	}
	if n > 93 {
		return 0, errors.New("Fibonacci: input overflows uint64; max supported n is 93")
	}

	if n <= 1 {
		return uint64(n), nil
	}

	a, _ := Fibonacci(n - 1)
	b, _ := Fibonacci(n - 2)
	return a + b, nil
}
```

Using `uint64` is deliberate here because it makes overflow boundaries explicit in both code and tests. `F(93)` still fits in `uint64`, but `F(94)` does not, so guarding at `n > 93` prevents silent wraparound bugs that can be very hard to diagnose later.

This recursive version is useful for demonstrating the red-green cycle, but it is intentionally not the production shape. It recomputes the same subproblems many times, so runtime grows exponentially. That cost matters because a test that passes for `n=10` can become impractical for larger inputs.

Running the tests confirms we've achieved green:

```bash
$ go test -v ./internal/fibonacci/
=== RUN   TestFibonacci
=== RUN   TestFibonacci/Fibonacci_of_0
=== RUN   TestFibonacci/Fibonacci_of_1
=== RUN   TestFibonacci/Fibonacci_of_10
=== RUN   TestFibonacci/negative_input
=== RUN   TestFibonacci/overflow_input
--- PASS: TestFibonacci (0.00s)
    --- PASS: TestFibonacci/Fibonacci_of_0 (0.00s)
    --- PASS: TestFibonacci/Fibonacci_of_1 (0.00s)
    --- PASS: TestFibonacci/Fibonacci_of_10 (0.00s)
    --- PASS: TestFibonacci/negative_input (0.00s)
    --- PASS: TestFibonacci/overflow_input (0.00s)
PASS
ok      github.com/bulletproof-software/internal/fibonacci    0.000s
```

### Refactor: Improve Without Breaking Tests

Refactoring with a passing test suite allows architectural improvement without behavior drift. In production codebases, this is how teams keep design quality high while maintaining delivery pace.


With tests passing, you can now refactor with confidence. The tests verify that your refactoring doesn't change behavior. You can rename functions, restructure code, optimize performance, and improve readability—all while knowing that any mistake will be caught immediately.

Our recursive Fibonacci implementation is inefficient for large inputs. Let's refactor it to use iteration, which is much faster:

```go
// internal/fibonacci/fibonacci.go
package fibonacci

import (
	"errors"
)

// Fibonacci returns the nth Fibonacci number.
// Negative inputs return an error.
func Fibonacci(n int) (uint64, error) {
	if n < 0 {
		return 0, errors.New("Fibonacci: negative input not allowed")
	}
	if n > 93 {
		return 0, errors.New("Fibonacci: input overflows uint64; max supported n is 93")
	}

	if n <= 1 {
		return uint64(n), nil
	}

	var a, b uint64 = 0, 1
	for i := 2; i <= n; i++ {
		a, b = b, a+b
	}
	return b, nil
}
```

The iterative form keeps behavior identical while dropping time complexity from exponential to linear and stack usage from deep recursion to constant space. This is exactly the type of refactor tests should protect: same contract, safer implementation for real workloads.

Running the tests confirms our refactoring preserved correctness:

```bash
$ go test -v ./internal/fibonacci/
PASS
ok      github.com/bulletproof-software/internal/fibonacci    0.000s
```

### Continuing the Cycle

Repeatability is where reliability comes from. A single red-green-refactor loop is useful, but consistent loops across features create compounding quality gains and fewer late-stage defects.


The Red-Green-Refactor cycle continues throughout development. Each new feature, each bug fix, each refactoring starts with a test. You build up a comprehensive suite of tests that document your codebase, catch regressions, and enable confident change. Over time, the tests become as valuable as the production code itself.

  

## Section 4: Testing Environment Setup

Before diving deeper into testing techniques, let's ensure your environment is properly configured. This section covers setting up a professional Go testing environment with tools that will serve you throughout this book and your career.

### Module Initialization

Consistent module boundaries and dependency declarations are prerequisites for reproducible builds. Reproducibility is essential for long-term maintainability, especially when patching old releases or investigating production incidents.


Every modern Go project uses Go modules for dependency management. Initialize your project with `go mod init` to create the `go.mod` file that defines your module and dependencies. Using modules ensures reproducible builds and clear dependency management.

```bash
# Initialize a new Go module
go mod init github.com/bulletproof-software/myproject

# Add dependencies as needed
go get github.com/stretchr/testify
```

The `go.mod` file tracks your dependencies with precise versions, while `go.sum` records cryptographic checksums for security and reproducibility. Always commit both files to version control.

### Essential Testing Tools

Tools should amplify judgment, not replace it. Selecting a minimal, high-signal toolchain keeps teams focused on correctness and behavior while avoiding brittle complexity from unnecessary dependencies.

In textbook terms, this section is about engineering leverage. The right tools make good practices easier to repeat and bad practices harder to hide. Over the life of a codebase, that leverage compounds into better reliability outcomes with less rework.


While Go's standard library provides comprehensive testing capabilities, several external tools enhance your testing workflow. The `stretchr/testify` package offers assertion helpers, mock generators, and suite support that reduce boilerplate. The `go.uber.org/goleak` package helps detect goroutine leaks in concurrent code. The `github.com/kyoh86/richgo` package formats test output more readably.

```go
// go.mod
module github.com/bulletproof-software/myproject

go 1.24

require (
    github.com/davecgh/go-spew v1.1.1
    github.com/pmezard/go-difflib v1.0.0
    github.com/stretchr/testify v1.8.4
    github.com/google/go-cmp v0.6.0
    go.uber.org/goleak v1.3.0
)
```

### Test Configuration with golangci-lint

Linting in test code catches blind spots like weak assertions, ignored errors, and flaky patterns before they reach CI. Stable lint rules raise floor quality across contributors with different experience levels.


Lint configuration should encode team standards that improve reliability, not stylistic preferences that create noise. Start from checks with clear correctness or maintainability impact and add stricter rules gradually with documented rationale.

Version control your lint policy and review it periodically as Go tooling evolves. Stable, intentional linting keeps signal high and prevents churn during upgrades.


Code quality tools like `golangci-lint` enforce consistent style and catch common mistakes. Configure it to run tests and linting in your CI pipeline:

```yaml
# .golangci.yml
linters:
  enable:
    - errcheck
    - gosimple
    - govet
    - ineffassign
    - staticcheck
    - typecheck
    - unused
    - gofmt
    - goimports
    
linters-settings:
  errcheck:
    check-type-assertions: true
    check-blank: true
    
  govet:
    check-shadowing: true
    enable-all: true

run:
  timeout: 5m
  tests: true
```

### Continuous Integration for Tests

CI is the enforcement boundary for team-wide reliability. It ensures every contribution meets the same objective quality bar regardless of local machine state or individual workflow habits.


CI test execution should optimize for deterministic results and short mean time to diagnosis. Keep test steps explicit, fail early on environment misconfiguration, and publish artifacts that help engineers debug without rerunning entire pipelines.


Your CI pipeline should run tests on every commit. Here's a GitHub Actions workflow that runs tests with coverage reporting:

  

```yaml
# .github/workflows/tests.yml
name: Tests

on:
  push:
    branches: [main, develop]
  pull_request:
    branches: [main]

jobs:
  test:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v4
      
      - name: Set up Go
        uses: actions/setup-go@v5
        with:
          go-version: '1.24'
      
      - name: Cache Go modules
        uses: actions/cache@v4
        with:
          path: |
            ~/.cache/go-build
            ~/go/pkg/mod
          key: ${{ runner.os }}-go-${{ hashFiles('**/go.sum') }}
          restore-keys: |
            ${{ runner.os }}-go-
      
      - name: Download dependencies
        run: go mod download
      
      - name: Run tests with race detector
        run: go test -race -coverprofile=coverage.out ./...
      
      - name: Upload coverage
        uses: codecov/codecov-action@v3
        with:
          files: ./coverage.out
          fail_ci_if_error: true
```

### IDE Integration

Integrating test feedback into the editor shortens the loop between change and verification. Short loops increase test frequency, and frequent testing is one of the strongest predictors of fewer escaped defects.


Modern IDEs provide excellent Go testing integration. VS Code with the official Go extension offers test discovery, one-click test runs, and coverage highlighting within the editor. GoLand provides similar capabilities with additional features like test generation and mock creation. Configure your IDE to run tests on save for rapid feedback during development.

  

## Section 5: Writing Comprehensive Tests

With your environment configured, you're ready to write thorough tests for real-world scenarios. This section demonstrates testing patterns that scale to complex applications.

### Test Structure Best Practices

In production systems, test structure is part of design, not just verification. A consistent Arrange-Act-Assert shape keeps failure messages focused on one behavior and makes future refactors safer because intent stays visible. When tests become hard to read, they stop being documentation and teams lose confidence in changing code.


Effective tests share common characteristics: they're focused on a single behavior, clearly named, independent of other tests, and thorough in covering edge cases. Let's build a validation package with comprehensive tests to illustrate these principles.

  

```go
// internal/validator/email_test.go
package validator

import (
	"testing"
)

func TestValidateEmail(t *testing.T) {
	tests := []struct {
		name  string
		email string
		valid bool
	}{
		{
			name:  "standard valid email",
			email: "user@example.com",
			valid: true,
		},
		{
			name:  "email with subdomain",
			email: "user@mail.example.com",
			valid: true,
		},
		{
			name:  "email with plus addressing",
			email: "user+tag@example.com",
			valid: true,
		},
		{
			name:  "email with dots in local part",
			email: "first.last@example.com",
			valid: true,
		},
		{
			name:  "missing local part",
			email: "@example.com",
			valid: false,
		},
		{
			name:  "missing domain",
			email: "user@",
			valid: false,
		},
		{
			name:  "missing @ symbol",
			email: "userexample.com",
			valid: false,
		},
		{
			name:  "empty string",
			email: "",
			valid: false,
		},
		{
			name:  "only @ symbol",
			email: "@",
			valid: false,
		},
		{
			name:  "multiple @ symbols",
			email: "user@@example.com",
			valid: false,
		},
		{
			name:  "space in email",
			email: "user @example.com",
			valid: false,
		},
		{
			name:  "Unicode email",
			email: "用户@例子.测试",
			valid: true,
		},
	}

	for _, tt := range tests {
		t.Run(tt.name, func(t *testing.T) {
			err := ValidateEmail(tt.email)

			if tt.valid && err != nil {
				t.Errorf("ValidateEmail(%q) = %v; want nil", tt.email, err)
			}

			if !tt.valid && err == nil {
				t.Errorf("ValidateEmail(%q) = nil; want error", tt.email)
			}
		})
	}
}
```

### Testing with Assertions

Assertion style controls failure readability. High-quality assertions turn failures into immediate diagnosis clues, which lowers debugging time and keeps test suites valuable as systems scale.


Assertions should improve signal, not hide behavior. Prefer clear, direct comparisons and error messages that include input context, expected value, and actual value. High-quality assertion output lowers investigation time and makes test failures actionable.


While Go's standard library requires explicit comparisons and error checking, assertion libraries reduce boilerplate. The `testify/assert` package provides functions like `assert.Equal`, `assert.Error`, and `assert.Contains` that produce clear failure messages:

  

```go
// internal/validator/email_test.go
package validator

import (
	"testing"

	"github.com/stretchr/testify/assert"
)

func TestValidateEmail_WithTestify(t *testing.T) {
	tests := []struct {
		name    string
		email   string
		wantErr bool
	}{
		{
			name:    "valid email",
			email:   "user@example.com",
			wantErr: false,
		},
		{
			name:    "invalid email missing @",
			email:   "userexample.com",
			wantErr: true,
		},
		{
			name:    "invalid email empty",
			email:   "",
			wantErr: true,
		},
	}

	for _, tt := range tests {
		t.Run(tt.name, func(t *testing.T) {
			err := ValidateEmail(tt.email)

			if tt.wantErr {
				assert.Error(t, err)
			} else {
				assert.NoError(t, err)
			}
		})
	}
}
```

### Error Path Testing

Production incidents usually live in failure paths, not happy paths. Testing explicit error behavior verifies that the system fails safely, communicates clearly, and recovers predictably under stress.


Comprehensive testing includes verifying that errors occur when expected. Tests for error conditions ensure your code handles edge cases gracefully:

  

```go
// internal/validator/validation_test.go
package validator

import (
	"testing"

	"github.com/stretchr/testify/assert"
)

func TestValidatePassword(t *testing.T) {
	tests := []struct {
		name     string
		password string
		wantErr  bool
		errType  error
	}{
		{
			name:     "valid strong password",
			password: "SecureP@ssw0rd!",
			wantErr:  false,
			errType:  nil,
		},
		{
			name:     "password too short",
			password: "short",
			wantErr:  true,
			errType:  ErrPasswordTooShort,
		},
		{
			name:     "password no uppercase",
			password: "lowercase123!",
			wantErr:  true,
			errType:  ErrPasswordNoUppercase,
		},
		{
			name:     "password no lowercase",
			password: "UPPERCASE123!",
			wantErr:  true,
			errType:  ErrPasswordNoLowercase,
		},
		{
			name:     "password no digit",
			password: "NoDigits!",
			wantErr:  true,
			errType:  ErrPasswordNoDigit,
		},
		{
			name:     "password no special char",
			password: "NoSpecialChar123",
			wantErr:  true,
			errType:  ErrPasswordNoSpecialChar,
		},
	}

	for _, tt := range tests {
		t.Run(tt.name, func(t *testing.T) {
			err := ValidatePassword(tt.password)

			if tt.wantErr {
				assert.Error(t, err)
				if tt.errType != nil {
					assert.ErrorIs(t, err, tt.errType)
				}
			} else {
				assert.NoError(t, err)
			}
		})
	}
}
```

  

## Section 6: Benchmark Testing

Beyond correctness tests, Go's testing framework supports benchmarks that measure performance. Benchmarks ensure your code meets performance requirements and help identify regressions.

### Writing Benchmarks

Performance assumptions are often wrong without measurement. Benchmarks provide objective data so optimization decisions are grounded in evidence and aligned with user-facing outcomes.


Benchmark results are only useful when inputs represent realistic workloads and comparisons are reproducible. Track baseline numbers in CI artifacts and investigate regressions as part of normal review, not only during performance incidents.


Benchmark functions start with `Benchmark` and receive a `*testing.B` parameter. The framework runs the benchmark function multiple times, adjusting the iteration count until statistically significant results are obtained:

```go
// internal/fibonacci/fibonacci_test.go
package fibonacci

import (
	"strconv"
	"testing"
)

func BenchmarkFibonacci(b *testing.B) {
	values := []int{10, 20, 30, 40}

	for _, n := range values {
		b.Run(strconv.Itoa(n), func(b *testing.B) {
			b.ResetTimer()
			for i := 0; i < b.N; i++ {
				_, _ = Fibonacci(n)
			}
		})
	}
}

func BenchmarkFibonacciIterative(b *testing.B) {
	// Benchmark different values
	values := []int{10, 20, 30, 40, 50}

	for _, n := range values {
		b.Run(strconv.Itoa(n), func(b *testing.B) {
			b.ResetTimer()
			for i := 0; i < b.N; i++ {
				_, _ = Fibonacci(n)
			}
		})
	}
}
```

Running benchmarks with `go test -bench=. -benchmem` produces output like:

```
goos: darwin
goarch: arm64
pkg: github.com/bulletproof-software/internal/fibonacci
BenchmarkFibonacci-8              5000000               241.5 ns/op        0 B/op        0 allocs/op
BenchmarkFibonacci/10-8         100000000                10.23 ns/op       0 B/op        0 allocs/op
BenchmarkFibonacci/20-8           5000000               287.6 ns/op        0 B/op        0 allocs/op
BenchmarkFibonacci/30-8            200000               720.4 ns/op        0 B/op        0 allocs/op
BenchmarkFibonacci/40-8             30000              4562 ns/op          0 B/op        0 allocs/op
```

### Memory Allocation Profiling

Allocation behavior affects latency, throughput, and garbage collection pressure. Understanding allocation hotspots helps prevent performance regressions that only appear under sustained production load.


Benchmarks can also measure memory allocations, which is crucial for understanding garbage collection pressure:

```go
func BenchmarkFibonacciWithAllocations(b *testing.B) {
	b.ReportAllocs()

	for i := 0; i < b.N; i++ {
		_, _ = Fibonacci(30)
	}
}
```

The `ReportAllocs()` method adds allocation counts to the benchmark output, helping you identify functions that create excessive garbage.

  

## Section 7: Test Coverage Analysis

Code coverage metrics help identify untested code paths. While 100% coverage isn't always practical or valuable, understanding what your tests cover guides testing effort.

### Generating Coverage Reports

Coverage reports are navigation tools for risk, not vanity metrics. They help teams identify unverified behavior zones and prioritize testing effort where defects are most likely.

Used correctly, coverage data supports planning and review conversations. It helps teams ask better questions such as "which error paths are still untested?" and "which recent refactor changed unverified logic?" rather than merely chasing a percentage target.


Go's `-coverprofile` flag generates coverage data that can be analyzed:

```bash
# Generate coverage profile
go test -coverprofile=coverage.out ./...

# View coverage in terminal
go tool cover -func=coverage.out

# Generate HTML coverage report
go tool cover -html=coverage.out -o coverage.html
```

### Coverage by Function

Function-level coverage reveals localized blind spots that aggregate coverage percentages can hide. This granularity helps reviewers target missing tests before changes merge.

Function-level analysis is especially useful in large services where broad package coverage can mask critical gaps in validation, authorization, or state-transition logic. Looking at functions directly keeps reliability work connected to actual behavior boundaries.


To focus on specific packages, filter the coverage report:

```bash
# Coverage for specific package
go test -coverprofile=coverage.out ./internal/validator/
go tool cover -func=coverage.out | grep validator
```

### Interpreting Coverage Data

Correct interpretation prevents metric abuse. High coverage with weak assertions can still miss critical failures, so teams must pair coverage data with behavior-focused test quality.


Coverage reports show which lines are exercised by tests. The output distinguishes between covered lines (shown with coverage counts) and uncovered lines. Focus on covering critical paths, error handling, and edge cases rather than pursuing arbitrary coverage percentages.

## Prompt Engineering for This Topic

Mastering prompt engineering for test-driven development involves understanding what information AI assistants need to generate comprehensive tests. The quality of prompts directly affects the quality of generated tests.

### Effective Prompts for Testing

**Good Prompt 1:**

```
Create a Go package for parsing and validating credit card numbers. Include:

1. A ValidateCard function that checks card number validity using the Luhn algorithm
2. Support for Visa, Mastercard, Amex, and Discover card formats
3. Comprehensive table-driven tests covering:
   - Valid card numbers for each network
   - Invalid length and checksum
   - Invalid prefix patterns
   - Empty and malformed input
4. Benchmark tests for the validation function
5. Use testify/assert for assertions

Return the complete implementation in calculator.go and tests in calculator_test.go.
```

**Why It Works:** This prompt specifies exactly what function to create, the algorithm to implement, the testing framework to use, and detailed test cases. The "why" (Luhn algorithm) and the "what" (validation rules) are both clear.

**Good Prompt 2:**

```
Build a Go function that implements a rate limiter using the token bucket algorithm.

The rate limiter should:
- Accept requests per second and burst capacity as configuration
- Track tokens in a thread-safe manner using a mutex
- Implement a TryConsume method that returns false when out of tokens
- Handle concurrent access from multiple goroutines

Write comprehensive tests:
1. Basic rate limiting behavior
2. Burst capacity handling
3. Token refill over time
4. Concurrent access from multiple goroutines
5. Race detector validation

Include the race detector in your test runs.
```

**Why It Works:** This prompt specifies the algorithm, concurrency requirements, test scenarios, and explicitly requests race detection. It covers both correctness and concurrency concerns.

**Good Prompt 3:**

```
Create a user repository interface and implementation for a PostgreSQL database.

The repository should:
- Define interfaces in a separate file (repository.go)
- Implement CRUD operations for a User type
- Use database/sql with proper error handling
- Support transactions with rollback

Write tests using sqlmock:
1. Successful create operation
2. Create with constraint violation (duplicate email)
3. Successful read by ID
4. Read with not found error
5. Update with optimistic locking
6. Delete operation
7. Transaction commit
8. Transaction rollback on error

Each test should verify both the success path and any error conditions.
```

**Why It Works:** This prompt separates interface design from implementation, specifies the database operations, requires transaction testing, and specifies mock-based unit tests for database operations.

### Ineffective Prompts and Why They Fail

**Ineffective Prompt 1:**

```
Write tests for user validation in Go.
```

**Why It Fails:** No specification of what validation rules exist, no testing framework preference, no test case examples, no implementation provided. The AI cannot generate meaningful tests without understanding what behavior to verify.

**Ineffective Prompt 2:**

```
Create a rate limiter with tests. I need it to work fast and handle lots of users.
```

**Why It Fails:** Vague requirements ("fast," "lots of users"), no algorithm specified, no testing requirements, no performance benchmarks defined. The AI cannot determine what "fast enough" means or how to verify it.

**Ineffective Prompt 3:**

```
Make the validation code better and add tests for edge cases.
```

**Why It Fails:** No existing code provided, no definition of "better," no specification of edge cases. The AI has no baseline to improve upon or targets to verify.

### Prompt Construction Framework

Effective prompts for test-driven development include these components:

1. **Context:** What system or domain is this for? Why are you building this feature?
2. **Requirements:** What exactly should the function/type do? What inputs does it accept? What outputs does it produce?
3. **Error Handling:** What error conditions exist? What should happen for invalid inputs?
4. **Test Scenarios:** What test cases should be covered? Include normal cases, edge cases, and error conditions.
5. **Performance Concerns:** Are there performance requirements? Should benchmarks be included?
6. **Concurrency Requirements:** Is this code concurrent? Should tests verify thread safety?
7. **Output Format:** How should the code be organized? Which testing framework to use?

## Common Pitfalls

Avoid these mistakes that undermine testing effectiveness:

### Pitfall 1: Testing Implementation Details

Tests tied to internals become brittle during healthy refactoring. Behavior-oriented tests preserve design freedom while still protecting user-visible correctness.


Tests that verify internal implementation rather than external behavior become fragile. When you refactor internal code, passing tests should continue passing. If tests fail because implementation details changed, they're testing the wrong thing.

**Solution:** Test behavior, not implementation. Verify outputs given inputs, not which functions were called internally.

### Pitfall 2: Ignoring Error Paths

Untested errors become reliability debt that surfaces under pressure. Explicitly validating error outcomes prevents surprise failures during peak traffic and dependency outages.


Many developers test only happy paths, leaving error handling completely untested. Error paths are often the most buggy because they're rarely exercised during manual testing.

**Solution:** Explicitly test every error condition. Your table-driven tests should include cases where functions return errors.

### Pitfall 3: Order-Dependent Tests

Order dependence hides shared-state coupling and creates flaky CI failures. Deterministic, isolated tests are critical for trustworthy automation and fast release velocity.


Tests that depend on execution order are unreliable. They might pass when run individually but fail when run together, or vice versa. The Go test runner doesn't guarantee execution order.

**Solution:** Make each test independent. Clean up any shared state in defer statements or `t.Cleanup()`.

### Pitfall 4: Not Using the Race Detector

Data races can pass local testing and still corrupt production behavior under concurrency. Race detection catches undefined behavior early, before it becomes an intermittent and expensive outage.


Concurrent code often appears to work correctly but contains subtle race conditions. These bugs are hard to reproduce and diagnose in production.

**Solution:** Run `go test -race` regularly, especially after any concurrent code changes. Include race detection in CI.

## Best Practices Summary

This chapter established fundamental principles that will guide all subsequent testing:

- Write tests before implementation to clarify requirements and ensure testability
- Use the Red-Green-Refactor cycle to guide development pace
- Cover normal cases, edge cases, and error conditions equally
- Use table-driven tests for organized, comprehensive test coverage
- Configure your environment for professional testing workflows
- Run the race detector on concurrent code
- Benchmark performance-critical paths
- Measure and review code coverage to identify untested areas

## Exercises

### Exercise 1.1: String Reversal Function

Simple transformation functions are ideal for practicing edge-case thinking, table-driven design, and clear failure messaging, all of which scale directly to larger features.


Write a function that reverses a string and comprehensive tests. Your tests should cover:

- Normal strings of various lengths
- Empty strings
- Single characters
- Unicode characters (including multi-byte)
- Strings with whitespace
- Strings that are palindromes

**Test Template:**

  

```go
// internal/reverse/reverse_test.go
package reverse

import (
	"testing"
)

func TestReverse(t *testing.T) {
	tests := []struct {
		name     string
		input    string
		expected string
	}{
		// Add your test cases here
	}

	for _, tt := range tests {
		t.Run(tt.name, func(t *testing.T) {
			result := Reverse(tt.input)
			if result != tt.expected {
				t.Errorf("Reverse(%q) = %q; want %q", tt.input, result, tt.expected)
			}
		})
	}
}

func TestReverse_Unicode(t *testing.T) {
	// Add Unicode-specific tests
	// Test Japanese, Chinese, Emoji characters
}
```

### Exercise 1.2: Prime Number Function

Numeric logic surfaces boundary conditions and algorithm assumptions quickly. Learning to test these carefully builds discipline for correctness-critical code paths.


Write a function that checks if a number is prime. Include:

- Table-driven tests for prime and composite numbers
- Tests for edge cases (0, 1, negative numbers)
- Performance benchmarks for large numbers
- Comparison between different implementation approaches

### Exercise 1.3: Stack Data Structure

Data-structure exercises force explicit reasoning about invariants, mutation, and invalid operations. That same reasoning is essential for reliable business-state transitions in production systems.


Implement a generic stack with tests:

- Push and pop operations
- Stack underflow on empty pop
- Stack peek without removal
- Stack length verification
- Concurrent push/pop operations with race detector

## Further Reading

- Go Testing Package Documentation: https://pkg.go.dev/testing
- Testify Assertion Package: https://pkg.go.dev/github.com/stretchr/testify
- Go Blog: Using Go Modules: https://go.dev/blog/using-go-modules
- Effective Go: Testing: https://go.dev/doc/effective_go#testing
- Dave Cheney's Testing Workshop: https://dave.cheney.net/workshops

## Chapter Summary

This chapter established the foundation for test-driven development in Go. You learned that comprehensive testing transforms software development from uncertain debugging to confident construction. The economic argument for testing is compelling: catching bugs early saves enormous costs compared to production remediation.

Go's testing ecosystem, built into the standard library, provides everything needed for professional testing. The `testing` package offers comprehensive functionality, and conventions like `_test.go` files and `Test*` function names enable automatic test discovery. The race detector, benchmark support, and coverage tools integrate seamlessly.

The Red-Green-Refactor cycle provides a disciplined rhythm for development. Writing tests first clarifies requirements, forces good API design, and ensures everything you build is tested. Making tests pass with minimal implementation gets you to green quickly, and refactoring with test confidence improves code quality without fear.

The patterns established here—table-driven tests, assertion helpers, benchmark functions, coverage analysis—will serve you throughout this book and your career. Chapter 2 will build on this foundation, exploring Go's type system and error handling patterns that enable robust, testable code.

---

  

# Chapter 2: Go Reliability Patterns and Core Semantics

### Learning Objectives

This chapter's objectives are not syntax goals; they are reliability goals. Treat each concept as a tool for making behavior explicit, testable, and safe to evolve over time.

Read these objectives as operational competencies, not checklist items. The goal is to internalize decisions that prevent defects early: choosing better types, modeling errors with intent, and understanding data-structure semantics before they become production issues.


- Master Go's type system and understand how static typing contributes to reliability
- Implement robust error handling patterns using custom error types and error wrapping
- Understand pointers, memory allocation, and how to avoid common memory errors
- Work effectively with slices, maps, and other built-in data structures
- Apply test-driven development principles to fundamental Go programming concepts
- Recognize idiomatic Go patterns that produce maintainable, production-ready code

### Introduction: Types as Documentation and Safety

Go's type system forms the foundation upon which reliable software is built. Unlike dynamically typed languages where type errors manifest at runtime as mysterious failures, Go catches type mismatches at compile time, before your code ever runs. This static verification, combined with comprehensive testing, creates a powerful defense against defects.

Types serve dual purposes in Go: they enable the compiler to verify correctness, and they document your intent to other developers. When you see a function signature like `func ProcessUser(user User) error`, the types communicate that this function accepts a User struct and may fail. Reading the implementation reveals exactly how the function behaves, but the types establish a contract that the compiler enforces.

This chapter explores the fundamental building blocks of Go programming through the lens of test-driven development. Every concept is presented with tests first, demonstrating how testing reinforces your understanding of Go's type system, error handling, memory model, and data structures. By the end of this chapter, you'll have a solid foundation in Go programming that enables the advanced topics in subsequent chapters.

The patterns established here—custom error types, proper pointer usage, slice and map operations—appear throughout production Go codebases. Mastering these fundamentals means you'll immediately recognize idiomatic Go when you see it, and you'll write code that feels natural to experienced Go developers.

This is not a from-scratch Go syntax course. It is a production-oriented fundamentals chapter aimed at readers who already know programming basics and want to understand how Go semantics influence reliability, testing, and maintainable system design.

  

## Section 1: Go's Type System and Testing

Go's type system provides compile-time guarantees that reduce runtime errors significantly. Understanding how types work, and testing that your understanding is correct, sets the stage for all Go programming.

### Basic Types and Type Inference

Type choices encode assumptions about value ranges, precision, and representation. Correct type selection prevents silent bugs and makes intent visible during code review.


Go provides basic types for integers, floating-point numbers, strings, and booleans. Each type has specific characteristics that affect how you use it. Testing helps solidify your understanding of these types and their behaviors.

  

```go
// internal/types/basic_test.go
package types

import (
	"testing"
)

func TestIntegerTypes(t *testing.T) {
	tests := []struct {
		name     string
		a        int
		b        int
		expected int
		op       func(int, int) int
	}{
		{
			name:     "addition positive",
			a:        5,
			b:        3,
			expected: 8,
			op:       func(a, b int) int { return a + b },
		},
		{
			name:     "addition with zero",
			a:        10,
			b:        0,
			expected: 10,
			op:       func(a, b int) int { return a + b },
		},
		{
			name:     "subtraction negative result",
			a:        5,
			b:        10,
			expected: -5,
			op:       func(a, b int) int { return a - b },
		},
		{
			name:     "multiplication large numbers",
			a:        1000,
			b:        500,
			expected: 500000,
			op:       func(a, b int) int { return a * b },
		},
	}

	for _, tt := range tests {
		t.Run(tt.name, func(t *testing.T) {
			result := tt.op(tt.a, tt.b)
			if result != tt.expected {
				t.Errorf("%s(%d, %d) = %d; want %d", tt.name, tt.a, tt.b, result, tt.expected)
			}
		})
	}
}

func TestStringOperations(t *testing.T) {
	tests := []struct {
		name     string
		input    string
		expected int
	}{
		{
			name:     "string length ASCII",
			input:    "hello",
			expected: 5,
		},
		{
			name:     "string length Unicode",
			input:    "hello世界",
			expected: 11, // 5 ASCII + 6 bytes for two Chinese characters
		},
		{
			name:     "empty string",
			input:    "",
			expected: 0,
		},
	}

	for _, tt := range tests {
		t.Run(tt.name, func(t *testing.T) {
			result := len(tt.input)
			if result != tt.expected {
				t.Errorf("len(%q) = %d; want %d", tt.input, result, tt.expected)
			}
		})
	}
}
```

These tests demonstrate Go's type system in action. The `int` type represents signed integers, and operations on integers follow mathematical rules. Strings in Go are immutable sequences of bytes, and the `len()` function returns the number of bytes, not the number of Unicode characters—a common source of bugs when dealing with international text.

### Defining Custom Types

Custom types create semantic boundaries that generic primitives cannot express. They reduce accidental misuse and make domain rules enforceable by the compiler.


Go allows you to define new types based on existing ones. This capability is essential for creating domain-specific abstractions that are checked by the compiler.

  

```go
// internal/types/user_test.go
package types

import (
	"testing"
)

// UserID represents a unique user identifier.
// It is based on int64 to support large user bases.
type UserID int64

// User represents an authenticated user in the system.
type User struct {
	ID       UserID
	Email    string
	Name     string
	Age      int
	IsActive bool
}

// NewUser creates a new user with the given parameters.
// Returns an error if the email is invalid or the name is empty.
func NewUser(email, name string, age int) (*User, error) {
	if email == "" {
		return nil, ErrInvalidEmail
	}
	if name == "" {
		return nil, ErrEmptyName
	}
	if age < 0 {
		return nil, ErrInvalidAge
	}

	return &User{
		ID:       UserID(generateID()),
		Email:    email,
		Name:     name,
		Age:      age,
		IsActive: true,
	}, nil
}

// Custom error types for validation
var (
	ErrInvalidEmail = errors.New("invalid email address")
	ErrEmptyName    = errors.New("name cannot be empty")
	ErrInvalidAge   = errors.New("age must be non-negative")
)

func TestNewUser(t *testing.T) {
	tests := []struct {
		name     string
		email    string
		userName string
		age      int
		wantErr  error
	}{
		{
			name:     "valid user",
			email:    "user@example.com",
			userName: "John Doe",
			age:      30,
			wantErr:  nil,
		},
		{
			name:     "empty email",
			email:    "",
			userName: "John Doe",
			age:      30,
			wantErr:  ErrInvalidEmail,
		},
		{
			name:     "empty name",
			email:    "user@example.com",
			userName: "",
			age:      30,
			wantErr:  ErrEmptyName,
		},
		{
			name:     "negative age",
			email:    "user@example.com",
			userName: "John Doe",
			age:      -1,
			wantErr:  ErrInvalidAge,
		},
	}

	for _, tt := range tests {
		t.Run(tt.name, func(t *testing.T) {
			user, err := NewUser(tt.email, tt.userName, tt.age)

			if tt.wantErr != nil {
				if err != tt.wantErr {
					t.Errorf("NewUser() error = %v; want %v", err, tt.wantErr)
				}
				return
			}

			if err != nil {
				t.Errorf("NewUser() unexpected error: %v", err)
				return
			}

			if user.Email != tt.email {
				t.Errorf("user.Email = %q; want %q", user.Email, tt.email)
			}
			if user.Name != tt.userName {
				t.Errorf("user.Name = %q; want %q", user.Name, tt.userName)
			}
			if !user.IsActive {
				t.Error("user.IsActive = false; want true")
			}
		})
	}
}
```

This example demonstrates several important concepts. First, custom types like `UserID` provide type safety—you can't accidentally pass a regular `int64` where a `UserID` is expected. Second, struct types aggregate related data. Third, constructor functions like `NewUser` enable validation and initialization. Fourth, tests verify both success and failure cases.

### Zero Values and Their Testing Implications

Zero values influence default behavior across APIs and structs. Understanding them helps you design safer defaults and catch initialization bugs before they escape into production.


Every type in Go has a zero value—the value a variable has when declared but not initialized. For numeric types, it's `0`. For booleans, it's `false`. For strings, it's `""`. For pointers, slices, maps, and functions, it's `nil`. Understanding zero values prevents entire categories of bugs.

  

```go
// internal/types/zero_test.go
package types

import "testing"

func TestZeroValues(t *testing.T) {
	tests := []struct {
		name  string
		check func(t *testing.T)
	}{
		{
			name: "integer zero value",
			check: func(t *testing.T) {
				var i int
				if i != 0 {
					t.Errorf("int zero value = %d; want 0", i)
				}
			},
		},
		{
			name: "boolean zero value",
			check: func(t *testing.T) {
				var b bool
				if b != false {
					t.Errorf("bool zero value = %v; want false", b)
				}
			},
		},
		{
			name: "string zero value",
			check: func(t *testing.T) {
				var s string
				if s != "" {
					t.Errorf("string zero value = %q; want \"\"", s)
				}
			},
		},
		{
			name: "slice zero value is nil",
			check: func(t *testing.T) {
				var s []int
				if s != nil {
					t.Errorf("slice zero value is not nil")
				}
				// But len and cap still work
				if len(s) != 0 || cap(s) != 0 {
					t.Errorf("nil slice: len=%d, cap=%d; want 0, 0", len(s), cap(s))
				}
			},
		},
		{
			name: "map zero value is nil",
			check: func(t *testing.T) {
				var m map[string]int
				if m != nil {
					t.Errorf("map zero value is not nil")
				}
				// Reading from nil map returns zero value
				v := m["key"]
				if v != 0 {
					t.Errorf("read from nil map = %d; want 0", v)
				}
			},
		},
	}

	for _, tt := range tests {
		t.Run(tt.name, func(t *testing.T) {
			tt.check(t)
		})
	}
}
```

Zero values enable useful patterns. A nil slice can be appended to without initialization. A nil map can be read from (returning zero values). However, writing to a nil map causes a panic, which tests like these help you discover and prevent.

### Interfaces Enable Testability

Interfaces are long-term change boundaries. Properly scoped interfaces decouple policy from implementation, enabling replacement and testing without costly architectural rewrites.


Interfaces are Go's mechanism for abstraction and polymorphism. They enable dependency injection, mocking, and testable code architecture.

  

```go
// internal/types/repository_test.go
package types

import (
	"errors"
	"testing"
)

// Repository defines data access operations.
type Repository interface {
	Get(id int64) (*User, error)
	Create(user *User) error
	Update(user *User) error
	Delete(id int64) error
}

// MockRepository implements Repository for testing.
type MockRepository struct {
	users map[int64]*User
	err   error
}

func NewMockRepository() *MockRepository {
	return &MockRepository{
		users: make(map[int64]*User),
	}
}

func (m *MockRepository) Get(id int64) (*User, error) {
	if m.err != nil {
		return nil, m.err
	}
	user, exists := m.users[id]
	if !exists {
		return nil, ErrNotFound
	}
	return user, nil
}

func (m *MockRepository) Create(user *User) error {
	if m.err != nil {
		return m.err
	}
	m.users[user.ID] = user
	return nil
}

func (m *MockRepository) Update(user *User) error {
	if m.err != nil {
		return m.err
	}
	if _, exists := m.users[user.ID]; !exists {
		return ErrNotFound
	}
	m.users[user.ID] = user
	return nil
}

func (m *MockRepository) Delete(id int64) error {
	if m.err != nil {
		return m.err
	}
	delete(m.users, id)
	return nil
}

// UserService uses Repository through an interface.
type UserService struct {
	repo Repository
}

func NewUserService(repo Repository) *UserService {
	return &UserService{repo: repo}
}

func (s *UserService) GetUser(id int64) (*User, error) {
	return s.repo.Get(id)
}

func TestUserServiceGetUser(t *testing.T) {
	tests := []struct {
		name      string
		userID    int64
		setupMock func(*MockRepository)
		wantErr   error
	}{
		{
			name:   "user found",
			userID: 1,
			setupMock: func(m *MockRepository) {
				m.users[1] = &User{
					ID:    1,
					Email: "test@example.com",
					Name:  "Test User",
				}
			},
			wantErr: nil,
		},
		{
			name:      "user not found",
			userID:    999,
			setupMock: func(m *MockRepository) {},
			wantErr:   ErrNotFound,
		},
		{
			name:   "repository error",
			userID: 1,
			setupMock: func(m *MockRepository) {
				m.err = errors.New("database connection failed")
			},
			wantErr: errors.New("database connection failed"),
		},
	}

	for _, tt := range tests {
		t.Run(tt.name, func(t *testing.T) {
			mock := NewMockRepository()
			tt.setupMock(mock)

			service := NewUserService(mock)
			user, err := service.GetUser(tt.userID)

			if tt.wantErr != nil {
				if err == nil {
					t.Errorf("GetUser() error = nil; want error")
					return
				}
				if err.Error() != tt.wantErr.Error() {
					t.Errorf("GetUser() error = %v; want %v", err, tt.wantErr)
				}
				return
			}

			if err != nil {
				t.Errorf("GetUser() unexpected error: %v", err)
				return
			}

			if user == nil {
				t.Error("GetUser() returned nil user")
			}
		})
	}
}
```

This pattern—defining interfaces, creating mock implementations for testing, and using dependency injection—appears throughout production Go code. It enables you to test business logic without touching databases, external APIs, or other slow or unreliable dependencies.

  

## Section 2: Error Handling Patterns

Go's approach to error handling differs fundamentally from exception-based languages. Rather than throwing exceptions that propagate up the call stack, Go functions explicitly return errors as values. This design makes error handling visible and forces developers to address failure cases.

### The Error Interface

Go's minimal error interface encourages explicit failure modeling instead of hidden control flow. This explicitness is foundational to predictable behavior in distributed systems.


Go's `error` type is an interface with a single method:

```go
type error interface {
	Error() string
}
```

Any type that implements this interface can be used as an error. This simplicity enables powerful error handling patterns.

### Basic Error Handling

Repetitive `if err != nil` checks are a deliberate reliability tradeoff. They keep failure handling local and visible, reducing surprises that are common in exception-driven stacks.


Explicit error checks are one of Go's strongest reliability features. They force failure paths into normal code review and testing instead of burying them in exceptional control flow. The result is software that fails predictably and is easier to operate.


  

```go
// internal/errors/basic_test.go
package errors

import (
	"errors"
	"testing"
)

// divide performs integer division with error checking.
func divide(a, b int) (int, error) {
	if b == 0 {
		return 0, errors.New("division by zero")
	}
	return a / b, nil
}

func TestDivide(t *testing.T) {
	tests := []struct {
		name      string
		a         int
		b         int
		want      int
		wantErr   bool
		errString string
	}{
		{
			name:    "normal division",
			a:       10,
			b:       2,
			want:    5,
			wantErr: false,
		},
		{
			name:    "negative result",
			a:       10,
			b:       -2,
			want:    -5,
			wantErr: false,
		},
		{
			name:      "division by zero",
			a:         10,
			b:         0,
			want:      0,
			wantErr:   true,
			errString: "division by zero",
		},
	}

	for _, tt := range tests {
		t.Run(tt.name, func(t *testing.T) {
			got, err := divide(tt.a, tt.b)

			if tt.wantErr {
				if err == nil {
					t.Errorf("divide(%d, %d) error = nil; want error", tt.a, tt.b)
					return
				}
				if err.Error() != tt.errString {
					t.Errorf("divide() error = %q; want %q", err.Error(), tt.errString)
				}
				return
			}

			if err != nil {
				t.Errorf("divide(%d, %d) unexpected error: %v", tt.a, tt.b, err)
				return
			}

			if got != tt.want {
				t.Errorf("divide(%d, %d) = %d; want %d", tt.a, tt.b, got, tt.want)
			}
		})
	}
}
```

This pattern—checking `if err != nil` after every error-returning function call—appears throughout Go code. While verbose, it makes error handling explicit and prevents errors from being silently ignored.

### Custom Error Types

Structured errors allow callers, logs, and API translators to make consistent decisions. This creates stable contracts between layers and better operational diagnostics.


Creating custom error types enables adding context and behavior to errors.

  

```go
// internal/errors/custom_test.go
package errors

import (
	"errors"
	"fmt"
	"testing"
)

// ValidationError represents an input validation failure.
type ValidationError struct {
	Field   string
	Message string
}

func (e *ValidationError) Error() string {
	return fmt.Sprintf("validation failed for %s: %s", e.Field, e.Message)
}

// NewValidationError creates a validation error.
func NewValidationError(field, message string) *ValidationError {
	return &ValidationError{
		Field:   field,
		Message: message,
	}
}

// ValidateUser validates user input.
func ValidateUser(email, name string, age int) error {
	if email == "" {
		return NewValidationError("email", "cannot be empty")
	}
	if name == "" {
		return NewValidationError("name", "cannot be empty")
	}
	if age < 0 {
		return NewValidationError("age", "must be non-negative")
	}
	if age > 150 {
		return NewValidationError("age", "must be realistic")
	}
	return nil
}

func TestValidateUser(t *testing.T) {
	tests := []struct {
		name      string
		email     string
		userName  string
		age       int
		wantErr   bool
		wantField string
	}{
		{
			name:     "valid user",
			email:    "user@example.com",
			userName: "John Doe",
			age:      30,
			wantErr:  false,
		},
		{
			name:      "empty email",
			email:     "",
			userName:  "John Doe",
			age:       30,
			wantErr:   true,
			wantField: "email",
		},
		{
			name:      "empty name",
			email:     "user@example.com",
			userName:  "",
			age:       30,
			wantErr:   true,
			wantField: "name",
		},
		{
			name:      "negative age",
			email:     "user@example.com",
			userName:  "John Doe",
			age:       -1,
			wantErr:   true,
			wantField: "age",
		},
		{
			name:      "unrealistic age",
			email:     "user@example.com",
			userName:  "John Doe",
			age:       200,
			wantErr:   true,
			wantField: "age",
		},
	}

	for _, tt := range tests {
		t.Run(tt.name, func(t *testing.T) {
			err := ValidateUser(tt.email, tt.userName, tt.age)

			if tt.wantErr {
				if err == nil {
					t.Errorf("ValidateUser() error = nil; want error")
					return
				}

				var validationErr *ValidationError
				if !errors.As(err, &validationErr) {
					t.Errorf("error type = %T; want *ValidationError", err)
					return
				}

				if validationErr.Field != tt.wantField {
					t.Errorf("error field = %q; want %q", validationErr.Field, tt.wantField)
				}
				return
			}

			if err != nil {
				t.Errorf("ValidateUser() unexpected error: %v", err)
			}
		})
	}
}
```

Custom error types carry structured information that generic errors cannot. The `errors.As` function enables type assertions on errors, allowing you to extract that structured information safely.

### Error Wrapping and Context

Wrapping preserves root cause while adding layer-specific meaning. Without context, production debugging slows dramatically because operators cannot tell where failures originated.


Go 1.13 introduced error wrapping, enabling you to add context to errors as they propagate up the call stack while preserving the original error for inspection.

  

```go
// internal/errors/wrapping_test.go
package errors

import (
	"database/sql"
	"errors"
	"fmt"
	"testing"
)

var (
	ErrNotFound = errors.New("not found")
	ErrInternal = errors.New("internal error")
)

// Repository handles data access operations.
type Repository struct {
	db *sql.DB
}

// GetByID retrieves a user by ID, wrapping database errors with context.
func (r *Repository) GetByID(id int64) (*User, error) {
	query := `SELECT id, email, username FROM users WHERE id = $1`

	user := &User{}
	err := r.db.QueryRow(query, id).Scan(&user.ID, &user.Email, &user.Username)
	if err == sql.ErrNoRows {
		return nil, ErrNotFound
	}
	if err != nil {
		return nil, fmt.Errorf("get user by id: %w", err)
	}
	return user, nil
}

func TestErrorWrapping(t *testing.T) {
	// Simulate an error from lower layer
	lowLevelErr := errors.New("connection timeout")
	wrappedErr := fmt.Errorf("database query failed: %w", lowLevelErr)

	// errors.Is checks the entire error chain
	if !errors.Is(wrappedErr, lowLevelErr) {
		t.Error("errors.Is failed to find lowLevelErr in chain")
	}

	// errors.Unwrap retrieves the underlying error
	unwrapped := errors.Unwrap(wrappedErr)
	if unwrapped != lowLevelErr {
		t.Errorf("errors.Unwrap() = %v; want %v", unwrapped, lowLevelErr)
	}
}

func TestErrorIs(t *testing.T) {
	baseErr := ErrNotFound
	wrappedOnce := fmt.Errorf("layer 1: %w", baseErr)
	wrappedTwice := fmt.Errorf("layer 2: %w", wrappedOnce)

	if !errors.Is(wrappedTwice, ErrNotFound) {
		t.Error("errors.Is should find ErrNotFound through multiple layers")
	}

	if errors.Is(wrappedTwice, ErrInternal) {
		t.Error("errors.Is should not match different error")
	}
}
```

Error wrapping enables you to add context at each layer of your application while maintaining the ability to check for specific error types. This pattern is essential for debugging production issues where knowing which database query failed matters as much as knowing that a database error occurred.

  

## Section 3: Pointers and Memory

Understanding pointers is crucial for writing correct Go code. Pointers enable efficient passing of large structures, mutable function parameters, and optional values.

### Pointer Basics

Pointer semantics determine ownership and mutability. Misunderstanding these semantics leads to hidden coupling and side effects that make systems harder to reason about.


Pointers are powerful because they expose identity and mutation, but that power creates coupling between call sites. If mutation is not part of the API contract, prefer values to preserve local reasoning and reduce side effects.

When you do use pointers, make ownership and nil handling explicit in tests. Clear pointer semantics lead to fewer surprises during refactors and better long-term maintainability.


  

```go
// internal/pointers/basics_test.go
package pointers

import "testing"

func TestPointerBasics(t *testing.T) {
	t.Run("pointer to value", func(t *testing.T) {
		x := 42
		p := &x // & gets the address of x

		if *p != 42 {
			t.Errorf("*p = %d; want 42", *p)
		}

		*p = 100 // * dereferences the pointer
		if x != 100 {
			t.Errorf("x = %d; want 100", x)
		}
	})

	t.Run("nil pointer", func(t *testing.T) {
		var p *int
		if p != nil {
			t.Error("uninitialized pointer should be nil")
		}

		// Dereferencing nil pointer causes panic
		// *p = 42 // This would panic
	})

	t.Run("pointer equality", func(t *testing.T) {
		x := 42
		p1 := &x
		p2 := &x

		if p1 != p2 {
			t.Error("pointers to same variable should be equal")
		}

		y := 42
		p3 := &y
		if p1 == p3 {
			t.Error("pointers to different variables should not be equal")
		}
	})
}
```

### Value vs. Pointer Receivers

Receiver choice shapes API behavior, copying cost, and method-set compatibility. Choosing intentionally avoids subtle bugs and improves long-term maintainability.


Methods can have value receivers or pointer receivers. The choice affects whether the method can modify the receiver and how efficiently large structures are passed.

  

```go
// internal/pointers/receivers_test.go
package pointers

import "testing"

type Counter struct {
	count int
}

// Increment with value receiver - does NOT modify original
func (c Counter) IncrementValue() {
	c.count++
}

// Increment with pointer receiver - DOES modify original
func (c *Counter) IncrementPointer() {
	c.count++
}

func TestReceivers(t *testing.T) {
	t.Run("value receiver does not modify", func(t *testing.T) {
		c := Counter{count: 0}
		c.IncrementValue()

		if c.count != 0 {
			t.Errorf("count = %d; want 0 (value receiver should not modify)", c.count)
		}
	})

	t.Run("pointer receiver modifies", func(t *testing.T) {
		c := Counter{count: 0}
		c.IncrementPointer()

		if c.count != 1 {
			t.Errorf("count = %d; want 1 (pointer receiver should modify)", c.count)
		}
	})

	t.Run("pointer to struct can call both", func(t *testing.T) {
		c := &Counter{count: 0}
		c.IncrementValue() // Go automatically dereferences
		c.IncrementPointer()

		if c.count != 1 {
			t.Errorf("count = %d; want 1", c.count)
		}
	})
}
```

Use pointer receivers when:
- The method needs to modify the receiver
- The receiver is a large struct (copying would be expensive)
- Consistency matters (if some methods have pointer receivers, all should)

Use value receivers when:
- The receiver is a small struct
- The receiver is a map, function, or channel (these are already reference types)
- The method doesn't modify the receiver and immutability is desired

  

## Section 4: Slices and Maps

Slices and maps are Go's primary collection types. Understanding their behavior, especially their reference semantics, prevents bugs.

### Slice Fundamentals

Slice aliasing is one of the most common sources of surprising behavior in Go. Mastering capacity and backing-array semantics prevents data corruption and nondeterministic bugs.


The reliability risk with slices is hidden aliasing. Two slices can share the same backing array, so appending or mutating one value can unexpectedly change data used elsewhere. In long-lived services, these side effects create bugs that only appear under specific traffic patterns.

A durable rule is to make ownership explicit: if a function keeps data, copy it; if it only reads, document read-only expectations in the API. This small discipline dramatically reduces accidental coupling and protects code from subtle behavior shifts as features accumulate.


  

```go
// internal/collections/slices_test.go
package collections

import (
	"reflect"
	"testing"
)

func TestSliceBasics(t *testing.T) {
	t.Run("slice creation", func(t *testing.T) {
		// Various ways to create slices
		var s1 []int             // nil slice
		s2 := []int{}            // empty slice (not nil)
		s3 := make([]int, 5)     // length 5, capacity 5
		s4 := make([]int, 5, 10) // length 5, capacity 10

		if s1 != nil {
			t.Error("var s []int should create nil slice")
		}
		if s2 == nil {
			t.Error("s := []int{} should create non-nil slice")
		}
		if len(s3) != 5 || cap(s3) != 5 {
			t.Errorf("make([]int, 5) len=%d cap=%d; want len=5 cap=5", len(s3), cap(s3))
		}
		if len(s4) != 5 || cap(s4) != 10 {
			t.Errorf("make([]int, 5, 10) len=%d cap=%d; want len=5 cap=10", len(s4), cap(s4))
		}
	})

	t.Run("append behavior", func(t *testing.T) {
		s := []int{1, 2, 3}
		original := s

		s = append(s, 4)

		// If capacity was sufficient, original is modified
		// If capacity was insufficient, new array is allocated
		if cap(original) > 3 {
			if !reflect.DeepEqual(original, []int{1, 2, 3, 4}) {
				t.Error("append with sufficient capacity should modify original")
			}
		}
	})

	t.Run("slice sharing underlying array", func(t *testing.T) {
		s1 := []int{1, 2, 3, 4, 5}
		s2 := s1[1:4] // shares underlying array

		s2[0] = 999

		if s1[1] != 999 {
			t.Error("modifying slice should affect original")
		}
	})
}

func TestSliceOperations(t *testing.T) {
	t.Run("copy slice", func(t *testing.T) {
		src := []int{1, 2, 3, 4, 5}
		dst := make([]int, len(src))

		n := copy(dst, src)

		if n != 5 {
			t.Errorf("copy returned %d; want 5", n)
		}
		if !reflect.DeepEqual(dst, src) {
			t.Errorf("dst = %v; want %v", dst, src)
		}

		// Modify dst does not affect src
		dst[0] = 999
		if src[0] == 999 {
			t.Error("modifying copy should not affect original")
		}
	})

	t.Run("remove element", func(t *testing.T) {
		s := []int{1, 2, 3, 4, 5}
		index := 2 // remove element at index 2 (value 3)

		s = append(s[:index], s[index+1:]...)

		expected := []int{1, 2, 4, 5}
		if !reflect.DeepEqual(s, expected) {
			t.Errorf("s = %v; want %v", s, expected)
		}
	})
}
```

### Map Fundamentals

Maps are powerful but have important constraints around ordering, zero values, and concurrent access. Knowing these constraints is essential for correctness and reproducibility.


  

```go
// internal/collections/maps_test.go
package collections

import "testing"

func TestMapBasics(t *testing.T) {
	t.Run("map creation and access", func(t *testing.T) {
		m := make(map[string]int)
		m["one"] = 1
		m["two"] = 2

		if m["one"] != 1 {
			t.Errorf("m[\"one\"] = %d; want 1", m["one"])
		}

		// Accessing non-existent key returns zero value
		if m["three"] != 0 {
			t.Errorf("m[\"three\"] = %d; want 0", m["three"])
		}
	})

	t.Run("checking key existence", func(t *testing.T) {
		m := map[string]int{"one": 1}

		// Two-value form checks existence
		v, exists := m["one"]
		if !exists {
			t.Error("key \"one\" should exist")
		}
		if v != 1 {
			t.Errorf("m[\"one\"] = %d; want 1", v)
		}

		v, exists = m["two"]
		if exists {
			t.Error("key \"two\" should not exist")
		}
		if v != 0 {
			t.Errorf("non-existent key returned %d; want 0", v)
		}
	})

	t.Run("deleting keys", func(t *testing.T) {
		m := map[string]int{"one": 1, "two": 2}

		delete(m, "one")

		if _, exists := m["one"]; exists {
			t.Error("deleted key should not exist")
		}

		// Deleting non-existent key is safe
		delete(m, "three") // no-op, no panic
	})

	t.Run("map iteration order", func(t *testing.T) {
		m := map[string]int{"a": 1, "b": 2, "c": 3}

		// Map iteration order is randomized
		// Don't rely on any particular order
		count := 0
		for range m {
			count++
		}

		if count != 3 {
			t.Errorf("iteration count = %d; want 3", count)
		}
	})
}

func TestMapAsSet(t *testing.T) {
	// Maps can implement sets using map[T]bool or map[T]struct{}
	t.Run("set operations", func(t *testing.T) {
		set := make(map[string]struct{})

		// Add elements
		set["apple"] = struct{}{}
		set["banana"] = struct{}{}

		// Check membership
		if _, exists := set["apple"]; !exists {
			t.Error("apple should be in set")
		}

		if _, exists := set["orange"]; exists {
			t.Error("orange should not be in set")
		}

		// Remove element
		delete(set, "apple")
		if _, exists := set["apple"]; exists {
			t.Error("apple should be removed from set")
		}
	})
}
```

Maps are reference types—assigning a map to a new variable doesn't copy the map, both variables refer to the same underlying data structure. This behavior differs from slices, where the slice header is copied but the underlying array is shared.

  

## Section 5: Structs and Composition

Go doesn't have inheritance, but it supports composition through struct embedding. This design encourages building complex types from simpler ones.

  

```go
// internal/structs/composition_test.go
package structs

import "testing"

type Address struct {
	Street  string
	City    string
	ZipCode string
}

type Person struct {
	Name    string
	Age     int
	Address Address // Composition
}

type Employee struct {
	Person     // Embedding
	EmployeeID string
	Department string
}

func TestStructComposition(t *testing.T) {
	t.Run("nested struct", func(t *testing.T) {
		p := Person{
			Name: "John Doe",
			Age:  30,
			Address: Address{
				Street:  "123 Main St",
				City:    "Anytown",
				ZipCode: "12345",
			},
		}

		if p.Address.City != "Anytown" {
			t.Errorf("city = %q; want \"Anytown\"", p.Address.City)
		}
	})

	t.Run("embedded struct", func(t *testing.T) {
		e := Employee{
			Person: Person{
				Name: "Jane Smith",
				Age:  28,
				Address: Address{
					City: "Somewhere",
				},
			},
			EmployeeID: "E12345",
			Department: "Engineering",
		}

		// Embedded fields are promoted
		if e.Name != "Jane Smith" {
			t.Errorf("name = %q; want \"Jane Smith\"", e.Name)
		}

		// Can still access through Person
		if e.Person.Name != "Jane Smith" {
			t.Errorf("name = %q; want \"Jane Smith\"", e.Person.Name)
		}
	})
}
```

Struct embedding enables code reuse without inheritance's complexity. Methods defined on embedded types are promoted to the embedding type, creating a form of composition that feels like inheritance but maintains Go's simplicity.

## Best Practices Summary

This chapter established fundamental Go programming patterns that appear throughout production code:

- Use Go's type system to catch errors at compile time
- Define custom types for domain concepts to improve clarity and safety
- Implement interfaces to enable testability through dependency injection
- Handle errors explicitly, wrapping them with context as they propagate
- Choose pointer vs. value receivers based on whether methods modify state
- Understand slice and map reference semantics to avoid subtle bugs
- Favor composition over inheritance using struct embedding
- Test everything, especially error paths and edge cases around zero values

Chapter 3 builds on these fundamentals, advancing your testing capabilities with table-driven patterns, mocking strategies, and comprehensive coverage analysis.

## Exercises

### Exercise 2.1: Implement a Generic Stack

Generics practice here teaches how to express reusable behavior without sacrificing type safety. This is key to building maintainable libraries in modern Go.


Create a stack data structure with proper error handling:

```go
type Stack struct {
	items []interface{}
}

func (s *Stack) Push(item interface{})      {}
func (s *Stack) Pop() (interface{}, error)  {}
func (s *Stack) Peek() (interface{}, error) {}
func (s *Stack) Size() int                  {}
```

Write comprehensive tests covering:
- Push and pop operations
- Underflow (popping from empty stack)
- Multiple items
- Peek without removal

### Exercise 2.2: Build a Simple Cache

Caching introduces correctness tradeoffs around staleness, eviction, and invalidation. Practicing on a small cache builds intuition for larger system-level performance design.

This is also a practical bridge between fundamentals and production architecture. A small cache forces decisions about synchronization, API contracts, and failure semantics that mirror the same tradeoffs in distributed systems.


Implement a thread-safe cache with:
- Get and Set operations
- Size limit with LRU eviction
- Custom error types for cache miss, size exceeded
- Comprehensive tests

### Exercise 2.3: User Validation

Validation logic sits at trust boundaries and affects every downstream layer. Strong validation tests improve security, data quality, and error transparency simultaneously.


Create a user validation package with:
- Email format validation
- Password strength requirements
- Age range validation
- Custom ValidationError types
- Table-driven tests for all validation rules

## Further Reading

- Effective Go: https://go.dev/doc/effective_go
- Go Blog - Error Handling: https://go.dev/blog/error-handling-and-go
- Go Blog - Slices: https://go.dev/blog/slices-intro
- Go by Example: https://gobyexample.com

## Chapter Summary

This chapter explored Go's fundamental building blocks through the lens of test-driven development. You learned that Go's type system provides compile-time safety while tests verify runtime behavior. Error handling in Go is explicit and verbose, but this design makes failure paths visible and forces developers to address them. Pointers enable efficient memory usage and mutable parameters. Slices and maps provide powerful collection types with reference semantics that require careful understanding. Struct composition replaces inheritance, enabling code reuse without complexity.

The testing patterns established here—table-driven tests, error path verification, edge case coverage—scale to the advanced testing techniques in Chapter 3. Every fundamental concept was paired with tests demonstrating correct usage, reinforcing the test-everything mindset that produces production-ready software.

---

  

# Chapter 3: Advanced Testing Techniques

### Learning Objectives

- Master table-driven testing patterns for comprehensive test coverage
- Use subtests to organize complex test scenarios and enable selective test execution
- Implement test fixtures and proper setup/teardown patterns
- Apply mocking and dependency injection for isolated unit testing
- Utilize test coverage tools to identify untested code paths
- Write benchmark tests to verify performance characteristics
- Implement fuzz testing for input validation and edge case discovery
- Build confidence in complex systems through systematic testing approaches

### Introduction: From Basic Tests to Comprehensive Verification

Chapter 1 introduced the fundamental testing mindset, and Chapter 2 established Go's type system and data structures. This chapter elevates your testing capabilities to professional level, teaching patterns that handle complexity gracefully while ensuring thorough verification.

As software systems grow in complexity, so do the challenges of testing them. Real-world applications involve databases, networks, external APIs, concurrent operations, and intricate business logic. Testing these systems requires advanced techniques: organizing tests hierarchically with subtests, isolating units with mocks, discovering edge cases through fuzzing, and measuring coverage to identify gaps.

The techniques in this chapter are not optional embellishments—they are essential tools for production-quality code. Without subtests, complex scenarios become unwieldy single tests that fail for multiple reasons. Without mocks, unit tests become integration tests, slow and brittle. Without coverage analysis, you cannot know what your tests actually verify. Without fuzz testing, malicious or malformed inputs will find bugs you never anticipated.

Consider a banking application processing transactions. Tests must cover normal deposits and withdrawals, zero and negative amounts, insufficient funds, concurrent transactions from multiple accounts, network timeouts during processing, and database failures during commit. Managing this complexity requires every technique in this chapter working together.

  

## Section 1: Table-Driven Testing Mastery

Table-driven tests are Go's idiomatic approach to organizing multiple test cases. The pattern—a slice of test case structs iterated with `t.Run`—provides clarity, maintainability, and comprehensive coverage. This section explores advanced table-driven patterns for complex scenarios.

### Extended Table Patterns

Beyond basic input-expected-output tables, advanced patterns handle setup, teardown, and complex verification logic within test cases.

  

```go
// internal/banking/transaction_test.go
package banking

import (
	"testing"
	"time"
)

// TransactionType represents the kind of transaction.
type TransactionType string

const (
	TransactionDeposit    TransactionType = "deposit"
	TransactionWithdrawal TransactionType = "withdrawal"
	TransactionTransfer   TransactionType = "transfer"
)

// Transaction represents a single financial transaction.
type Transaction struct {
	ID        string
	AccountID string
	Type      TransactionType
	Amount    float64
	TargetID  string // For transfers
	Timestamp time.Time
	Status    TransactionStatus
}

// TransactionStatus represents the state of a transaction.
type TransactionStatus string

const (
	StatusPending   TransactionStatus = "pending"
	StatusCompleted TransactionStatus = "completed"
	StatusFailed    TransactionStatus = "failed"
)

// TestTableEntry defines a complete test case for transaction processing.
type TestTableEntry struct {
	name       string                                            // Subtest name
	setup      func(*testing.T) (*Account, *Transaction, func()) // Setup returns test objects and cleanup
	execute    func(*testing.T, *Account, *Transaction) error    // Operation under test
	verify     func(*testing.T, *Account, *Transaction, error)   // Verification logic
	skip       bool                                              // Conditional skip
	skipReason string                                            // Reason for skipping
}

// TestProcessTransaction runs comprehensive table-driven tests.
func TestProcessTransaction(t *testing.T) {
	table := []TestTableEntry{
		{
			name: "successful deposit",
			setup: func(t *testing.T) (*Account, *Transaction, func()) {
				account := &Account{
					ID:      "acc-001",
					Balance: 100.0,
					Status:  Active,
				}
				tx := &Transaction{
					ID:        "tx-001",
					AccountID: "acc-001",
					Type:      TransactionDeposit,
					Amount:    50.0,
					Timestamp: time.Now(),
				}
				cleanup := func() {}
				return account, tx, cleanup
			},
			execute: func(t *testing.T, account *Account, tx *Transaction) error {
				return ProcessDeposit(account, tx)
			},
			verify: func(t *testing.T, account *Account, tx *Transaction, err error) {
				if err != nil {
					t.Errorf("ProcessDeposit() error = %v; want nil", err)
				}
				if account.Balance != 150.0 {
					t.Errorf("Balance = %.2f; want 150.00", account.Balance)
				}
				if tx.Status != StatusCompleted {
					t.Errorf("Status = %q; want %q", tx.Status, StatusCompleted)
				}
			},
		},
		{
			name: "withdrawal with insufficient funds",
			setup: func(t *testing.T) (*Account, *Transaction, func()) {
				account := &Account{
					ID:      "acc-002",
					Balance: 50.0,
					Status:  Active,
				}
				tx := &Transaction{
					ID:        "tx-002",
					AccountID: "acc-002",
					Type:      TransactionWithdrawal,
					Amount:    100.0,
					Timestamp: time.Now(),
				}
				return account, tx, func() {}
			},
			execute: func(t *testing.T, account *Account, tx *Transaction) error {
				return ProcessWithdrawal(account, tx)
			},
			verify: func(t *testing.T, account *Account, tx *Transaction, err error) {
				if err != ErrInsufficientFunds {
					t.Errorf("error = %v; want %v", err, ErrInsufficientFunds)
				}
				if account.Balance != 50.0 {
					t.Errorf("Balance = %.2f; want 50.00 (unchanged)", account.Balance)
				}
				if tx.Status != StatusFailed {
					t.Errorf("Status = %q; want %q", tx.Status, StatusFailed)
				}
			},
		},
		{
			name: "deposit to frozen account",
			setup: func(t *testing.T) (*Account, *Transaction, func()) {
				account := &Account{
					ID:      "acc-003",
					Balance: 100.0,
					Status:  Frozen,
				}
				tx := &Transaction{
					ID:        "tx-003",
					AccountID: "acc-003",
					Type:      TransactionDeposit,
					Amount:    50.0,
				}
				return account, tx, func() {}
			},
			execute: func(t *testing.T, account *Account, tx *Transaction) error {
				return ProcessDeposit(account, tx)
			},
			verify: func(t *testing.T, account *Account, tx *Transaction, err error) {
				if err != ErrAccountFrozen {
					t.Errorf("error = %v; want %v", err, ErrAccountFrozen)
				}
			},
		},
	}

	for _, tt := range table {
		t.Run(tt.name, func(t *testing.T) {
			if tt.skip {
				t.Skip(tt.skipReason)
			}

			account, tx, cleanup := tt.setup(t)
			defer cleanup()

			err := tt.execute(t, account, tx)
			tt.verify(t, account, tx, err)
		})
	}
}
```

This advanced pattern separates setup, execution, and verification into distinct functions within each test case. This separation makes tests more readable and enables reusing verification logic across similar test cases.

### Dynamic Table Generation

Sometimes test cases are generated dynamically based on data or configuration rather than being statically defined.

  

```go
// internal/validator/dynamic_test.go
package validator

import (
	"strings"
	"testing"
)

func TestPasswordStrength(t *testing.T) {
	// Generate test cases for various password lengths
	var tests []struct {
		name     string
		password string
		wantErr  error
	}

	// Too short passwords
	for length := 1; length < 8; length++ {
		tests = append(tests, struct {
			name     string
			password string
			wantErr  error
		}{
			name:     fmt.Sprintf("too short - %d chars", length),
			password: strings.Repeat("a", length),
			wantErr:  ErrPasswordTooShort,
		})
	}

	// Valid length passwords
	for length := 8; length <= 12; length++ {
		tests = append(tests, struct {
			name     string
			password string
			wantErr  error
		}{
			name:     fmt.Sprintf("valid length - %d chars", length),
			password: createStrongPassword(length),
			wantErr:  nil,
		})
	}

	for _, tt := range tests {
		t.Run(tt.name, func(t *testing.T) {
			err := ValidatePasswordStrength(tt.password)
			if err != tt.wantErr {
				t.Errorf("ValidatePasswordStrength() error = %v; want %v", err, tt.wantErr)
			}
		})
	}
}

func createStrongPassword(length int) string {
	// Generate password meeting strength requirements
	return "Aa1!" + strings.Repeat("x", length-4)
}
```

Dynamic table generation enables testing ranges of values, edge cases around boundaries, and data-driven test scenarios without manually writing hundreds of test cases.

  

## Section 2: Subtests and Test Organization

Subtests enable hierarchical organization of test cases, making test output more readable and enabling selective test execution.

### Hierarchical Test Organization

Hierarchical subtests give you precise failure localization and make matrix-style behavior testing tractable. Use clear naming conventions so CI output is readable and reruns can target only failing branches quickly.


  

```go
// internal/api/user_test.go
package api

import (
	"net/http"
	"net/http/httptest"
	"testing"
)

func TestUserAPI(t *testing.T) {
	t.Run("CreateUser", func(t *testing.T) {
		t.Run("valid input", func(t *testing.T) {
			req := httptest.NewRequest(http.MethodPost, "/users",
				strings.NewReader(`{"email":"user@example.com","name":"John"}`))

			rr := httptest.NewRecorder()
			handler := NewUserHandler()
			handler.ServeHTTP(rr, req)

			if rr.Code != http.StatusCreated {
				t.Errorf("Status = %d; want %d", rr.Code, http.StatusCreated)
			}
		})

		t.Run("invalid email", func(t *testing.T) {
			req := httptest.NewRequest(http.MethodPost, "/users",
				strings.NewReader(`{"email":"invalid","name":"John"}`))

			rr := httptest.NewRecorder()
			handler := NewUserHandler()
			handler.ServeHTTP(rr, req)

			if rr.Code != http.StatusBadRequest {
				t.Errorf("Status = %d; want %d", rr.Code, http.StatusBadRequest)
			}
		})

		t.Run("missing required fields", func(t *testing.T) {
			tests := []struct {
				name string
				body string
			}{
				{"missing email", `{"name":"John"}`},
				{"missing name", `{"email":"user@example.com"}`},
				{"empty body", `{}`},
			}

			for _, tt := range tests {
				t.Run(tt.name, func(t *testing.T) {
					req := httptest.NewRequest(http.MethodPost, "/users",
						strings.NewReader(tt.body))

					rr := httptest.NewRecorder()
					handler := NewUserHandler()
					handler.ServeHTTP(rr, req)

					if rr.Code != http.StatusBadRequest {
						t.Errorf("Status = %d; want %d", rr.Code, http.StatusBadRequest)
					}
				})
			}
		})
	})

	t.Run("GetUser", func(t *testing.T) {
		t.Run("existing user", func(t *testing.T) {
			// Test implementation
		})

		t.Run("non-existent user", func(t *testing.T) {
			// Test implementation
		})
	})

	t.Run("UpdateUser", func(t *testing.T) {
		// Nested subtests for update scenarios
	})
}
```

This hierarchical organization produces readable test output:

```
=== RUN   TestUserAPI
=== RUN   TestUserAPI/CreateUser
=== RUN   TestUserAPI/CreateUser/valid_input
=== RUN   TestUserAPI/CreateUser/invalid_email
=== RUN   TestUserAPI/CreateUser/missing_required_fields
=== RUN   TestUserAPI/CreateUser/missing_required_fields/missing_email
=== RUN   TestUserAPI/CreateUser/missing_required_fields/missing_name
=== RUN   TestUserAPI/GetUser
--- PASS: TestUserAPI (0.02s)
```

### Parallel Test Execution

Subtests can run in parallel, dramatically reducing test suite execution time for I/O-bound tests.

  

```go
// internal/api/parallel_test.go
package api

import (
	"testing"
	"time"
)

func TestParallelRequests(t *testing.T) {
	tests := []struct {
		name     string
		endpoint string
		method   string
	}{
		{"get users", "/users", "GET"},
		{"get posts", "/posts", "GET"},
		{"get comments", "/comments", "GET"},
	}

	for _, tt := range tests {
		tt := tt // Capture range variable
		t.Run(tt.name, func(t *testing.T) {
			t.Parallel() // Mark test as parallel

			// Simulate slow external API call
			time.Sleep(100 * time.Millisecond)

			// Test logic here
		})
	}
}
```

The `t.Parallel()` call marks a subtest for parallel execution. When all tests in a parent are parallel, they run concurrently. This can reduce a 3-second sequential test suite to under 1 second.

  

## Section 3: Test Fixtures and Setup/Teardown

Test fixtures provide consistent starting states for tests. Proper setup and teardown ensure tests don't interfere with each other.

### Setup and Teardown Patterns

Setup and teardown code should minimize shared mutable state and use t.Cleanup to guarantee release paths. Deterministic lifecycle handling prevents flaky tests and keeps suites fast enough to run continuously in CI.


  

```go
// internal/database/repository_test.go
package database

import (
	"database/sql"
	_ "github.com/lib/pq"
	"testing"
)

func TestUserRepository(t *testing.T) {
	// Setup: Create test database connection
	db, err := sql.Open("postgres", "postgres://localhost/testdb")
	if err != nil {
		t.Fatalf("Failed to connect to test database: %v", err)
	}
	defer db.Close() // Teardown

	// Setup: Clean database state
	if err := cleanDatabase(db); err != nil {
		t.Fatalf("Failed to clean database: %v", err)
	}

	// Create repository under test
	repo := NewUserRepository(db)

	t.Run("Create", func(t *testing.T) {
		// Per-test setup
		t.Cleanup(func() {
			cleanDatabase(db)
		})

		user := &User{
			Email: "test@example.com",
			Name:  "Test User",
		}

		err := repo.Create(user)
		if err != nil {
			t.Errorf("Create() error = %v; want nil", err)
		}
	})

	t.Run("Get", func(t *testing.T) {
		// Setup: Insert test data
		testUser := &User{
			Email: "get@example.com",
			Name:  "Get Test",
		}
		if err := repo.Create(testUser); err != nil {
			t.Fatalf("Setup failed: %v", err)
		}

		// Teardown for this specific test
		t.Cleanup(func() {
			cleanDatabase(db)
		})

		// Test execution
		retrieved, err := repo.Get(testUser.ID)
		if err != nil {
			t.Errorf("Get() error = %v; want nil", err)
		}
		if retrieved.Email != testUser.Email {
			t.Errorf("Email = %q; want %q", retrieved.Email, testUser.Email)
		}
	})
}

func cleanDatabase(db *sql.DB) error {
	_, err := db.Exec("TRUNCATE users CASCADE")
	return err
}
```

The `t.Cleanup()` function registers cleanup functions that run after the test completes, regardless of whether the test passes or fails. This ensures resources are properly released and state is cleaned up.

### Test Helper Functions

Extract common setup and assertion logic into helper functions to reduce boilerplate.

  

```go
// internal/testhelpers/assertions.go
package testhelpers

import (
	"reflect"
	"testing"
)

// AssertEqual fails the test if got != want.
func AssertEqual(t *testing.T, got, want interface{}) {
	t.Helper() // Marks this function as a test helper

	if !reflect.DeepEqual(got, want) {
		t.Errorf("got %v; want %v", got, want)
	}
}

// AssertNoError fails the test if err != nil.
func AssertNoError(t *testing.T, err error) {
	t.Helper()

	if err != nil {
		t.Errorf("unexpected error: %v", err)
	}
}

// AssertError fails the test if err == nil.
func AssertError(t *testing.T, err error) {
	t.Helper()

	if err == nil {
		t.Error("expected error; got nil")
	}
}

// CreateTestUser creates a user for testing.
func CreateTestUser(t *testing.T, repo Repository) *User {
	t.Helper()

	user := &User{
		Email: "test@example.com",
		Name:  "Test User",
	}

	err := repo.Create(user)
	if err != nil {
		t.Fatalf("CreateTestUser() failed: %v", err)
	}

	return user
}
```

The `t.Helper()` call tells the testing framework that this function is a helper, so failure messages report the line number of the calling test, not the helper function itself.

  

## Section 4: Mocking and Dependency Injection

Mocking isolates the code under test from external dependencies, making tests fast, reliable, and focused.

### Interface-Based Mocking

Interface-based mocking works best when interfaces are small and defined by the consuming package. This avoids creating broad, framework-like abstractions that leak implementation details. Narrow interfaces keep tests focused on behavior and make dependencies easier to swap over time.


  

```go
// internal/services/user_service_test.go
package services

import (
	"errors"
	"testing"
)

// EmailService defines email operations.
type EmailService interface {
	SendWelcomeEmail(to, name string) error
}

// MockEmailService implements EmailService for testing.
type MockEmailService struct {
	sendCalled bool
	sendTo     string
	sendName   string
	sendError  error
}

func (m *MockEmailService) SendWelcomeEmail(to, name string) error {
	m.sendCalled = true
	m.sendTo = to
	m.sendName = name
	return m.sendError
}

// UserService handles user operations.
type UserService struct {
	repo         Repository
	emailService EmailService
}

func NewUserService(repo Repository, emailService EmailService) *UserService {
	return &UserService{
		repo:         repo,
		emailService: emailService,
	}
}

func (s *UserService) RegisterUser(email, name string) error {
	// Create user
	user := &User{Email: email, Name: name}
	if err := s.repo.Create(user); err != nil {
		return err
	}

	// Send welcome email
	if err := s.emailService.SendWelcomeEmail(email, name); err != nil {
		// Log error but don't fail registration
		log.Printf("Failed to send welcome email: %v", err)
	}

	return nil
}

func TestUserServiceRegisterUser(t *testing.T) {
	t.Run("successful registration with email", func(t *testing.T) {
		mockRepo := NewMockRepository()
		mockEmail := &MockEmailService{}

		service := NewUserService(mockRepo, mockEmail)
		err := service.RegisterUser("user@example.com", "John Doe")

		if err != nil {
			t.Errorf("RegisterUser() error = %v; want nil", err)
		}

		// Verify email was sent
		if !mockEmail.sendCalled {
			t.Error("SendWelcomeEmail was not called")
		}
		if mockEmail.sendTo != "user@example.com" {
			t.Errorf("email sent to %q; want %q", mockEmail.sendTo, "user@example.com")
		}
	})

	t.Run("registration succeeds even if email fails", func(t *testing.T) {
		mockRepo := NewMockRepository()
		mockEmail := &MockEmailService{
			sendError: errors.New("SMTP connection failed"),
		}

		service := NewUserService(mockRepo, mockEmail)
		err := service.RegisterUser("user@example.com", "John Doe")

		// Registration should succeed despite email failure
		if err != nil {
			t.Errorf("RegisterUser() error = %v; want nil", err)
		}

		// Verify user was created
		if len(mockRepo.users) != 1 {
			t.Errorf("users created = %d; want 1", len(mockRepo.users))
		}
	})
}
```

This pattern enables testing business logic without sending actual emails, connecting to real databases, or making HTTP requests. Tests run in milliseconds instead of seconds and don't depend on external services.

### Table-Driven Tests with Mocks

Combine table-driven patterns with mocking for comprehensive coverage of different scenarios.

  

```go
func TestNotificationService(t *testing.T) {
	tests := []struct {
		name          string
		setupMock     func(*MockEmailService, *MockSMSService)
		userEmail     string
		userPhone     string
		message       string
		wantEmailSent bool
		wantSMSSent   bool
		wantErr       bool
	}{
		{
			name: "send both email and SMS",
			setupMock: func(email *MockEmailService, sms *MockSMSService) {
				// Both services succeed
			},
			userEmail:     "user@example.com",
			userPhone:     "+1234567890",
			message:       "Test notification",
			wantEmailSent: true,
			wantSMSSent:   true,
			wantErr:       false,
		},
		{
			name: "email fails but SMS succeeds",
			setupMock: func(email *MockEmailService, sms *MockSMSService) {
				email.sendError = errors.New("SMTP error")
			},
			userEmail:     "user@example.com",
			userPhone:     "+1234567890",
			message:       "Test notification",
			wantEmailSent: true,
			wantSMSSent:   true,
			wantErr:       true,
		},
		{
			name:          "no phone number",
			setupMock:     func(email *MockEmailService, sms *MockSMSService) {},
			userEmail:     "user@example.com",
			userPhone:     "",
			message:       "Test notification",
			wantEmailSent: true,
			wantSMSSent:   false,
			wantErr:       false,
		},
	}

	for _, tt := range tests {
		t.Run(tt.name, func(t *testing.T) {
			mockEmail := &MockEmailService{}
			mockSMS := &MockSMSService{}
			tt.setupMock(mockEmail, mockSMS)

			service := NewNotificationService(mockEmail, mockSMS)
			err := service.SendNotification(tt.userEmail, tt.userPhone, tt.message)

			if (err != nil) != tt.wantErr {
				t.Errorf("SendNotification() error = %v; wantErr %v", err, tt.wantErr)
			}

			if mockEmail.sendCalled != tt.wantEmailSent {
				t.Errorf("email sent = %v; want %v", mockEmail.sendCalled, tt.wantEmailSent)
			}

			if mockSMS.sendCalled != tt.wantSMSSent {
				t.Errorf("SMS sent = %v; want %v", mockSMS.sendCalled, tt.wantSMSSent)
			}
		})
	}
}
```

  

## Section 5: Test Coverage Analysis

Coverage metrics identify untested code paths. While 100% coverage doesn't guarantee correctness, understanding what your tests cover guides testing efforts.

### Generating Coverage Reports

```bash
# Generate coverage profile
go test -coverprofile=coverage.out ./...

# View coverage in terminal
go tool cover -func=coverage.out

# Generate HTML coverage report
go tool cover -html=coverage.out -o coverage.html
```

The HTML report shows exactly which lines are covered and which are not, with color coding for quick visual assessment.

### Coverage-Guided Test Writing

```go
// internal/calculator/calculator.go
package calculator

func Calculate(op string, a, b float64) (float64, error) {
	switch op {
	case "+":
		return a + b, nil
	case "-":
		return a - b, nil
	case "*":
		return a * b, nil
	case "/":
		if b == 0 {
			return 0, ErrDivisionByZero
		}
		return a / b, nil
	default:
		return 0, ErrInvalidOperation
	}
}
```

Running coverage on incomplete tests reveals gaps:

```
internal/calculator/calculator.go:15: Calculate    75.0%
```

The coverage report shows that the division by zero and invalid operation cases aren't tested. Add test cases to reach 100%:

```go
func TestCalculate(t *testing.T) {
	tests := []struct {
		name    string
		op      string
		a       float64
		b       float64
		want    float64
		wantErr error
	}{
		// ... existing cases ...
		{
			name:    "division by zero",
			op:      "/",
			a:       10,
			b:       0,
			want:    0,
			wantErr: ErrDivisionByZero,
		},
		{
			name:    "invalid operation",
			op:      "%",
			a:       10,
			b:       3,
			want:    0,
			wantErr: ErrInvalidOperation,
		},
	}
	// ... test execution ...
}
```

Now coverage reports 100%, and you've verified error handling paths.

  

## Section 6: Benchmark Testing

Benchmarks measure performance, enabling data-driven optimization decisions and catching performance regressions.

### Writing Benchmarks

Benchmark results are only useful when inputs represent realistic workloads and comparisons are reproducible. Track baseline numbers in CI artifacts and investigate regressions as part of normal review, not only during performance incidents.

  

```go
// internal/search/search_test.go
package search

import (
	"testing"
)

func BenchmarkLinearSearch(b *testing.B) {
	data := generateTestData(10000)
	target := data[5000]

	b.ResetTimer()
	for i := 0; i < b.N; i++ {
		LinearSearch(data, target)
	}
}

func BenchmarkBinarySearch(b *testing.B) {
	data := generateSortedTestData(10000)
	target := data[5000]

	b.ResetTimer()
	for i := 0; i < b.N; i++ {
		BinarySearch(data, target)
	}
}

func BenchmarkSearchVariousSizes(b *testing.B) {
	sizes := []int{100, 1000, 10000, 100000}

	for _, size := range sizes {
		b.Run(fmt.Sprintf("size=%d", size), func(b *testing.B) {
			data := generateTestData(size)
			target := data[size/2]

			b.ResetTimer()
			for i := 0; i < b.N; i++ {
				LinearSearch(data, target)
			}
		})
	}
}
```

Running benchmarks:

```bash
$ go test -bench=. -benchmem
BenchmarkLinearSearch-8           50000    25000 ns/op      0 B/op    0 allocs/op
BenchmarkBinarySearch-8         5000000      250 ns/op      0 B/op    0 allocs/op
BenchmarkSearchVariousSizes/size=100-8     1000000    1200 ns/op
BenchmarkSearchVariousSizes/size=1000-8     100000   12000 ns/op
```

The `-benchmem` flag adds memory allocation statistics, revealing hidden allocations that affect performance.

  

## Section 7: Fuzz Testing

Fuzz testing automatically generates inputs to discover edge cases, crashes, and security vulnerabilities that manual testing misses.

### Basic Fuzz Testing

Fuzzing is most effective when seed corpora include boundary values and previously observed failure inputs. Treat discovered crashing inputs as regression assets and commit them so the same bug class stays fixed permanently.


```go
// internal/parser/url_test.go
package parser

import (
	"testing"
)

func FuzzParseURL(f *testing.F) {
	// Seed corpus with known inputs
	f.Add("https://example.com")
	f.Add("http://example.com:8080/path?query=value")
	f.Add("ftp://ftp.example.com")

	f.Fuzz(func(t *testing.T, url string) {
		// The fuzzer generates random strings
		// Your code should handle them without panicking
		parsed, err := ParseURL(url)

		if err != nil {
			// Invalid input is okay, should return error
			return
		}

		// If parsing succeeded, verify invariants
		if parsed.Scheme == "" {
			t.Error("scheme should not be empty for valid URL")
		}
	})
}
```

Run fuzz tests:

```bash
$ go test -fuzz=FuzzParseURL -fuzztime=30s
```

The fuzzer explores different input patterns, looking for crashes, panics, or assertion failures. It saves failing inputs to `testdata/fuzz/` for regression testing.

### Fuzz Testing for Validation

```go
func FuzzValidateEmail(f *testing.F) {
	// Seed with valid and invalid examples
	f.Add("user@example.com")
	f.Add("invalid@@example.com")
	f.Add("user@")
	f.Add("@example.com")

	f.Fuzz(func(t *testing.T, email string) {
		err := ValidateEmail(email)

		// Fuzzer should never cause panic
		// Both error and success are valid outcomes
		_ = err
	})
}
```

Fuzz testing excels at finding edge cases in parsing, validation, and serialization code—exactly where security vulnerabilities often hide.

## Best Practices Summary

This chapter advanced your testing capabilities to production level:

- Use table-driven tests to organize test cases clearly and comprehensively
- Leverage subtests for hierarchical organization and parallel execution
- Implement proper setup/teardown with t.Cleanup() to ensure clean state
- Apply mocking through interfaces for isolated, fast unit tests
- Generate and analyze coverage reports to identify untested code paths
- Write benchmarks to make performance decisions based on data
- Use fuzz testing to discover edge cases automatically
- Create test helpers with t.Helper() for reusable assertions

These patterns scale from small functions to complex systems. As your codebase grows, these techniques remain effective, enabling comprehensive verification without unmaintainable test suites.

## Exercises

### Exercise 3.1: Complete Repository Test Suite

Implement comprehensive tests for a user repository:

```go
type UserRepository interface {
	Create(user *User) error
	GetByID(id int64) (*User, error)
	GetByEmail(email string) (*User, error)
	Update(user *User) error
	Delete(id int64) error
}
```

Include:
- Table-driven tests for all operations
- Mock repository implementation
- Setup/teardown for database state
- Error path coverage
- Coverage verification

### Exercise 3.2: API Handler Test Suite

Write tests for HTTP handlers:

```go
type UserHandler struct {
	service UserService
}

func (h *UserHandler) CreateUser(w http.ResponseWriter, r *http.Request)
func (h *UserHandler) GetUser(w http.ResponseWriter, r *http.Request)
func (h *UserHandler) UpdateUser(w http.ResponseWriter, r *http.Request)
```

Include:
- Subtests for each endpoint
- Valid and invalid input testing
- Status code verification
- Response body assertions
- Mock service layer

### Exercise 3.3: Benchmark Comparison

Implement and benchmark different algorithms:

```go
func Sort1(data []int) []int
func Sort2(data []int) []int
func Sort3(data []int) []int
```

Include:
- Benchmarks for various data sizes
- Memory allocation analysis
- Comparison of approaches

## Further Reading

- Go Testing Package: https://pkg.go.dev/testing
- Go Blog - Table Driven Tests: https://go.dev/blog/subtests
- Go Blog - Fuzzing: https://go.dev/blog/fuzz-beta
- Testify Package: https://github.com/stretchr/testify

## Chapter Summary

This chapter elevated your testing from basic verification to comprehensive quality assurance. Table-driven tests provide clear, maintainable organization for complex test scenarios. Subtests enable hierarchical structure and parallel execution. Test fixtures and setup/teardown ensure consistent state. Mocking through interfaces isolates units for fast, focused tests. Coverage analysis identifies gaps in verification. Benchmarks enable performance optimization based on data rather than intuition. Fuzz testing discovers edge cases that manual testing would never find.

These techniques compose into powerful testing strategies. A complex API handler test suite might use table-driven tests organized with subtests, mocking external dependencies, measuring coverage to ensure completeness, and fuzzing input validation. Each technique strengthens the others.

Chapter 4 builds on this testing foundation, applying security-first development principles where comprehensive testing becomes essential for verifying that security measures actually work.
 
---

  

# Chapter 4: Security-First Development

## Learning Objectives

- Understand the OWASP Top 10 vulnerabilities and their impact on software security
- Implement comprehensive input validation and sanitization to prevent injection attacks
- Secure password handling using bcrypt with proper salt and work factor configuration
- Design and implement JWT-based authentication with refresh tokens
- Protect against Cross-Site Scripting (XSS) and Cross-Site Request Forgery (CSRF)
- Write security-focused tests that verify protection mechanisms
- Apply defense-in-depth principles to create robust, secure applications
- Integrate security testing into your development workflow

## Introduction: Security as a First-Class Concern

Security is not a feature to be added after development—it must be foundational to how you design and write code. The cost of security vulnerabilities is staggering: data breaches average millions in remediation, regulatory fines can devastate organizations, and reputational damage can take years to recover from. Yet security flaws are often simple to prevent with proper attention during development.

This chapter adopts a security-first approach to software development, where every code decision considers security implications. You will learn to think like an attacker, anticipating how malicious inputs and actions could exploit your code. More importantly, you will learn to implement defenses that stop these attacks, verified through comprehensive testing.

The techniques in this chapter protect against the OWASP Top 10—the most critical web application security risks. These include injection attacks, broken authentication, sensitive data exposure, XML external entities, broken access control, security misconfigurations, Cross-Site Scripting, insecure deserialization, using components with known vulnerabilities, and insufficient logging and monitoring. Each vulnerability type includes practical defenses implemented in Go with corresponding tests.

Go's type system and standard library provide strong foundations for secure coding. The language's memory safety features eliminate entire categories of vulnerabilities like buffer overflows and use-after-free bugs. Combined with proper security libraries and disciplined input handling, Go enables the development of secure systems that resist common attacks.

  

## Section 1: Input Validation and Sanitization

Every piece of external data is potentially malicious. Input validation ensures that only expected, safe data enters your system. Sanitization transforms potentially dangerous data into safe forms. Together, they form the first line of defense against injection attacks.

### Comprehensive Input Validation

Comprehensive validation should define accepted shape, constraints, and normalization rules at domain boundaries. Rejecting invalid input early keeps downstream logic simpler and prevents persistence of ambiguous states.


  

```go
// internal/security/validation_test.go
package security

import (
	"regexp"
	"testing"
)

// ValidationResult represents the outcome of validation.
type ValidationResult struct {
	Valid  bool
	Errors []string
}

// UserRegistrationInput represents registration data.
type UserRegistrationInput struct {
	Email    string
	Username string
	Password string
	Age      int
}

var (
	emailRegex    = regexp.MustCompile(`^[a-zA-Z0-9._%+-]+@[a-zA-Z0-9.-]+\.[a-zA-Z]{2,}$`)
	usernameRegex = regexp.MustCompile(`^[a-zA-Z0-9_-]{3,20}$`)
)

// ValidateRegistrationInput validates user registration data.
func ValidateRegistrationInput(input UserRegistrationInput) *ValidationResult {
	result := &ValidationResult{Valid: true, Errors: []string{}}

	// Email validation
	if input.Email == "" {
		result.Valid = false
		result.Errors = append(result.Errors, "email is required")
	} else if len(input.Email) > 254 {
		result.Valid = false
		result.Errors = append(result.Errors, "email exceeds maximum length")
	} else if !emailRegex.MatchString(input.Email) {
		result.Valid = false
		result.Errors = append(result.Errors, "email format is invalid")
	}

	// Username validation
	if input.Username == "" {
		result.Valid = false
		result.Errors = append(result.Errors, "username is required")
	} else if !usernameRegex.MatchString(input.Username) {
		result.Valid = false
		result.Errors = append(result.Errors, "username must be 3-20 alphanumeric characters")
	}

	// Password validation
	if err := ValidatePasswordStrength(input.Password); err != nil {
		result.Valid = false
		result.Errors = append(result.Errors, err.Error())
	}

	// Age validation
	if input.Age < 13 {
		result.Valid = false
		result.Errors = append(result.Errors, "must be at least 13 years old")
	} else if input.Age > 150 {
		result.Valid = false
		result.Errors = append(result.Errors, "age must be realistic")
	}

	return result
}

func TestValidateRegistrationInput(t *testing.T) {
	tests := []struct {
		name       string
		input      UserRegistrationInput
		wantValid  bool
		wantErrors int
	}{
		{
			name: "valid input",
			input: UserRegistrationInput{
				Email:    "user@example.com",
				Username: "johndoe",
				Password: "SecureP@ss123",
				Age:      25,
			},
			wantValid:  true,
			wantErrors: 0,
		},
		{
			name: "empty email",
			input: UserRegistrationInput{
				Email:    "",
				Username: "johndoe",
				Password: "SecureP@ss123",
				Age:      25,
			},
			wantValid:  false,
			wantErrors: 1,
		},
		{
			name: "invalid email format",
			input: UserRegistrationInput{
				Email:    "not-an-email",
				Username: "johndoe",
				Password: "SecureP@ss123",
				Age:      25,
			},
			wantValid:  false,
			wantErrors: 1,
		},
		{
			name: "username too short",
			input: UserRegistrationInput{
				Email:    "user@example.com",
				Username: "ab",
				Password: "SecureP@ss123",
				Age:      25,
			},
			wantValid:  false,
			wantErrors: 1,
		},
		{
			name: "username with invalid characters",
			input: UserRegistrationInput{
				Email:    "user@example.com",
				Username: "john@doe",
				Password: "SecureP@ss123",
				Age:      25,
			},
			wantValid:  false,
			wantErrors: 1,
		},
		{
			name: "weak password",
			input: UserRegistrationInput{
				Email:    "user@example.com",
				Username: "johndoe",
				Password: "weak",
				Age:      25,
			},
			wantValid:  false,
			wantErrors: 1,
		},
		{
			name: "age too young",
			input: UserRegistrationInput{
				Email:    "user@example.com",
				Username: "johndoe",
				Password: "SecureP@ss123",
				Age:      10,
			},
			wantValid:  false,
			wantErrors: 1,
		},
		{
			name: "multiple validation errors",
			input: UserRegistrationInput{
				Email:    "",
				Username: "a",
				Password: "weak",
				Age:      10,
			},
			wantValid:  false,
			wantErrors: 4,
		},
	}

	for _, tt := range tests {
		t.Run(tt.name, func(t *testing.T) {
			result := ValidateRegistrationInput(tt.input)

			if result.Valid != tt.wantValid {
				t.Errorf("Valid = %v; want %v", result.Valid, tt.wantValid)
			}

			if len(result.Errors) != tt.wantErrors {
				t.Errorf("Error count = %d; want %d. Errors: %v",
					len(result.Errors), tt.wantErrors, result.Errors)
			}
		})
	}
}
```

This validation approach uses allowlists (defining what is permitted) rather than denylists (defining what is forbidden). Allowlists are inherently more secure because they reject unknown inputs by default, whereas denylists can be bypassed by creative attackers finding inputs you didn't think to forbid.

### Password Strength Validation

Strength validation should balance security and usability with clear, deterministic rules. Keep enforcement on the server even if the client also validates, because client checks can be bypassed.


Strong passwords protect user accounts from brute-force attacks and credential stuffing. Password validation should enforce complexity requirements without being so strict that users resort to writing passwords down.

  

```go
// internal/security/password_test.go
package security

import (
	"errors"
	"testing"
	"unicode"
)

var (
	ErrPasswordTooShort      = errors.New("password must be at least 8 characters (8+ bytes)")
	ErrPasswordTooLong       = errors.New("password must not exceed 72 bytes (bcrypt limit)")
	ErrPasswordNoUppercase   = errors.New("password must contain uppercase letter")
	ErrPasswordNoLowercase   = errors.New("password must contain lowercase letter")
	ErrPasswordNoDigit       = errors.New("password must contain digit")
	ErrPasswordNoSpecialChar = errors.New("password must contain special character")
)

// ValidatePasswordStrength checks password strength requirements.
func ValidatePasswordStrength(password string) error {
	if len(password) < 8 {
		return ErrPasswordTooShort
	}
	if len(password) > 72 {
		// bcrypt has a 72-byte input limit
		return ErrPasswordTooLong
	}

	var (
		hasUpper   bool
		hasLower   bool
		hasDigit   bool
		hasSpecial bool
	)

	for _, char := range password {
		switch {
		case unicode.IsUpper(char):
			hasUpper = true
		case unicode.IsLower(char):
			hasLower = true
		case unicode.IsDigit(char):
			hasDigit = true
		case unicode.IsPunct(char) || unicode.IsSymbol(char):
			hasSpecial = true
		}
	}

	if !hasUpper {
		return ErrPasswordNoUppercase
	}
	if !hasLower {
		return ErrPasswordNoLowercase
	}
	if !hasDigit {
		return ErrPasswordNoDigit
	}
	if !hasSpecial {
		return ErrPasswordNoSpecialChar
	}

	return nil
}

func TestValidatePasswordStrength(t *testing.T) {
	tests := []struct {
		name     string
		password string
		wantErr  error
	}{
		{
			name:     "strong password",
			password: "SecureP@ss123",
			wantErr:  nil,
		},
		{
			name:     "too short",
			password: "Sh0rt!",
			wantErr:  ErrPasswordTooShort,
		},
		{
			name:     "too long",
			password: "ThisPasswordIsWayTooLongAndExceedsTheMaximumAllowedLengthForBcryptWhichIs72Bytes!!!!!",
			wantErr:  ErrPasswordTooLong,
		},
		{
			name:     "no uppercase",
			password: "lowercase123!",
			wantErr:  ErrPasswordNoUppercase,
		},
		{
			name:     "no lowercase",
			password: "UPPERCASE123!",
			wantErr:  ErrPasswordNoLowercase,
		},
		{
			name:     "no digit",
			password: "NoDigitsHere!",
			wantErr:  ErrPasswordNoDigit,
		},
		{
			name:     "no special character",
			password: "NoSpecialChar123",
			wantErr:  ErrPasswordNoSpecialChar,
		},
	}

	for _, tt := range tests {
		t.Run(tt.name, func(t *testing.T) {
			err := ValidatePasswordStrength(tt.password)

			if err != tt.wantErr {
				t.Errorf("ValidatePasswordStrength() error = %v; want %v", err, tt.wantErr)
			}
		})
	}
}
```

These length checks are byte-based, not rune-based. In Go, `len(password)` returns the number of bytes in the UTF-8 string, which is the right measurement for bcrypt because bcrypt truncates input after 72 bytes.

This matters for non-ASCII passwords. For example, many characters outside basic ASCII use multiple bytes, so a password that appears to be fewer than 72 visible characters can still exceed bcrypt's 72-byte limit and must be rejected explicitly.

### Input Sanitization

Sanitization removes or escapes dangerous characters from input that will be displayed or used in contexts where special characters have meaning.

  

```go
// internal/security/sanitize_test.go
package security

import (
	"html"
	"strings"
	"testing"
)

// SanitizeHTML removes or escapes HTML tags from user input.
func SanitizeHTML(input string) string {
	// HTML escape to prevent XSS
	return html.EscapeString(input)
}

// SanitizeSQL removes SQL-dangerous characters (though parameterized queries are preferred).
func SanitizeSQL(input string) string {
	// Remove semicolons, quotes, and comment markers
	replacer := strings.NewReplacer(
		";", "",
		"'", "''", // SQL standard way to escape single quotes
		"--", "",
		"/*", "",
		"*/", "",
	)
	return replacer.Replace(input)
}

func TestSanitizeHTML(t *testing.T) {
	tests := []struct {
		name  string
		input string
		want  string
	}{
		{
			name:  "clean text",
			input: "Hello, World!",
			want:  "Hello, World!",
		},
		{
			name:  "script tag",
			input: "<script>alert('XSS')</script>",
			want:  "&lt;script&gt;alert(&#39;XSS&#39;)&lt;/script&gt;",
		},
		{
			name:  "img tag with onerror",
			input: `<img src=x onerror="alert('XSS')">`,
			want:  "&lt;img src=x onerror=&#34;alert(&#39;XSS&#39;)&#34;&gt;",
		},
		{
			name:  "mixed content",
			input: "Safe text <b>bold</b> more text",
			want:  "Safe text &lt;b&gt;bold&lt;/b&gt; more text",
		},
	}

	for _, tt := range tests {
		t.Run(tt.name, func(t *testing.T) {
			got := SanitizeHTML(tt.input)
			if got != tt.want {
				t.Errorf("SanitizeHTML() = %q; want %q", got, tt.want)
			}
		})
	}
}
```

  

## Section 2: SQL Injection Prevention

SQL injection remains one of the most dangerous and common vulnerabilities. It occurs when user input is concatenated into SQL queries, allowing attackers to modify query logic.

### Understanding SQL Injection

SQL injection prevention is primarily about separating code from data. Parameterized queries provide that separation consistently, while string concatenation erodes it and reintroduces risk during future feature work.

Long-term safety comes from building repository helpers that make safe patterns the default and unsafe patterns awkward. Pair that with tests for malicious inputs so regressions are caught before release.


  

```go
// internal/security/sql_injection_test.go
package security

import (
	"database/sql"
	"testing"
)

// VULNERABLE: Never do this
func GetUserUnsafe(db *sql.DB, email string) (*User, error) {
	// This is vulnerable to SQL injection
	query := "SELECT id, email, username FROM users WHERE email = '" + email + "'"

	// Attack example: email = "' OR '1'='1"
	// Resulting query: SELECT id, email, username FROM users WHERE email = '' OR '1'='1'
	// This returns ALL users

	user := &User{}
	err := db.QueryRow(query).Scan(&user.ID, &user.Email, &user.Username)
	return user, err
}

// SECURE: Use parameterized queries
func GetUserSafe(db *sql.DB, email string) (*User, error) {
	// Database driver handles escaping
	query := "SELECT id, email, username FROM users WHERE email = $1"

	user := &User{}
	err := db.QueryRow(query, email).Scan(&user.ID, &user.Email, &user.Username)
	if err == sql.ErrNoRows {
		return nil, ErrNotFound
	}
	if err != nil {
		return nil, fmt.Errorf("query user: %w", err)
	}
	return user, nil
}

func TestSQLInjectionPrevention(t *testing.T) {
	// This test demonstrates why parameterized queries are necessary
	maliciousInputs := []string{
		"' OR '1'='1",
		"'; DROP TABLE users; --",
		"' UNION SELECT password FROM users WHERE '1'='1",
		"admin'--",
	}

	for _, input := range maliciousInputs {
		t.Run("malicious input: "+input, func(t *testing.T) {
			// With parameterized queries, these inputs are treated as literal strings
			// The database driver escapes them properly

			// In a real test, you would verify that:
			// 1. No users are returned for invalid emails
			// 2. No SQL errors occur
			// 3. No unintended side effects happen

			t.Logf("Testing with input: %q", input)
			// Test would verify safe handling here
		})
	}
}
```

### Secure Database Operations

  

```go
// internal/repository/user_repository_test.go
package repository

import (
	"database/sql"
	"fmt"
	"testing"
)

type UserRepository struct {
	db *sql.DB
}

func NewUserRepository(db *sql.DB) *UserRepository {
	return &UserRepository{db: db}
}

// GetByEmail safely retrieves a user by email using parameterized query.
func (r *UserRepository) GetByEmail(email string) (*User, error) {
	query := `
        SELECT id, email, username, password_hash, role, created_at
        FROM users
        WHERE email = $1
    `

	user := &User{}
	err := r.db.QueryRow(query, email).Scan(
		&user.ID,
		&user.Email,
		&user.Username,
		&user.PasswordHash,
		&user.Role,
		&user.CreatedAt,
	)

	if err == sql.ErrNoRows {
		return nil, ErrNotFound
	}
	if err != nil {
		return nil, fmt.Errorf("get user by email: %w", err)
	}

	return user, nil
}

// Create safely inserts a new user using parameterized query.
func (r *UserRepository) Create(user *User) error {
	query := `
        INSERT INTO users (email, username, password_hash, role)
        VALUES ($1, $2, $3, $4)
        RETURNING id, created_at
    `

	err := r.db.QueryRow(
		query,
		user.Email,
		user.Username,
		user.PasswordHash,
		user.Role,
	).Scan(&user.ID, &user.CreatedAt)

	if err != nil {
		return fmt.Errorf("create user: %w", err)
	}

	return nil
}

// SearchUsers demonstrates safe use of LIKE operator.
func (r *UserRepository) SearchUsers(searchTerm string) ([]*User, error) {
	// Escape special LIKE characters
	searchTerm = escapeLikeString(searchTerm)

	query := `
        SELECT id, email, username, role
        FROM users
        WHERE username LIKE $1 OR email LIKE $1
        LIMIT 50
    `

	// Add wildcards in application, not in user input
	pattern := "%" + searchTerm + "%"

	rows, err := r.db.Query(query, pattern)
	if err != nil {
		return nil, fmt.Errorf("search users: %w", err)
	}
	defer rows.Close()

	var users []*User
	for rows.Next() {
		user := &User{}
		if err := rows.Scan(&user.ID, &user.Email, &user.Username, &user.Role); err != nil {
			return nil, fmt.Errorf("scan user: %w", err)
		}
		users = append(users, user)
	}

	return users, rows.Err()
}

func escapeLikeString(s string) string {
	// Escape LIKE special characters
	s = strings.ReplaceAll(s, "%", "\\%")
	s = strings.ReplaceAll(s, "_", "\\_")
	return s
}
```

  

## Section 3: Password Security with bcrypt

Passwords must never be stored in plain text. bcrypt is a password hashing function designed specifically for this purpose, with built-in salt generation and configurable work factor.

### Password Hashing Implementation

Password hashing policy should be treated as a configurable security control with regular review. Cost factors that are safe today may be weak next year, so implementations should make rehash decisions explicit and testable.

For long-term maintainability, separate hashing interfaces from concrete algorithms and record algorithm metadata with stored hashes when possible. That makes future migrations practical without forced resets.


  

```go
// internal/security/password_hash_test.go
package security

import (
	"fmt"
	"strings"
	"testing"

	"golang.org/x/crypto/bcrypt"
)

// PasswordHasher handles password hashing operations.
type PasswordHasher struct {
	cost int
}

// NewPasswordHasher creates a hasher with specified cost.
func NewPasswordHasher(cost int) *PasswordHasher {
	if cost < bcrypt.MinCost || cost > bcrypt.MaxCost {
		cost = bcrypt.DefaultCost
	}
	return &PasswordHasher{cost: cost}
}

// Hash generates a bcrypt hash of the password.
func (h *PasswordHasher) Hash(password string) (string, error) {
	if len(password) > 72 {
		return "", fmt.Errorf("password exceeds bcrypt 72-byte limit")
	}

	hash, err := bcrypt.GenerateFromPassword([]byte(password), h.cost)
	if err != nil {
		return "", fmt.Errorf("generate password hash: %w", err)
	}

	return string(hash), nil
}

// Verify checks if the password matches the hash.
func (h *PasswordHasher) Verify(password, hash string) error {
	err := bcrypt.CompareHashAndPassword([]byte(hash), []byte(password))
	if err == bcrypt.ErrMismatchedHashAndPassword {
		return ErrInvalidPassword
	}
	if err != nil {
		return fmt.Errorf("compare password: %w", err)
	}
	return nil
}

// NeedsRehash checks if the hash uses outdated cost factor.
func (h *PasswordHasher) NeedsRehash(hash string) bool {
	cost, err := bcrypt.Cost([]byte(hash))
	if err != nil {
		return false
	}
	return cost < h.cost
}

func TestPasswordHasher(t *testing.T) {
	hasher := NewPasswordHasher(bcrypt.DefaultCost)

	t.Run("hash and verify correct password", func(t *testing.T) {
		password := "SecureP@ss123"

		hash, err := hasher.Hash(password)
		if err != nil {
			t.Fatalf("Hash() error = %v", err)
		}

		if hash == password {
			t.Error("Hash should not equal plain password")
		}

		err = hasher.Verify(password, hash)
		if err != nil {
			t.Errorf("Verify() error = %v; want nil", err)
		}
	})

	t.Run("verify incorrect password", func(t *testing.T) {
		password := "SecureP@ss123"
		wrongPassword := "WrongPassword"

		hash, err := hasher.Hash(password)
		if err != nil {
			t.Fatalf("Hash() error = %v", err)
		}

		err = hasher.Verify(wrongPassword, hash)
		if err != ErrInvalidPassword {
			t.Errorf("Verify() error = %v; want %v", err, ErrInvalidPassword)
		}
	})

	t.Run("hash produces different results for same password", func(t *testing.T) {
		password := "SecureP@ss123"

		hash1, _ := hasher.Hash(password)
		hash2, _ := hasher.Hash(password)

		if hash1 == hash2 {
			t.Error("Hash should produce different salts each time")
		}

		// But both should verify
		if err := hasher.Verify(password, hash1); err != nil {
			t.Error("First hash should verify")
		}
		if err := hasher.Verify(password, hash2); err != nil {
			t.Error("Second hash should verify")
		}
	})

	t.Run("password too long", func(t *testing.T) {
		longPassword := strings.Repeat("a", 73)

		_, err := hasher.Hash(longPassword)
		if err == nil {
			t.Error("Hash() should reject password over 72 bytes")
		}
	})

	t.Run("needs rehash", func(t *testing.T) {
		lowCostHasher := NewPasswordHasher(bcrypt.MinCost)
		password := "SecureP@ss123"

		oldHash, _ := lowCostHasher.Hash(password)

		higherCostHasher := NewPasswordHasher(bcrypt.DefaultCost)
		if !higherCostHasher.NeedsRehash(oldHash) {
			t.Error("NeedsRehash() should return true for lower cost hash")
		}
	})
}
```

### User Authentication Flow

  

```go
// internal/auth/service_test.go
package auth

import (
	"testing"
	"time"
)

type AuthService struct {
	userRepo UserRepository
	hasher   PasswordHasher
	tokenGen TokenGenerator
}

func NewAuthService(userRepo UserRepository, hasher PasswordHasher, tokenGen TokenGenerator) *AuthService {
	return &AuthService{
		userRepo: userRepo,
		hasher:   hasher,
		tokenGen: tokenGen,
	}
}

// Register creates a new user with hashed password.
func (s *AuthService) Register(email, username, password string) (*User, error) {
	// Validate password strength
	if err := ValidatePasswordStrength(password); err != nil {
		return nil, err
	}

	// Hash password
	hash, err := s.hasher.Hash(password)
	if err != nil {
		return nil, fmt.Errorf("hash password: %w", err)
	}

	// Create user
	user := &User{
		Email:        email,
		Username:     username,
		PasswordHash: hash,
		Role:         "user",
	}

	if err := s.userRepo.Create(user); err != nil {
		return nil, fmt.Errorf("create user: %w", err)
	}

	return user, nil
}

// Login authenticates a user and returns a JWT token.
func (s *AuthService) Login(email, password string) (string, error) {
	// Get user by email
	user, err := s.userRepo.GetByEmail(email)
	if err == ErrNotFound {
		// Don't reveal whether email exists
		return "", ErrInvalidCredentials
	}
	if err != nil {
		return "", fmt.Errorf("get user: %w", err)
	}

	// Verify password
	if err := s.hasher.Verify(password, user.PasswordHash); err != nil {
		return "", ErrInvalidCredentials
	}

	// Check if password needs rehashing
	if s.hasher.NeedsRehash(user.PasswordHash) {
		newHash, _ := s.hasher.Hash(password)
		user.PasswordHash = newHash
		s.userRepo.Update(user) // Update in background
	}

	// Generate token
	token, err := s.tokenGen.Generate(user)
	if err != nil {
		return "", fmt.Errorf("generate token: %w", err)
	}

	return token, nil
}

func TestAuthService_Register(t *testing.T) {
	mockRepo := NewMockUserRepository()
	hasher := NewPasswordHasher(bcrypt.DefaultCost)
	tokenGen := NewMockTokenGenerator()
	service := NewAuthService(mockRepo, hasher, tokenGen)

	t.Run("successful registration", func(t *testing.T) {
		user, err := service.Register(
			"user@example.com",
			"johndoe",
			"SecureP@ss123",
		)

		if err != nil {
			t.Fatalf("Register() error = %v", err)
		}

		if user.Email != "user@example.com" {
			t.Errorf("Email = %q; want %q", user.Email, "user@example.com")
		}

		// Password should be hashed
		if user.PasswordHash == "SecureP@ss123" {
			t.Error("Password should be hashed")
		}

		// Should be able to verify password
		err = hasher.Verify("SecureP@ss123", user.PasswordHash)
		if err != nil {
			t.Error("Password verification failed")
		}
	})

	t.Run("weak password rejected", func(t *testing.T) {
		_, err := service.Register(
			"user@example.com",
			"johndoe",
			"weak",
		)

		if err == nil {
			t.Error("Register() should reject weak password")
		}
	})
}

func TestAuthService_Login(t *testing.T) {
	mockRepo := NewMockUserRepository()
	hasher := NewPasswordHasher(bcrypt.DefaultCost)
	tokenGen := NewMockTokenGenerator()
	service := NewAuthService(mockRepo, hasher, tokenGen)

	// Setup: Create a user
	password := "SecureP@ss123"
	hash, _ := hasher.Hash(password)
	user := &User{
		ID:           1,
		Email:        "user@example.com",
		PasswordHash: hash,
	}
	mockRepo.users[user.Email] = user

	t.Run("successful login", func(t *testing.T) {
		token, err := service.Login("user@example.com", password)

		if err != nil {
			t.Fatalf("Login() error = %v", err)
		}

		if token == "" {
			t.Error("Token should not be empty")
		}
	})

	t.Run("invalid password", func(t *testing.T) {
		_, err := service.Login("user@example.com", "WrongPassword")

		if err != ErrInvalidCredentials {
			t.Errorf("Login() error = %v; want %v", err, ErrInvalidCredentials)
		}
	})

	t.Run("non-existent user", func(t *testing.T) {
		_, err := service.Login("nonexistent@example.com", password)

		if err != ErrInvalidCredentials {
			t.Errorf("Login() error = %v; want %v", err, ErrInvalidCredentials)
		}
	})
}
```

  

## Section 4: JWT Authentication

JSON Web Tokens (JWT) provide stateless authentication where the server doesn't need to store session data. The token itself contains claims about the user, signed by the server.

### JWT Implementation

  

```go
// internal/auth/jwt_test.go
package auth

import (
	"github.com/golang-jwt/jwt/v5"
	"testing"
	"time"
)

// Claims represents the JWT claims.
type Claims struct {
	UserID int64  `json:"user_id"`
	Email  string `json:"email"`
	Role   string `json:"role"`
	jwt.RegisteredClaims
}

// TokenService handles JWT operations.
type TokenService struct {
	secretKey       []byte
	accessDuration  time.Duration
	refreshDuration time.Duration
}

// NewTokenService creates a token service.
func NewTokenService(secretKey string, accessDuration, refreshDuration time.Duration) *TokenService {
	return &TokenService{
		secretKey:       []byte(secretKey),
		accessDuration:  accessDuration,
		refreshDuration: refreshDuration,
	}
}

// GenerateAccessToken creates an access token.
func (s *TokenService) GenerateAccessToken(user *User) (string, error) {
	claims := &Claims{
		UserID: user.ID,
		Email:  user.Email,
		Role:   user.Role,
		RegisteredClaims: jwt.RegisteredClaims{
			ExpiresAt: jwt.NewNumericDate(time.Now().Add(s.accessDuration)),
			IssuedAt:  jwt.NewNumericDate(time.Now()),
			NotBefore: jwt.NewNumericDate(time.Now()),
		},
	}

	token := jwt.NewWithClaims(jwt.SigningMethodHS256, claims)
	return token.SignedString(s.secretKey)
}

// GenerateRefreshToken creates a refresh token with longer expiration.
func (s *TokenService) GenerateRefreshToken(user *User) (string, error) {
	claims := &Claims{
		UserID: user.ID,
		RegisteredClaims: jwt.RegisteredClaims{
			ExpiresAt: jwt.NewNumericDate(time.Now().Add(s.refreshDuration)),
			IssuedAt:  jwt.NewNumericDate(time.Now()),
		},
	}

	token := jwt.NewWithClaims(jwt.SigningMethodHS256, claims)
	return token.SignedString(s.secretKey)
}

// ValidateToken parses and validates a token.
func (s *TokenService) ValidateToken(tokenString string) (*Claims, error) {
	token, err := jwt.ParseWithClaims(tokenString, &Claims{}, func(token *jwt.Token) (interface{}, error) {
		// Verify signing method
		if _, ok := token.Method.(*jwt.SigningMethodHMAC); !ok {
			return nil, fmt.Errorf("unexpected signing method: %v", token.Header["alg"])
		}
		return s.secretKey, nil
	})

	if err != nil {
		return nil, fmt.Errorf("parse token: %w", err)
	}

	if claims, ok := token.Claims.(*Claims); ok && token.Valid {
		return claims, nil
	}

	return nil, fmt.Errorf("invalid token")
}

func TestTokenService(t *testing.T) {
	secretKey := "test-secret-key-very-secure"
	service := NewTokenService(secretKey, 15*time.Minute, 7*24*time.Hour)

	user := &User{
		ID:    1,
		Email: "user@example.com",
		Role:  "admin",
	}

	t.Run("generate and validate access token", func(t *testing.T) {
		token, err := service.GenerateAccessToken(user)
		if err != nil {
			t.Fatalf("GenerateAccessToken() error = %v", err)
		}

		claims, err := service.ValidateToken(token)
		if err != nil {
			t.Fatalf("ValidateToken() error = %v", err)
		}

		if claims.UserID != user.ID {
			t.Errorf("UserID = %d; want %d", claims.UserID, user.ID)
		}
		if claims.Email != user.Email {
			t.Errorf("Email = %q; want %q", claims.Email, user.Email)
		}
		if claims.Role != user.Role {
			t.Errorf("Role = %q; want %q", claims.Role, user.Role)
		}
	})

	t.Run("expired token", func(t *testing.T) {
		// Create service with very short expiration
		shortService := NewTokenService(secretKey, -1*time.Hour, 7*24*time.Hour)
		token, _ := shortService.GenerateAccessToken(user)

		// Wait a moment to ensure expiration
		time.Sleep(10 * time.Millisecond)

		_, err := service.ValidateToken(token)
		if err == nil {
			t.Error("ValidateToken() should reject expired token")
		}
	})

	t.Run("tampered token", func(t *testing.T) {
		token, _ := service.GenerateAccessToken(user)

		// Tamper with token
		tamperedToken := token[:len(token)-10] + "tampered00"

		_, err := service.ValidateToken(tamperedToken)
		if err == nil {
			t.Error("ValidateToken() should reject tampered token")
		}
	})

	t.Run("wrong secret key", func(t *testing.T) {
		token, _ := service.GenerateAccessToken(user)

		wrongService := NewTokenService("wrong-secret", 15*time.Minute, 7*24*time.Hour)
		_, err := wrongService.ValidateToken(token)
		if err == nil {
			t.Error("ValidateToken() should reject token with wrong secret")
		}
	})
}
```

  

## Section 5: Cross-Site Scripting (XSS) Prevention

XSS attacks inject malicious scripts into web pages viewed by other users. Prevention requires proper output encoding and Content Security Policy headers.

### XSS Prevention Strategies

  

```go
// internal/security/xss_test.go
package security

import (
	"html"
	"html/template"
	"strings"
	"testing"
)

// SanitizeForHTML escapes HTML to prevent XSS.
func SanitizeForHTML(input string) string {
	return html.EscapeString(input)
}

// RenderTemplate safely renders user content in templates.
func RenderTemplate(tmpl *template.Template, data map[string]interface{}) (string, error) {
	var buf strings.Builder
	err := tmpl.Execute(&buf, data)
	return buf.String(), err
}

func TestXSSPrevention(t *testing.T) {
	xssAttempts := []struct {
		name     string
		input    string
		expected string
	}{
		{
			name:     "script tag",
			input:    "<script>alert('XSS')</script>",
			expected: "&lt;script&gt;alert(&#39;XSS&#39;)&lt;/script&gt;",
		},
		{
			name:     "img onerror",
			input:    `<img src=x onerror="alert('XSS')">`,
			expected: `&lt;img src=x onerror=&#34;alert(&#39;XSS&#39;)&#34;&gt;`,
		},
		{
			name:     "javascript protocol",
			input:    `<a href="javascript:alert('XSS')">Click</a>`,
			expected: `&lt;a href=&#34;javascript:alert(&#39;XSS&#39;)&#34;&gt;Click&lt;/a&gt;`,
		},
		{
			name:     "svg with script",
			input:    `<svg onload="alert('XSS')">`,
			expected: `&lt;svg onload=&#34;alert(&#39;XSS&#39;)&#34;&gt;`,
		},
	}

	for _, tt := range xssAttempts {
		t.Run(tt.name, func(t *testing.T) {
			sanitized := SanitizeForHTML(tt.input)
			if sanitized != tt.expected {
				t.Errorf("SanitizeForHTML() = %q; want %q", sanitized, tt.expected)
			}

			// Verify the sanitized output doesn't execute
			if strings.Contains(sanitized, "<script") {
				t.Error("Output contains unescaped script tag")
			}
		})
	}
}

func TestTemplateAutoEscape(t *testing.T) {
	tmpl := template.Must(template.New("test").Parse(`<div>{{.UserInput}}</div>`))

	tests := []struct {
		name  string
		input string
	}{
		{
			name:  "script injection",
			input: "<script>alert('XSS')</script>",
		},
		{
			name:  "html injection",
			input: `<img src=x onerror="alert('XSS')">`,
		},
	}

	for _, tt := range tests {
		t.Run(tt.name, func(t *testing.T) {
			output, err := RenderTemplate(tmpl, map[string]interface{}{
				"UserInput": tt.input,
			})

			if err != nil {
				t.Fatalf("RenderTemplate() error = %v", err)
			}

			// Verify dangerous content is escaped
			if strings.Contains(output, "<script") {
				t.Error("Template did not escape script tag")
			}

			// Verify escaping occurred
			if !strings.Contains(output, "&lt;") {
				t.Error("Expected HTML escaping")
			}
		})
	}
}
```

  

## Section 6: Cross-Site Request Forgery (CSRF) Protection

CSRF attacks trick authenticated users into performing unwanted actions. Protection requires validating that requests originate from your application.

### CSRF Token Implementation

  

```go
// internal/security/csrf_test.go
package security

import (
	"crypto/rand"
	"encoding/base64"
	"fmt"
	"net/http"
	"sync"
	"testing"
)

// CSRFProtector handles CSRF token generation and validation.
type CSRFProtector struct {
	tokens map[string]bool
	mu     sync.RWMutex
}

// NewCSRFProtector creates a CSRF protector.
func NewCSRFProtector() *CSRFProtector {
	return &CSRFProtector{
		tokens: make(map[string]bool),
	}
}

// GenerateToken creates a new CSRF token.
func (p *CSRFProtector) GenerateToken() (string, error) {
	bytes := make([]byte, 32)
	if _, err := rand.Read(bytes); err != nil {
		return "", fmt.Errorf("generate random bytes: %w", err)
	}

	token := base64.URLEncoding.EncodeToString(bytes)

	p.mu.Lock()
	p.tokens[token] = true
	p.mu.Unlock()

	return token, nil
}

// ValidateToken checks if a token is valid.
func (p *CSRFProtector) ValidateToken(token string) bool {
	p.mu.RLock()
	valid := p.tokens[token]
	p.mu.RUnlock()

	return valid
}

// ConsumeToken validates and removes a token (one-time use).
func (p *CSRFProtector) ConsumeToken(token string) bool {
	p.mu.Lock()
	defer p.mu.Unlock()

	if !p.tokens[token] {
		return false
	}

	delete(p.tokens, token)
	return true
}

func TestCSRFProtector(t *testing.T) {
	protector := NewCSRFProtector()

	t.Run("generate and validate token", func(t *testing.T) {
		token, err := protector.GenerateToken()
		if err != nil {
			t.Fatalf("GenerateToken() error = %v", err)
		}

		if token == "" {
			t.Error("Token should not be empty")
		}

		if !protector.ValidateToken(token) {
			t.Error("ValidateToken() should return true for valid token")
		}
	})

	t.Run("invalid token", func(t *testing.T) {
		if protector.ValidateToken("invalid-token") {
			t.Error("ValidateToken() should return false for invalid token")
		}
	})

	t.Run("consume token", func(t *testing.T) {
		token, _ := protector.GenerateToken()

		if !protector.ConsumeToken(token) {
			t.Error("ConsumeToken() should return true for valid token")
		}

		// Token should be invalid after consumption
		if protector.ValidateToken(token) {
			t.Error("Token should be invalid after consumption")
		}
	})

	t.Run("unique tokens", func(t *testing.T) {
		token1, _ := protector.GenerateToken()
		token2, _ := protector.GenerateToken()

		if token1 == token2 {
			t.Error("Generated tokens should be unique")
		}
	})
}
```

## Section 7: Dependency Supply Chain Security

Production-ready security includes dependency integrity, not only request-level defenses. Modern attacks often target transitive dependencies, compromised registries, or tampered build artifacts because those paths can bypass normal application logic controls.

Go modules include built-in checksum verification through `go.sum`, but teams should still verify downloaded module content during CI and release workflows. `go mod verify` confirms cached module files match expected checksums, while `govulncheck` identifies known vulnerabilities reachable from your code paths.

Use explicit module trust settings for private dependencies. `GOSUMDB` controls checksum database verification for public modules, while `GOPRIVATE` declares private module paths that should bypass public proxy and checksum lookups. Set these values intentionally in CI and build environments rather than relying on developer-local defaults.

Finally, connect module integrity to artifact integrity. After dependency verification and vulnerability scanning, sign and attest produced artifacts so deployment systems can enforce provenance policies. Chapter 15 extends this with container signing and attestation workflow patterns.

```bash
go mod verify
govulncheck ./...
```

## Best Practices Summary

This chapter established security-first development practices essential for production systems:

- Validate all input using allowlists rather than denylists
- Enforce strong password requirements with proper feedback
- Always use parameterized SQL queries to prevent injection
- Hash passwords with bcrypt, never store plain text
- Implement JWT authentication with proper expiration and validation
- Sanitize output to prevent XSS attacks
- Protect against CSRF with tokens
- Verify dependency integrity and vulnerability status as part of security gates
- Test security measures comprehensively
- Apply defense-in-depth: multiple layers of protection

Security is not a checklist—it's a mindset that influences every design decision. Each security measure should be tested as thoroughly as functional requirements.

## Exercises

### Exercise 4.1: Complete Validation System

Implement comprehensive validation for a blog post:
- Title: 1-200 characters, no HTML
- Content: required, sanitized HTML allowed
- Tags: 0-10 tags, alphanumeric only
- Author ID: valid user reference
- Publication date: not in the past

### Exercise 4.2: Rate Limiting

Implement rate limiting to prevent brute-force attacks:
- Limit login attempts per IP address
- Lock accounts after failed attempts
- Include CAPTCHA after threshold
- Test with concurrent requests

### Exercise 4.3: Audit Logging

Create a security audit log system:
- Log authentication events
- Log authorization failures
- Log sensitive data access
- Include timestamp, user, IP, action
- Test log integrity

## Further Reading

- OWASP Top 10: https://owasp.org/www-project-top-ten/
- Go Crypto Package: https://pkg.go.dev/golang.org/x/crypto
- JWT Best Practices: https://tools.ietf.org/html/rfc8725
- bcrypt Documentation: https://pkg.go.dev/golang.org/x/crypto/bcrypt

## Chapter Summary

Security-first development treats security as a foundational concern rather than an afterthought. This chapter demonstrated comprehensive input validation that rejects malicious data before it enters your system. SQL injection prevention through parameterized queries eliminates entire categories of attacks. Password security with bcrypt ensures user credentials remain protected even if your database is compromised. JWT authentication provides stateless session management with proper expiration and validation. XSS prevention through output encoding protects users from malicious scripts. CSRF protection ensures requests originate from legitimate users.

These security measures work together as defense-in-depth—multiple layers of protection that make successful attacks exponentially harder. Testing security measures is as critical as implementing them; comprehensive tests verify that protections actually work and catch regressions that could introduce vulnerabilities.

Chapter 5 builds on this security foundation, demonstrating how to implement secure database operations with proper transaction handling and connection pooling.

---

# Part Two: Backend Development

  

# Chapter 5: Database Operations and Testing

### Learning Objectives

- Apply database design principles for production systems
- Choose between SQL and NoSQL appropriately
- Use the database/sql package effectively
- Configure connection pooling for performance
- Implement transactions and rollbacks
- Test database operations with test databases and sqlmock
- Design repository patterns for clean data access abstraction

### Introduction: The Foundation of Data Persistence

Every production application eventually needs to store and retrieve data. While in-memory data structures work for caching and transient state, the authoritative source of truth for your application lives in the database. Poor database operations lead to data corruption, performance degradation, and security vulnerabilities—failures that are far more difficult to recover from than application crashes.

The previous chapter established security-first development practices that protect your application from malicious inputs. This chapter extends that foundation to data persistence, teaching you to interact with databases in ways that ensure data integrity, maintain performance under load, and remain testable throughout development. Database operations are not merely technical implementation details—they represent the persistence layer that your entire system depends upon.

Understanding database operations requires more than knowing SQL syntax or Go's database packages. You must understand how database connections are managed, how transactions ensure atomic operations, how indexes affect query performance, and how to test database code without depending on external infrastructure. These skills differentiate applications that survive production workloads from those that fail under pressure.

Consider what happens when database operations go wrong in production. A connection pool exhausted by unclosed connections prevents new users from accessing your application. A missing transaction causes partial updates when errors occur mid-operation, leaving data in inconsistent states. Missing indexes slow queries to the point of timeouts, cascading failures throughout your system. Each of these scenarios represents a class of problems that proper database operations practices prevent.

The CMS project requires reliable database operations for every feature: user accounts must persist across sessions, content must be stored and retrieved efficiently, relationships between users and content must be maintained correctly. This chapter builds the database layer that the rest of your application depends upon.

  

## Section 1: Database Schema Design

Database schema design directly impacts application performance and maintainability. Proper constraints ensure data integrity at the database level, providing a second line of defense beyond application-level validation. Designing your schema correctly from the start prevents costly migrations later and enables the database to enforce business rules automatically.

### Understanding Schema Constraints

The users table defines the foundation of your authentication system. The email column uses `VARCHAR(254)` because the RFC 5321 specification allows email addresses up to 254 characters. The `UNIQUE` constraint prevents duplicate registrations, while `NOT NULL` ensures every user has a valid email address. The username column uses a shorter 50-character limit with similar constraints, balancing usability against storage efficiency.

The `password_hash` column stores bcrypt hashes rather than plain text passwords. This design follows the security principles from Chapter 4—never store passwords in any form that could be reversed. The column width of 255 characters accommodates bcrypt hashes with sufficient overhead for future algorithm changes.

The role column enforces role-based access control that your authorization system depends upon. Using a VARCHAR with a DEFAULT constraint simplifies application logic by ensuring every user has a valid role even if the application forgets to specify one during registration.

### Foreign Keys and Referential Integrity

The posts table demonstrates foreign key relationships with `ON DELETE CASCADE`. When a user is deleted, all their posts are automatically deleted. This behavior prevents orphaned records—posts without authors—and maintains referential integrity without requiring manual cleanup in your application code.

The slug column provides a URL-friendly identifier for posts. The `UNIQUE` constraint ensures each post has a distinct URL, preventing routing conflicts. Using `VARCHAR(255)` accommodates most slug lengths while providing reasonable storage efficiency.

### Performance Through Indexing

Indexes transform query performance from linear scans to logarithmic lookups. The `idx_posts_author` index accelerates queries that filter or join on `author_id`, common in administrative dashboards showing a user's posts. The `idx_posts_status` index speeds up queries that filter by publication status, essential for public-facing APIs that only return published content. The `idx_posts_slug` index enables efficient lookups when rendering individual posts by their URL.

  

```sql
-- Users table with constraints
CREATE TABLE users (
    id            SERIAL PRIMARY KEY,
    email         VARCHAR(254) NOT NULL UNIQUE,
    username      VARCHAR(50) NOT NULL UNIQUE,
    password_hash VARCHAR(255) NOT NULL,
    role          VARCHAR(20) NOT NULL DEFAULT 'editor',
    created_at    TIMESTAMP NOT NULL DEFAULT CURRENT_TIMESTAMP,
    updated_at    TIMESTAMP NOT NULL DEFAULT CURRENT_TIMESTAMP
);

-- Posts table with foreign key
CREATE TABLE posts (
    id            SERIAL PRIMARY KEY,
    author_id     INTEGER NOT NULL REFERENCES users(id) ON DELETE CASCADE,
    title         VARCHAR(255) NOT NULL,
    slug          VARCHAR(255) NOT NULL UNIQUE,
    content       TEXT NOT NULL,
    status        VARCHAR(20) NOT NULL DEFAULT 'draft',
    published_at  TIMESTAMP,
    created_at    TIMESTAMP NOT NULL DEFAULT CURRENT_TIMESTAMP,
    updated_at    TIMESTAMP NOT NULL DEFAULT CURRENT_TIMESTAMP
);

-- Indexes for performance
CREATE INDEX idx_posts_author ON posts(author_id);
CREATE INDEX idx_posts_status ON posts(status);
CREATE INDEX idx_posts_slug ON posts(slug);

-- Categories table for content organization
CREATE TABLE categories (
    id          SERIAL PRIMARY KEY,
    name        VARCHAR(100) NOT NULL UNIQUE,
    slug        VARCHAR(100) NOT NULL UNIQUE,
    description TEXT,
    created_at  TIMESTAMP NOT NULL DEFAULT CURRENT_TIMESTAMP,
    updated_at  TIMESTAMP NOT NULL DEFAULT CURRENT_TIMESTAMP
);

-- Tags table for flexible content labeling
CREATE TABLE tags (
    id         SERIAL PRIMARY KEY,
    name       VARCHAR(100) NOT NULL UNIQUE,
    slug       VARCHAR(100) NOT NULL UNIQUE,
    created_at TIMESTAMP NOT NULL DEFAULT CURRENT_TIMESTAMP
);

-- Junction table for posts and categories (many-to-many)
CREATE TABLE post_categories (
    post_id     INTEGER NOT NULL REFERENCES posts(id) ON DELETE CASCADE,
    category_id INTEGER NOT NULL REFERENCES categories(id) ON DELETE CASCADE,
    PRIMARY KEY (post_id, category_id)
);

-- Junction table for posts and tags (many-to-many)
CREATE TABLE post_tags (
    post_id INTEGER NOT NULL REFERENCES posts(id) ON DELETE CASCADE,
    tag_id  INTEGER NOT NULL REFERENCES tags(id) ON DELETE CASCADE,
    PRIMARY KEY (post_id, tag_id)
);
```

The categories and tags tables demonstrate many-to-many relationships essential for flexible content organization. A post can belong to multiple categories, and a category can contain multiple posts. The junction tables enforce this relationship with composite primary keys that prevent duplicate associations while maintaining referential integrity.

  

## Section 2: SQL vs NoSQL Database Selection

The choice between SQL and NoSQL databases shapes your application's data model, query capabilities, and operational characteristics. Neither category is universally superior—each excels in specific scenarios. Understanding the tradeoffs enables you to make informed decisions that serve your application's actual requirements rather than following trends.

### When to Choose Relational Databases

Relational databases like PostgreSQL excel when data relationships matter. Your CMS requires users who author posts, posts that belong to categories, and tags that apply across posts. These relationships are naturally modeled with foreign keys and JOIN operations. ACID transactions ensure that creating a user and their first post either both succeed or both fail—no orphaned posts with missing authors.

PostgreSQL's strong consistency model means your queries see a consistent snapshot of data. When you query a post's author, you see the current author information—not a replica that might lag behind the primary. This predictability simplifies application logic and prevents subtle bugs where displayed data differs from actual stored data.

### When to Consider NoSQL

NoSQL databases like MongoDB trade consistency for flexibility and horizontal scalability. Schema-less document storage accommodates varying content structures without migrations. Write-heavy workloads scale across clusters more easily than relational databases. These characteristics serve use cases like user activity logging, real-time analytics, and content caching effectively.

For your CMS, PostgreSQL provides the right balance of features. Complex queries across users, posts, and categories require JOINs that NoSQL databases either cannot perform or perform inefficiently. Transactional integrity ensures consistent state during content creation workflows. The relational model matches your domain concepts directly, keeping application logic aligned with data structure.

  

## Section 3: Repository Pattern Implementation

The repository pattern abstracts database operations behind interfaces, enabling testability and providing a clean separation between business logic and data access. This architectural pattern scales from simple CRUD operations to complex domain models.

### Defining the Repository Interface

Repository interfaces should be designed around domain use cases rather than mirroring table-level CRUD blindly. This keeps business logic expressive and reduces the chance of leaking storage details into upper layers.


  

```go
// internal/repository/user_repository.go
package repository

import (
	"context"
	"database/sql"
	"fmt"
	"time"
)

// User represents a database user record.
type User struct {
	ID           int64     `json:"id"`
	Email        string    `json:"email"`
	Username     string    `json:"username"`
	PasswordHash string    `json:"-"`
	Role         string    `json:"role"`
	CreatedAt    time.Time `json:"created_at"`
	UpdatedAt    time.Time `json:"updated_at"`
}

// UserRepository defines the interface for user data access.
type UserRepository interface {
	Create(ctx context.Context, user *User) error
	GetByID(ctx context.Context, id int64) (*User, error)
	GetByEmail(ctx context.Context, email string) (*User, error)
	Update(ctx context.Context, user *User) error
	Delete(ctx context.Context, id int64) error
	List(ctx context.Context, limit, offset int) ([]*User, error)
}

// userRepository implements UserRepository with a database connection.
type userRepository struct {
	db *sql.DB
}

// NewUserRepository creates a repository with a database connection.
func NewUserRepository(db *sql.DB) UserRepository {
	return &userRepository{db: db}
}
```

The interface definition enables dependency injection and testing. Production code uses the PostgreSQL implementation, while tests use mock implementations. This separation makes your code testable without requiring actual database infrastructure during development.

Use `int64` for persisted identifiers in domain and repository contracts. Reserve `int` for in-memory counts, indexes, and loop variables where architecture-dependent width is acceptable.

### Implementing CRUD Operations

  

```go
// Create inserts a new user into the database.
func (r *userRepository) Create(ctx context.Context, user *User) error {
	query := `
        INSERT INTO users (email, username, password_hash, role, created_at, updated_at)
        VALUES ($1, $2, $3, $4, NOW(), NOW())
        RETURNING id, created_at, updated_at
    `

	err := r.db.QueryRowContext(ctx, query,
		user.Email,
		user.Username,
		user.PasswordHash,
		user.Role,
	).Scan(&user.ID, &user.CreatedAt, &user.UpdatedAt)

	if err != nil {
		return fmt.Errorf("create user: %w", err)
	}

	return nil
}

// GetByID retrieves a user by their ID.
func (r *userRepository) GetByID(ctx context.Context, id int64) (*User, error) {
	query := `
        SELECT id, email, username, password_hash, role, created_at, updated_at
        FROM users
        WHERE id = $1
    `

	user := &User{}
	err := r.db.QueryRowContext(ctx, query, id).Scan(
		&user.ID,
		&user.Email,
		&user.Username,
		&user.PasswordHash,
		&user.Role,
		&user.CreatedAt,
		&user.UpdatedAt,
	)

	if err == sql.ErrNoRows {
		return nil, ErrNotFound
	}
	if err != nil {
		return nil, fmt.Errorf("get user by id: %w", err)
	}

	return user, nil
}

// GetByEmail retrieves a user by their email address.
func (r *userRepository) GetByEmail(ctx context.Context, email string) (*User, error) {
	query := `
        SELECT id, email, username, password_hash, role, created_at, updated_at
        FROM users
        WHERE email = $1
    `

	user := &User{}
	err := r.db.QueryRowContext(ctx, query, email).Scan(
		&user.ID,
		&user.Email,
		&user.Username,
		&user.PasswordHash,
		&user.Role,
		&user.CreatedAt,
		&user.UpdatedAt,
	)

	if err == sql.ErrNoRows {
		return nil, ErrNotFound
	}
	if err != nil {
		return nil, fmt.Errorf("get user by email: %w", err)
	}

	return user, nil
}

// Update modifies an existing user in the database.
func (r *userRepository) Update(ctx context.Context, user *User) error {
	query := `
        UPDATE users
        SET email = $1, username = $2, role = $3, updated_at = NOW()
        WHERE id = $4
    `

	result, err := r.db.ExecContext(ctx, query, user.Email, user.Username, user.Role, user.ID)
	if err != nil {
		return fmt.Errorf("update user: %w", err)
	}

	rows, err := result.RowsAffected()
	if err != nil {
		return fmt.Errorf("rows affected: %w", err)
	}

	if rows == 0 {
		return ErrNotFound
	}

	return nil
}

// Delete removes a user from the database.
func (r *userRepository) Delete(ctx context.Context, id int64) error {
	query := "DELETE FROM users WHERE id = $1"

	result, err := r.db.ExecContext(ctx, query, id)
	if err != nil {
		return fmt.Errorf("delete user: %w", err)
	}

	rows, err := result.RowsAffected()
	if err != nil {
		return fmt.Errorf("rows affected: %w", err)
	}

	if rows == 0 {
		return ErrNotFound
	}

	return nil
}

// List retrieves users with pagination.
func (r *userRepository) List(ctx context.Context, limit, offset int) ([]*User, error) {
	query := `
        SELECT id, email, username, password_hash, role, created_at, updated_at
        FROM users
        ORDER BY created_at DESC
        LIMIT $1 OFFSET $2
    `

	rows, err := r.db.QueryContext(ctx, query, limit, offset)
	if err != nil {
		return nil, fmt.Errorf("list users: %w", err)
	}
	defer rows.Close()

	var users []*User
	for rows.Next() {
		user := &User{}
		err := rows.Scan(
			&user.ID,
			&user.Email,
			&user.Username,
			&user.PasswordHash,
			&user.Role,
			&user.CreatedAt,
			&user.UpdatedAt,
		)
		if err != nil {
			return nil, fmt.Errorf("scan user: %w", err)
		}
		users = append(users, user)
	}

	if err := rows.Err(); err != nil {
		return nil, fmt.Errorf("rows error: %w", err)
	}

	return users, nil
}
```

Each method follows consistent patterns: accepting context for cancellation, using parameterized queries for security, handling errors with proper wrapping, and checking for specific conditions like `sql.ErrNoRows` before returning generic errors.

The repository interfaces and implementations in this section are designed to be injected into service layers and HTTP handlers. In Chapter 6, these abstractions become the persistence foundation for production-grade HTTP APIs, allowing handler logic to stay testable while persistence concerns remain isolated.

Connection leak prevention depends on `defer` placement. Always place `defer rows.Close()` immediately after a successful `Query` or `QueryContext` call, before any additional branches that may return early. Delayed `defer` placement is a common cause of pool exhaustion under load.

Pagination parameters are shown as `int` for snippet simplicity and common handler ergonomics. If your pagination values can originate from very large dataset traversal or architecture-sensitive paths, prefer validating upper bounds or using `int64` at repository boundaries.

  

## Section 4: Connection Pool Configuration

Database connections are expensive resources. Establishing a connection requires network round-trips, authentication, and server-side initialization. Creating a new connection for every request wastes time and server resources. Connection pooling reuses connections across requests, amortizing the connection establishment cost and limiting concurrent connections to what the database can handle.

### Understanding Pool Parameters

Go's `database/sql` package provides connection pooling automatically, but you must configure pool parameters appropriately for your workload. The maximum open connections (`SetMaxOpenConns`) limits how many connections your application can open simultaneously. Setting this too high exhausts database connection limits under load; setting it too low causes requests to wait for available connections.

The maximum idle connections (`SetMaxIdleConns`) controls how many connections remain open when not in use. Maintaining idle connections reduces latency for subsequent requests that need database access. However, keeping too many idle connections wastes server resources. For most applications, 5-10 idle connections provide a good balance.

The connection maximum lifetime (`SetConnMaxLifetime`) prevents connections from becoming stale. Database connections can timeout due to network interruptions, server restarts, or idle timeouts. Old connections that have become invalid cause errors when used. Rotating connections periodically ensures your pool remains healthy.

  

```go
// internal/database/db.go
package database

import (
	"context"
	"database/sql"
	"fmt"
	"time"

	_ "github.com/lib/pq"
)

// NewDB creates a database connection with pooling.
func NewDB(connString string) (*sql.DB, error) {
	db, err := sql.Open("postgres", connString)
	if err != nil {
		return nil, fmt.Errorf("open database: %w", err)
	}

	// Configure connection pool for production workload
	// MaxOpenConns limits concurrent connections to database capacity
	// For typical web application: 25 connections handle 200-500 concurrent requests
	// Adjust based on your actual database's connection limit and query duration
	db.SetMaxOpenConns(25)

	// MaxIdleConns keeps warm connections ready for incoming requests
	// 5 connections handles most request bursts without exhausting resources
	db.SetMaxIdleConns(5)

	// ConnMaxLifetime prevents stale connections from causing runtime errors
	// 5 minutes is conservative—database typically resets connections after 30min idle
	db.SetConnMaxLifetime(5 * time.Minute)

	// Verify connection is actually usable before returning
	// sql.Open doesn't actually connect—this Ping forces connection verification
	ctx, cancel := context.WithTimeout(context.Background(), 5*time.Second)
	defer cancel()

	if err := db.PingContext(ctx); err != nil {
		return nil, fmt.Errorf("ping database: %w", err)
	}

	return db, nil
}

// HealthCheck verifies database connectivity for monitoring.
func HealthCheck(ctx context.Context, db *sql.DB) error {
	return db.PingContext(ctx)
}
```

The configuration shown handles typical web application workloads. If your application has different characteristics—long-running queries, high request volumes, or connection-intensive operations—adjust these values accordingly. Monitor connection pool statistics in production to identify optimal settings for your specific workload.

  

## Section 5: Transaction Management

Database transactions ensure that multiple operations succeed or fail together. Without transactions, partial failures leave your data in inconsistent states—a user account created without their initial profile data, a post published without recording the publishing event. Transactions model these operations as atomic units that the database guarantees will not partially apply.

### Understanding Transaction Semantics

Transactions in Go use the `Begin`, `Commit`, and `Rollback` methods on the database connection. The pattern involves beginning a transaction, executing operations within its context, and either committing successful operations or rolling back on any error. The defer statement ensures rollback occurs even if your function returns early due to an error.

Transaction isolation levels control how concurrent transactions interact. The default Read Committed isolation prevents dirty reads—seeing uncommitted changes from other transactions. Serializable isolation provides the strongest consistency guarantees but reduces concurrency. Understanding your application's consistency requirements enables choosing the appropriate isolation level.

  

```go
// internal/repository/post_repository.go
package repository

import (
	"context"
	"database/sql"
	"fmt"
	"time"

	"github.com/lib/pq"
)

// PostRepository handles post data access with transaction support.
type PostRepository struct {
	db *sql.DB
}

// NewPostRepository creates a post repository.
func NewPostRepository(db *sql.DB) *PostRepository {
	return &PostRepository{db: db}
}

// Post represents a blog post in the database.
type Post struct {
	ID            int64      `json:"id"`
	AuthorID      int64      `json:"author_id"`
	Title         string     `json:"title"`
	Slug          string     `json:"slug"`
	Content       string     `json:"content"`
	Excerpt       string     `json:"excerpt"`
	FeaturedImage string     `json:"featured_image"`
	Status        string     `json:"status"`
	PublishedAt   *time.Time `json:"published_at,omitempty"`
	CreatedAt     time.Time  `json:"created_at"`
	UpdatedAt     time.Time  `json:"updated_at"`
}

// PostWithAuthor represents a post joined with author information.
type PostWithAuthor struct {
	Post
	AuthorEmail    string `json:"author_email"`
	AuthorUsername string `json:"author_username"`
}

// CreateWithCategories creates a post and associates it with categories atomically.
func (r *PostRepository) CreateWithCategories(
	ctx context.Context,
	post *Post,
	categoryIDs []int64,
) error {
	tx, err := r.db.BeginTx(ctx, nil)
	if err != nil {
		return fmt.Errorf("begin transaction: %w", err)
	}

	// Ensure rollback on any failure
	defer func() {
		if err != nil {
			tx.Rollback()
		}
	}()

	// Create the post
	postQuery := `
        INSERT INTO posts (author_id, title, slug, content, excerpt, featured_image, status, created_at, updated_at)
        VALUES ($1, $2, $3, $4, $5, $6, $7, NOW(), NOW())
        RETURNING id, created_at, updated_at
    `

	err = tx.QueryRowContext(ctx, postQuery,
		post.AuthorID,
		post.Title,
		post.Slug,
		post.Content,
		post.Excerpt,
		post.FeaturedImage,
		post.Status,
	).Scan(&post.ID, &post.CreatedAt, &post.UpdatedAt)

	if err != nil {
		return fmt.Errorf("create post: %w", err)
	}

	// Associate categories
	if len(categoryIDs) > 0 {
		categoryQuery := `
            INSERT INTO post_categories (post_id, category_id)
            SELECT $1, unnest($2::bigint[])
        `

		_, err = tx.ExecContext(ctx, categoryQuery, post.ID, pq.Array(categoryIDs))
		if err != nil {
			return fmt.Errorf("associate categories: %w", err)
		}
	}

	// Commit transaction—only reached if no errors occurred
	if err = tx.Commit(); err != nil {
		return fmt.Errorf("commit transaction: %w", err)
	}

	return nil
}

// UpdateWithCategories updates a post and its categories atomically.
func (r *PostRepository) UpdateWithCategories(
	ctx context.Context,
	post *Post,
	categoryIDs []int64,
) error {
	tx, err := r.db.BeginTx(ctx, nil)
	if err != nil {
		return fmt.Errorf("begin transaction: %w", err)
	}

	defer func() {
		if err != nil {
			tx.Rollback()
		}
	}()

	// Update the post
	updateQuery := `
        UPDATE posts
        SET title = $1, slug = $2, content = $3, excerpt = $4,
            featured_image = $5, status = $6, updated_at = NOW()
        WHERE id = $7
    `

	result, err := tx.ExecContext(ctx, updateQuery,
		post.Title, post.Slug, post.Content, post.Excerpt,
		post.FeaturedImage, post.Status, post.ID,
	)
	if err != nil {
		return fmt.Errorf("update post: %w", err)
	}

	rows, err := result.RowsAffected()
	if err != nil {
		return fmt.Errorf("rows affected: %w", err)
	}
	if rows == 0 {
		return ErrNotFound
	}

	// Replace categories
	deleteQuery := "DELETE FROM post_categories WHERE post_id = $1"
	_, err = tx.ExecContext(ctx, deleteQuery, post.ID)
	if err != nil {
		return fmt.Errorf("delete old categories: %w", err)
	}

	if len(categoryIDs) > 0 {
		categoryQuery := `
            INSERT INTO post_categories (post_id, category_id)
            SELECT $1, unnest($2::bigint[])
        `
		_, err = tx.ExecContext(ctx, categoryQuery, post.ID, pq.Array(categoryIDs))
		if err != nil {
			return fmt.Errorf("insert categories: %w", err)
		}
	}

	if err = tx.Commit(); err != nil {
		return fmt.Errorf("commit transaction: %w", err)
	}

	return nil
}
```

The transaction pattern ensures that creating or updating a post with its categories either fully succeeds or fully fails. If the post insertion succeeds but category association fails, the transaction rolls back the post creation, maintaining consistent state.

  

## Section 6: Testing Database Operations

Testing database code requires careful consideration of dependencies. Integration tests using real databases verify actual behavior but require infrastructure and slow down test execution. Unit tests using mock databases run quickly and don't require infrastructure but must accurately simulate database behavior. A comprehensive testing strategy uses both approaches appropriately.

### Unit Testing with sqlmock

Use sqlmock to prove query behavior, argument binding, and transactional control flow quickly, but pair it with integration tests for real driver semantics. Reliable teams treat these as complementary layers: unit tests for speed and precision, integration tests for confidence in production behavior.


`sqlmock` provides a test double for `database/sql` by returning a real `*sql.DB` handle backed by programmable expectations. Your repository can keep its production signature (`*sql.DB`) while tests still assert query shape, arguments, and returned rows/errors without needing a live PostgreSQL instance.

  

```go
// internal/repository/user_repository_test.go
package repository

import (
	"context"
	"database/sql"
	"testing"
	"time"

	"github.com/DATA-DOG/go-sqlmock"
)

func TestUserRepository_Create(t *testing.T) {
	db, mock, err := sqlmock.New()
	if err != nil {
		t.Fatalf("sqlmock.New() error = %v", err)
	}
	defer db.Close()

	now := time.Now()
	rows := sqlmock.NewRows([]string{"id", "created_at", "updated_at"}).
		AddRow(int64(1), now, now)

	mock.ExpectQuery("INSERT INTO users \\(email, username, password_hash, role, created_at, updated_at\\)").
		WithArgs("user@example.com", "johndoe", "hashedpassword", "editor").
		WillReturnRows(rows)

	repo := NewUserRepository(db)
	user := &User{
		Email:        "user@example.com",
		Username:     "johndoe",
		PasswordHash: "hashedpassword",
		Role:         "editor",
	}

	if err := repo.Create(context.Background(), user); err != nil {
		t.Fatalf("Create() error = %v", err)
	}
	if user.ID != 1 {
		t.Fatalf("user.ID = %d; want 1", user.ID)
	}
	if err := mock.ExpectationsWereMet(); err != nil {
		t.Fatalf("unfulfilled expectations: %v", err)
	}
}

func TestUserRepository_GetByID_NotFound(t *testing.T) {
	db, mock, err := sqlmock.New()
	if err != nil {
		t.Fatalf("sqlmock.New() error = %v", err)
	}
	defer db.Close()

	mock.ExpectQuery("SELECT id, email, username, password_hash, role, created_at, updated_at").
		WithArgs(int64(999)).
		WillReturnError(sql.ErrNoRows)

	repo := NewUserRepository(db)
	_, err = repo.GetByID(context.Background(), 999)
	if err != ErrNotFound {
		t.Fatalf("err = %v; want ErrNotFound", err)
	}
	if err := mock.ExpectationsWereMet(); err != nil {
		t.Fatalf("unfulfilled expectations: %v", err)
	}
}

func TestUserRepository_List(t *testing.T) {
	db, mock, err := sqlmock.New()
	if err != nil {
		t.Fatalf("sqlmock.New() error = %v", err)
	}
	defer db.Close()

	now := time.Now()
	rows := sqlmock.NewRows([]string{"id", "email", "username", "password_hash", "role", "created_at", "updated_at"}).
		AddRow(int64(1), "user1@example.com", "user1", "hash1", "admin", now, now).
		AddRow(int64(2), "user2@example.com", "user2", "hash2", "editor", now, now)

	mock.ExpectQuery("SELECT id, email, username, password_hash, role, created_at, updated_at").
		WithArgs(10, 0).
		WillReturnRows(rows)

	repo := NewUserRepository(db)
	users, err := repo.List(context.Background(), 10, 0)
	if err != nil {
		t.Fatalf("List() error = %v", err)
	}
	if len(users) != 2 {
		t.Fatalf("len(users) = %d; want 2", len(users))
	}
	if err := mock.ExpectationsWereMet(); err != nil {
		t.Fatalf("unfulfilled expectations: %v", err)
	}
}
```

### Integration Testing with Real Databases

Integration tests verify that your repository actually works with a real database. These tests catch issues that mocks cannot, such as incorrect SQL syntax, database constraint violations, and transaction behavior.

  

```go
// Integration tests with real database for comprehensive verification

func TestUserRepository_Integration(t *testing.T) {
	if testing.Short() {
		t.Skip("skipping integration test in short mode")
	}

	// Use a test container or test database
	db, teardown := setupTestDatabase(t)
	defer teardown()

	repo := NewUserRepository(db)

	t.Run("create and retrieve user", func(t *testing.T) {
		user := &User{
			Email:        "test@example.com",
			Username:     "testuser",
			PasswordHash: "hash",
			Role:         "editor",
		}

		err := repo.Create(context.Background(), user)
		if err != nil {
			t.Fatalf("Create() error = %v", err)
		}

		if user.ID == 0 {
			t.Error("user.ID should be set after Create")
		}

		retrieved, err := repo.GetByID(context.Background(), user.ID)
		if err != nil {
			t.Fatalf("GetByID() error = %v", err)
		}

		if retrieved.Email != user.Email {
			t.Errorf("Email = %s; want %s", retrieved.Email, user.Email)
		}
	})

	t.Run("update user", func(t *testing.T) {
		user := &User{
			Email:        "update@example.com",
			Username:     "updateme",
			PasswordHash: "hash",
			Role:         "admin",
		}

		repo.Create(context.Background(), user)

		user.Role = "editor"
		err := repo.Update(context.Background(), user)
		if err != nil {
			t.Fatalf("Update() error = %v", err)
		}

		retrieved, _ := repo.GetByID(context.Background(), user.ID)
		if retrieved.Role != "editor" {
			t.Errorf("Role = %s; want editor", retrieved.Role)
		}
	})

	t.Run("delete user", func(t *testing.T) {
		user := &User{
			Email:        "delete@example.com",
			Username:     "deleteme",
			PasswordHash: "hash",
			Role:         "editor",
		}

		repo.Create(context.Background(), user)

		err := repo.Delete(context.Background(), user.ID)
		if err != nil {
			t.Fatalf("Delete() error = %v", err)
		}

		_, err = repo.GetByID(context.Background(), user.ID)
		if err != ErrNotFound {
			t.Errorf("GetByID() after delete error = %v; want ErrNotFound", err)
		}
	})
}

// setupTestDatabase creates a test database instance.
func setupTestDatabase(t *testing.T) (*sql.DB, func()) {
	// In production, use testcontainers-go or similar to spin up PostgreSQL
	connString := "postgres://test:test@localhost:5432/testdb?sslmode=disable"

	db, err := sql.Open("postgres", connString)
	if err != nil {
		t.Fatalf("Failed to connect to test database: %v", err)
	}

	// Apply schema
	schema := `
        DROP TABLE IF EXISTS users CASCADE;
        CREATE TABLE users (
            id            SERIAL PRIMARY KEY,
            email         VARCHAR(254) NOT NULL UNIQUE,
            username      VARCHAR(50) NOT NULL UNIQUE,
            password_hash VARCHAR(255) NOT NULL,
            role          VARCHAR(20) NOT NULL DEFAULT 'editor',
            created_at    TIMESTAMP NOT NULL DEFAULT CURRENT_TIMESTAMP,
            updated_at    TIMESTAMP NOT NULL DEFAULT CURRENT_TIMESTAMP
        );
    `

	if _, err := db.Exec(schema); err != nil {
		t.Fatalf("Failed to create schema: %v", err)
	}

	teardown := func() {
		db.Exec("DROP TABLE IF EXISTS users CASCADE")
		db.Close()
	}

	return db, teardown
}
```

## Best Practices Summary

This chapter established database operations practices essential for production systems:

- Design schemas with constraints that enforce business rules at the database level
- Choose SQL or NoSQL based on actual requirements, not trends
- Configure connection pools appropriately for your workload
- Use repository patterns to abstract data access and enable testing
- Implement transactions for operations requiring atomicity
- Test database code with both unit tests (sqlmock) and integration tests (real database)
- Always use context for cancellation and timeout handling
- Handle errors with proper wrapping to maintain debugging context

Database design with proper constraints ensures data integrity even when application code has bugs. Connection pooling configuration balances performance against database capacity. Transaction patterns guarantee atomic operations across multiple data modifications. Repository patterns provide clean interfaces that simplify testing. Testing strategies using both mocks and real databases ensure correctness at different levels of abstraction.

## Exercises

### Exercise 5.1: Extend Post Repository

Extend the post repository with the following methods:

```go
// Add these methods to PostRepository:
// GetBySlug(ctx context.Context, slug string) (*Post, error)
// GetByAuthor(ctx context.Context, authorID int64, limit, offset int) ([]*Post, error)
// GetPublished(ctx context.Context, limit, offset int) ([]*PostWithAuthor, error)
// Publish(ctx context.Context, id int64) error
// Unpublish(ctx context.Context, id int64) error
```

Implement each method with proper error handling and write comprehensive tests using both sqlmock and integration tests.

### Exercise 5.2: Category Repository

Create a category repository supporting:

```go
// Create category repository:
// Create(ctx context.Context, category *Category) error
// GetByID(ctx context.Context, id int64) (*Category, error)
// GetBySlug(ctx context.Context, slug string) (*Category, error)
// Update(ctx context.Context, category *Category) error
// Delete(ctx context.Context, id int64) error
// List(ctx context.Context) ([]*Category, error)
```

Include tests that verify constraint enforcement and error handling.

### Exercise 5.3: Transaction Testing

Write integration tests for the repository layer that verify:

- Transactions actually rollback on error
- Foreign key constraints prevent invalid references
- Unique constraints prevent duplicate entries
- Cascade deletes remove related records

Use a test database to verify these behaviors end-to-end.

## Further Reading

- PostgreSQL Documentation: https://www.postgresql.org/docs/current/
- SQL Database/sql Package: https://pkg.go.dev/database/sql
- sqlmock Documentation: https://github.com/DATA-DOG/go-sqlmock
- Repository Pattern: https://docs.microsoft.com/en-us/dotnet/architecture/microservices/microservice-ddd-cqrs-patterns/infrastructure-persistence-layer-design
- Connection Pooling Best Practices: https://wiki.postgresql.org/wiki/Number_Of_Database_Connections

## Chapter Summary

This chapter built the database layer that your CMS depends upon for reliable data persistence. Database design principles ensure data integrity through constraints at the database level. Connection pooling configuration balances performance against database capacity. Transaction patterns guarantee atomic operations across multiple data modifications.

The repository pattern abstracts database access behind clean, testable interfaces. Testing strategies using sqlmock enable fast unit tests while integration tests verify actual database behavior. These practices ensure your data layer remains reliable as your application grows.

Chapter 6 applies these database foundations to build HTTP servers and APIs. You will create handlers that receive requests, interact with your repository layer, and return appropriate responses. The combination of robust database operations and well-designed HTTP APIs forms the backbone of your production CMS.

---

  

# Chapter 6: HTTP Servers and API Design

## Learning Objectives

- Build production-grade HTTP servers using Go's net/http package
- Design RESTful APIs following REST principles and industry best practices
- Implement middleware patterns for cross-cutting concerns like logging and authentication
- Handle routing with the chi router for complex, hierarchical URL structures
- Create comprehensive request validation and consistent response formatting
- Test HTTP handlers thoroughly using httptest package with mock services
- Apply proper HTTP status codes and error handling patterns
- Implement rate limiting, CORS, and security middleware for production APIs
- Structure handlers for maintainability and testability

## Introduction: The Interface Between Systems

HTTP APIs form the primary interface between modern applications and their clients. Whether serving mobile apps, web frontends, or other backend services, your API design determines developer experience, performance characteristics, and long-term maintainability. A well-designed API is intuitive to use, consistent in behavior, and robust under production loads. A poorly designed API frustrates developers, encourages workarounds, and becomes technical debt that haunts your project for years.

The previous chapter established reliable database operations that persist your application's state. This chapter builds the HTTP layer that exposes that state to the world. HTTP servers translate external requests into internal operations, coordinate database access through repositories, and format responses for clients. Every interaction users have with your CMS flows through the HTTP handlers you write in this chapter.

Go's standard library provides exceptional HTTP support through the `net/http` package. Unlike many languages that require external frameworks for production-ready servers, Go's standard library includes everything needed: routing, middleware, request parsing, response writing, concurrent request handling, and comprehensive testing utilities. This design philosophy—batteries included—enables you to build production systems without external dependencies, though strategic use of third-party libraries can enhance functionality.

The principles in this chapter apply broadly to API design regardless of language or framework. Resource-oriented URLs make APIs intuitive and predictable. Appropriate HTTP methods communicate intent clearly. Consistent error responses enable robust client-side error handling. Proper status codes provide semantic information that clients can act upon. These patterns emerged from decades of HTTP API development and represent industry consensus on effective API design.

Testing HTTP handlers requires different techniques than testing pure functions or database repositories. The `httptest` package enables testing handlers without running actual HTTP servers or binding to network ports, making tests fast, reliable, and suitable for continuous integration environments. Combined with interface-based mocking of service layers, you can test API behavior thoroughly without external dependencies like databases or third-party services.

Consider what happens when HTTP APIs are designed poorly. Inconsistent endpoint naming forces developers to constantly reference documentation. Missing input validation allows invalid data to corrupt your database. Vague error messages leave clients unable to diagnose problems. Poor error handling causes 500 errors for user mistakes that should return 400 errors. Missing rate limiting enables abuse and denial of service. Each of these issues represents an avoidable failure that proper HTTP API design prevents.

The CMS project requires a comprehensive HTTP API: user registration and authentication, content creation and editing, category management, published content retrieval, and administrative operations. Each endpoint must validate inputs, authorize requests, perform operations through the repository layer, and format responses consistently. This chapter implements these endpoints using patterns that scale from simple CRUD operations to complex business logic.

  

## Section 1: HTTP Server Fundamentals

Building HTTP servers in Go starts with understanding the `net/http` package and its abstractions. The package provides the `Handler` interface, which any type with a `ServeHTTP(ResponseWriter, *Request)` method satisfies. This simple interface enables powerful composition patterns where handlers wrap other handlers to add functionality.

### Understanding HTTP Server Configuration

Production HTTP servers require careful configuration beyond simply calling `http.ListenAndServe`. Timeouts prevent slow clients from exhausting server resources. Maximum header sizes limit memory consumption from malicious requests. Graceful shutdown ensures in-flight requests complete before the server terminates. These configurations transform a simple development server into a production-ready system.

The `ReadTimeout` limits how long the server waits for the client to send the complete request, including headers and body. Setting this prevents slow clients from holding connections open indefinitely. A typical value of 10 seconds accommodates most legitimate clients while protecting against slowloris attacks where malicious clients send data very slowly.

The `WriteTimeout` limits how long the server takes to write the complete response. This timeout protects against clients that read slowly, preventing them from tying up server resources. For most APIs returning JSON responses, 10 seconds provides ample time even for large response bodies.

The `IdleTimeout` controls how long to keep connections open when waiting for the next request in keep-alive scenarios. HTTP keep-alive reuses TCP connections across multiple requests, improving performance by avoiding connection establishment overhead. An idle timeout of 60 seconds balances resource utilization against connection reuse benefits.

  

```go
// internal/server/server.go
package server

import (
	"context"
	"fmt"
	"log"
	"net/http"
	"os"
	"os/signal"
	"syscall"
	"time"
)

// Server wraps an HTTP server with production-ready configuration.
type Server struct {
	httpServer *http.Server
	addr       string
	logger     *log.Logger
}

// Config holds server configuration parameters.
type Config struct {
	Addr           string
	ReadTimeout    time.Duration
	WriteTimeout   time.Duration
	IdleTimeout    time.Duration
	MaxHeaderBytes int
}

// DefaultConfig returns sensible production defaults.
func DefaultConfig(addr string) Config {
	return Config{
		Addr:           addr,
		ReadTimeout:    10 * time.Second,
		WriteTimeout:   10 * time.Second,
		IdleTimeout:    60 * time.Second,
		MaxHeaderBytes: 1 << 20, // 1 MB
	}
}

// NewServer creates a configured HTTP server.
func NewServer(config Config, handler http.Handler) *Server {
	logger := log.New(os.Stdout, "[server] ", log.LstdFlags)

	return &Server{
		addr:   config.Addr,
		logger: logger,
		httpServer: &http.Server{
			Addr:           config.Addr,
			Handler:        handler,
			ReadTimeout:    config.ReadTimeout,
			WriteTimeout:   config.WriteTimeout,
			IdleTimeout:    config.IdleTimeout,
			MaxHeaderBytes: config.MaxHeaderBytes,
			ErrorLog:       logger,
		},
	}
}

// Start begins serving HTTP requests.
func (s *Server) Start() error {
	s.logger.Printf("Server starting on %s", s.addr)

	if err := s.httpServer.ListenAndServe(); err != nil && err != http.ErrServerClosed {
		return fmt.Errorf("server error: %w", err)
	}

	return nil
}

// Shutdown gracefully stops the server.
// It waits for in-flight requests to complete before returning.
func (s *Server) Shutdown(ctx context.Context) error {
	s.logger.Println("Server shutting down...")

	if err := s.httpServer.Shutdown(ctx); err != nil {
		return fmt.Errorf("shutdown error: %w", err)
	}

	s.logger.Println("Server stopped")
	return nil
}

// Run starts the server and handles graceful shutdown on SIGINT/SIGTERM.
func (s *Server) Run() error {
	// Start server in goroutine
	serverErrors := make(chan error, 1)
	go func() {
		serverErrors <- s.Start()
	}()

	// Wait for interrupt signal or server error
	shutdown := make(chan os.Signal, 1)
	signal.Notify(shutdown, os.Interrupt, syscall.SIGTERM)

	select {
	case err := <-serverErrors:
		return fmt.Errorf("server failed: %w", err)

	case sig := <-shutdown:
		s.logger.Printf("Received signal: %v", sig)

		// Give outstanding requests 15 seconds to complete
		ctx, cancel := context.WithTimeout(context.Background(), 15*time.Second)
		defer cancel()

		if err := s.Shutdown(ctx); err != nil {
			return fmt.Errorf("graceful shutdown failed: %w", err)
		}
	}

	return nil
}
```

This server implementation handles production concerns that naive implementations miss. Graceful shutdown ensures no requests are dropped during deployment. Signal handling enables orchestration systems like Kubernetes to manage the lifecycle cleanly. Timeouts protect against resource exhaustion. Error logging provides visibility into server issues.

### Testing Server Lifecycle

Testing server initialization, startup, and shutdown verifies that configuration applies correctly and graceful shutdown actually works. These tests catch configuration errors before production deployment.

  

```go
// internal/server/server_test.go
package server

import (
	"context"
	"net/http"
	"testing"
	"time"
)

func TestServer_StartAndShutdown(t *testing.T) {
	handler := http.HandlerFunc(func(w http.ResponseWriter, r *http.Request) {
		w.WriteHeader(http.StatusOK)
		w.Write([]byte("Hello, World!"))
	})

	config := DefaultConfig(":0") // :0 assigns random available port
	server := NewServer(config, handler)

	// Start server in background
	go func() {
		if err := server.Start(); err != nil {
			t.Logf("Server stopped: %v", err)
		}
	}()

	// Give server time to start
	time.Sleep(100 * time.Millisecond)

	// Test graceful shutdown
	ctx, cancel := context.WithTimeout(context.Background(), 5*time.Second)
	defer cancel()

	if err := server.Shutdown(ctx); err != nil {
		t.Errorf("Shutdown error: %v", err)
	}
}

func TestServer_TimeoutConfiguration(t *testing.T) {
	config := Config{
		Addr:         ":8080",
		ReadTimeout:  5 * time.Second,
		WriteTimeout: 10 * time.Second,
		IdleTimeout:  30 * time.Second,
	}

	handler := http.HandlerFunc(func(w http.ResponseWriter, r *http.Request) {
		w.WriteHeader(http.StatusOK)
	})

	server := NewServer(config, handler)

	// Verify configuration applied
	if server.httpServer.ReadTimeout != config.ReadTimeout {
		t.Errorf("ReadTimeout = %v; want %v", server.httpServer.ReadTimeout, config.ReadTimeout)
	}

	if server.httpServer.WriteTimeout != config.WriteTimeout {
		t.Errorf("WriteTimeout = %v; want %v", server.httpServer.WriteTimeout, config.WriteTimeout)
	}

	if server.httpServer.IdleTimeout != config.IdleTimeout {
		t.Errorf("IdleTimeout = %v; want %v", server.httpServer.IdleTimeout, config.IdleTimeout)
	}
}
```

  

## Section 2: RESTful API Design Principles

REST (Representational State Transfer) provides architectural constraints that guide API design. These constraints aren't arbitrary rules—they emerged from the design of HTTP and the World Wide Web, proven to scale to billions of users. Understanding and applying REST principles produces APIs that feel natural to developers familiar with HTTP.

### Resources and URL Structure

REST centers on resources—entities your application manages. Users, posts, categories, and tags are all resources. Each resource has a URL that identifies it uniquely. Collections of resources also have URLs. This resource-oriented design creates intuitive, predictable APIs.

Resource URLs follow a hierarchical structure. Collections are plural nouns: `/users`, `/posts`, `/categories`. Individual resources append an identifier: `/users/123`, `/posts/456`. Related resources nest under their parent: `/users/123/posts` returns posts by user 123. This hierarchy communicates relationships clearly without requiring documentation.

HTTP methods indicate operations on resources. GET retrieves resources without side effects, supporting caching and repeated requests safely. POST creates new resources, with the server assigning identifiers. PUT replaces entire resources, requiring clients to send complete representations. PATCH modifies resources partially, allowing incremental updates. DELETE removes resources.

The combination of resource URLs and HTTP methods creates a complete CRUD interface. `GET /users` lists users. `POST /users` creates a user. `GET /users/123` retrieves user 123. `PUT /users/123` updates user 123. `DELETE /users/123` removes user 123. This pattern repeats consistently across all resources, reducing the cognitive load on API consumers.

### Status Codes Communicate Meaning

HTTP status codes provide semantic information about request outcomes. Using status codes correctly enables clients to handle responses appropriately without parsing response bodies. The five status code classes each serve specific purposes:

**2xx Success**: The request succeeded. 200 OK indicates successful retrieval. 201 Created indicates successful creation with the Location header pointing to the new resource. 204 No Content indicates successful operation with no response body, common for DELETE operations.

**3xx Redirection**: The resource moved or multiple representations exist. 301 Moved Permanently indicates permanent URL changes. 304 Not Modified supports conditional requests with caching.

**4xx Client Errors**: The client sent an invalid request. 400 Bad Request indicates malformed requests or validation failures. 401 Unauthorized indicates missing or invalid authentication. 403 Forbidden indicates authenticated but insufficient permissions. 404 Not Found indicates the resource doesn't exist. 409 Conflict indicates the operation would violate constraints like duplicate email addresses. 422 Unprocessable Entity indicates syntactically valid but semantically incorrect requests.

**5xx Server Errors**: The server failed to fulfill a valid request. 500 Internal Server Error indicates unexpected server failures. 503 Service Unavailable indicates temporary unavailability, appropriate during maintenance or overload.

Selecting the correct status code communicates intention clearly. A client receiving 404 knows not to retry, while 503 suggests retrying after a delay. 400 indicates client-side bugs needing fixes, while 500 indicates server-side issues beyond client control.

### Consistent Error Response Format

Error responses need structure beyond status codes. Clients need actionable information to display errors to users or log for debugging. A consistent error response format enables generic error handling in client code.

  

```go
// internal/response/error.go
package response

import (
	"encoding/json"
	"net/http"
)

// ErrorResponse represents a structured error response.
type ErrorResponse struct {
	Error   string            `json:"error"`
	Message string            `json:"message,omitempty"`
	Details map[string]string `json:"details,omitempty"`
}

// ValidationError represents field-level validation errors.
type ValidationError struct {
	Field   string `json:"field"`
	Message string `json:"message"`
}

// ValidationErrorResponse represents validation failure details.
type ValidationErrorResponse struct {
	Error  string            `json:"error"`
	Errors []ValidationError `json:"errors"`
}

// WriteError writes a structured error response.
func WriteError(w http.ResponseWriter, status int, err string, message string) {
	w.Header().Set("Content-Type", "application/json")
	w.WriteHeader(status)

	response := ErrorResponse{
		Error:   err,
		Message: message,
	}

	json.NewEncoder(w).Encode(response)
}

// WriteValidationError writes validation error details.
func WriteValidationError(w http.ResponseWriter, errors []ValidationError) {
	w.Header().Set("Content-Type", "application/json")
	w.WriteHeader(http.StatusBadRequest)

	response := ValidationErrorResponse{
		Error:  "validation_failed",
		Errors: errors,
	}

	json.NewEncoder(w).Encode(response)
}

// WriteJSON writes a successful JSON response.
func WriteJSON(w http.ResponseWriter, status int, data interface{}) {
	w.Header().Set("Content-Type", "application/json")
	w.WriteHeader(status)
	json.NewEncoder(w).Encode(data)
}
```

This error format provides structure clients can rely on. The `error` field contains a machine-readable error code. The `message` field provides human-readable context. The `details` field can include additional debugging information. Validation errors use a specialized format listing field-level problems, enabling clients to highlight incorrect form fields.

  

## Section 3: Router Setup with Chi

While Go's standard library handles routing adequately for simple applications, production systems need hierarchical URL structures, middleware composition, and URL parameter extraction. The chi router provides these features with an ergonomic API that feels natural to Go developers.

### Understanding Chi's Design

Chi builds on `net/http` conventions rather than replacing them. Routes are standard HTTP handlers. Middleware are functions that return handlers. This design enables mixing chi-specific features with standard library code seamlessly.

Chi's hierarchical routing matches URL structure to code organization. Route groups under common paths share middleware and configuration. Sub-routers handle specific resource types, keeping related endpoints together. This organization makes large APIs maintainable by grouping related functionality.

  

```go
// internal/server/router.go
package server

import (
	"net/http"
	"time"

	"github.com/go-chi/chi/v5"
	"github.com/go-chi/chi/v5/middleware"
)

// NewRouter creates the application router with all routes and middleware.
func NewRouter(
	userHandler *UserHandler,
	postHandler *PostHandler,
	authHandler *AuthHandler,
) http.Handler {
	r := chi.NewRouter()

	// Global middleware applies to all requests
	r.Use(middleware.RequestID)                 // Add request ID for tracing
	r.Use(middleware.RealIP)                    // Extract real client IP
	r.Use(middleware.Logger)                    // Log all requests
	r.Use(middleware.Recoverer)                 // Recover from panics
	r.Use(middleware.Timeout(60 * time.Second)) // Timeout long requests

	// Health check endpoint for load balancers and monitoring
	r.Get("/health", func(w http.ResponseWriter, r *http.Request) {
		w.WriteHeader(http.StatusOK)
		w.Write([]byte("OK"))
	})

	// Ready check endpoint for orchestration systems
	r.Get("/ready", func(w http.ResponseWriter, r *http.Request) {
		// Check database connectivity, external services, etc.
		w.WriteHeader(http.StatusOK)
		w.Write([]byte("READY"))
	})

	// API routes under /api/v1 namespace
	r.Route("/api/v1", func(r chi.Router) {
		// Public authentication endpoints
		r.Post("/auth/register", authHandler.Register)
		r.Post("/auth/login", authHandler.Login)

		// Protected routes requiring authentication
		r.Group(func(r chi.Router) {
			r.Use(authHandler.RequireAuth) // Authentication middleware

			// User routes
			r.Route("/users", func(r chi.Router) {
				r.Get("/", userHandler.List)    // GET /api/v1/users
				r.Post("/", userHandler.Create) // POST /api/v1/users

				r.Route("/{id}", func(r chi.Router) {
					r.Get("/", userHandler.Get)       // GET /api/v1/users/123
					r.Put("/", userHandler.Update)    // PUT /api/v1/users/123
					r.Delete("/", userHandler.Delete) // DELETE /api/v1/users/123
				})
			})

			// Post routes
			r.Route("/posts", func(r chi.Router) {
				r.Get("/", postHandler.List)    // GET /api/v1/posts
				r.Post("/", postHandler.Create) // POST /api/v1/posts

				r.Route("/{id}", func(r chi.Router) {
					r.Get("/", postHandler.Get)       // GET /api/v1/posts/456
					r.Put("/", postHandler.Update)    // PUT /api/v1/posts/456
					r.Delete("/", postHandler.Delete) // DELETE /api/v1/posts/456

					// Nested actions on posts
					r.Post("/publish", postHandler.Publish)     // POST /api/v1/posts/456/publish
					r.Delete("/publish", postHandler.Unpublish) // DELETE /api/v1/posts/456/publish
				})
			})
		})

		// Public read-only routes don't require authentication
		r.Group(func(r chi.Router) {
			r.Get("/posts/published", postHandler.ListPublished)
			r.Get("/posts/{slug}", postHandler.GetBySlug)
		})
	})

	return r
}
```

This router organization provides clear structure. Health and readiness checks live at the root for easy access by infrastructure. The API lives under `/api/v1`, enabling future versions at `/api/v2` without breaking existing clients. Authentication middleware protects sensitive operations while allowing public read access. Related endpoints group together under route blocks.

### Testing Router Configuration

Router tests verify that routes map to correct handlers and middleware applies appropriately. These tests catch routing configuration errors before deployment.

  

```go
// internal/server/router_test.go
package server

import (
	"net/http"
	"net/http/httptest"
	"testing"
)

func TestRouter_HealthCheck(t *testing.T) {
	router := NewRouter(
		NewMockUserHandler(),
		NewMockPostHandler(),
		NewMockAuthHandler(),
	)

	req := httptest.NewRequest(http.MethodGet, "/health", nil)
	rr := httptest.NewRecorder()

	router.ServeHTTP(rr, req)

	if rr.Code != http.StatusOK {
		t.Errorf("Status = %d; want %d", rr.Code, http.StatusOK)
	}

	if rr.Body.String() != "OK" {
		t.Errorf("Body = %q; want %q", rr.Body.String(), "OK")
	}
}

func TestRouter_AuthenticationRequired(t *testing.T) {
	router := NewRouter(
		NewMockUserHandler(),
		NewMockPostHandler(),
		NewMockAuthHandler(),
	)

	// Request to protected endpoint without authentication
	req := httptest.NewRequest(http.MethodGet, "/api/v1/users", nil)
	rr := httptest.NewRecorder()

	router.ServeHTTP(rr, req)

	// Should return 401 Unauthorized
	if rr.Code != http.StatusUnauthorized {
		t.Errorf("Status = %d; want %d", rr.Code, http.StatusUnauthorized)
	}
}

func TestRouter_URLParameterExtraction(t *testing.T) {
	mockHandler := NewMockUserHandler()
	router := NewRouter(mockHandler, NewMockPostHandler(), NewMockAuthHandler())

	req := httptest.NewRequest(http.MethodGet, "/api/v1/users/123", nil)
	req.Header.Set("Authorization", "Bearer valid-token")
	rr := httptest.NewRecorder()

	router.ServeHTTP(rr, req)

	// Verify handler received correct ID parameter
	if mockHandler.lastID != "123" {
		t.Errorf("Handler received ID = %q; want %q", mockHandler.lastID, "123")
	}
}
```

  

## Section 4: Handler Implementation Patterns

Handlers translate HTTP requests into business operations and format results as HTTP responses. Well-structured handlers separate concerns: parsing requests, validating inputs, calling business logic, handling errors, and formatting responses. This separation makes handlers testable and maintainable.

### Handler Structure and Dependency Injection

Handlers receive dependencies through struct fields, enabling testing with mock implementations. The handler struct holds service interfaces, configuration, and logging facilities. Handler methods receive `http.ResponseWriter` and `*http.Request` parameters, satisfying the `http.Handler` interface.

  

```go
// internal/handler/user_handler.go
package handler

import (
	"context"
	"encoding/json"
	"net/http"
	"strconv"

	"github.com/go-chi/chi/v5"
	"your-module/internal/response"
	"your-module/internal/service"
)

// UserHandler handles HTTP requests for user operations.
type UserHandler struct {
	service service.UserService
	logger  Logger
}

// NewUserHandler creates a user handler with dependencies.
func NewUserHandler(service service.UserService, logger Logger) *UserHandler {
	return &UserHandler{
		service: service,
		logger:  logger,
	}
}

// List handles GET /users with pagination.
func (h *UserHandler) List(w http.ResponseWriter, r *http.Request) {
	ctx := r.Context()

	// Parse and validate query parameters
	limit, err := parseQueryInt(r, "limit", 20)
	if err != nil {
		response.WriteError(w, http.StatusBadRequest, "invalid_limit", "limit must be a positive integer")
		return
	}

	offset, err := parseQueryInt(r, "offset", 0)
	if err != nil {
		response.WriteError(w, http.StatusBadRequest, "invalid_offset", "offset must be a non-negative integer")
		return
	}

	// Validate ranges
	if limit > 100 {
		response.WriteError(w, http.StatusBadRequest, "limit_exceeded", "limit cannot exceed 100")
		return
	}

	if limit < 1 {
		response.WriteError(w, http.StatusBadRequest, "invalid_limit", "limit must be at least 1")
		return
	}

	// Call service layer
	users, err := h.service.List(ctx, limit, offset)
	if err != nil {
		h.logger.Error("Failed to list users", "error", err)
		response.WriteError(w, http.StatusInternalServerError, "internal_error", "Failed to retrieve users")
		return
	}

	// Format response with metadata
	responseData := map[string]interface{}{
		"users":  users,
		"limit":  limit,
		"offset": offset,
		"count":  len(users),
	}

	response.WriteJSON(w, http.StatusOK, responseData)
}

// Get handles GET /users/{id}.
func (h *UserHandler) Get(w http.ResponseWriter, r *http.Request) {
	ctx := r.Context()

	// Extract URL parameter
	idStr := chi.URLParam(r, "id")
	id, err := strconv.ParseInt(idStr, 10, 64)
	if err != nil {
		response.WriteError(w, http.StatusBadRequest, "invalid_id", "User ID must be a valid integer")
		return
	}

	// Retrieve user
	user, err := h.service.GetByID(ctx, id)
	if err == service.ErrNotFound {
		response.WriteError(w, http.StatusNotFound, "user_not_found", "User does not exist")
		return
	}
	if err != nil {
		h.logger.Error("Failed to get user", "id", id, "error", err)
		response.WriteError(w, http.StatusInternalServerError, "internal_error", "Failed to retrieve user")
		return
	}

	response.WriteJSON(w, http.StatusOK, user)
}

// Create handles POST /users.
func (h *UserHandler) Create(w http.ResponseWriter, r *http.Request) {
	ctx := r.Context()

	// Parse request body
	var req service.CreateUserRequest
	if err := json.NewDecoder(r.Body).Decode(&req); err != nil {
		response.WriteError(w, http.StatusBadRequest, "invalid_body", "Request body must be valid JSON")
		return
	}
	defer r.Body.Close()

	// Validate request through service layer
	if err := h.service.ValidateCreateRequest(req); err != nil {
		if validationErr, ok := err.(*service.ValidationError); ok {
			response.WriteValidationError(w, convertValidationErrors(validationErr))
			return
		}
		response.WriteError(w, http.StatusBadRequest, "invalid_request", err.Error())
		return
	}

	// Create user
	user, err := h.service.Create(ctx, req)
	if err == service.ErrDuplicateEmail {
		response.WriteError(w, http.StatusConflict, "email_exists", "Email address already registered")
		return
	}
	if err == service.ErrDuplicateUsername {
		response.WriteError(w, http.StatusConflict, "username_exists", "Username already taken")
		return
	}
	if err != nil {
		h.logger.Error("Failed to create user", "error", err)
		response.WriteError(w, http.StatusInternalServerError, "internal_error", "Failed to create user")
		return
	}

	// Return created user with 201 status
	w.Header().Set("Location", fmt.Sprintf("/api/v1/users/%d", user.ID))
	response.WriteJSON(w, http.StatusCreated, user)
}

// Update handles PUT /users/{id}.
func (h *UserHandler) Update(w http.ResponseWriter, r *http.Request) {
	ctx := r.Context()

	// Extract and validate ID
	idStr := chi.URLParam(r, "id")
	id, err := strconv.ParseInt(idStr, 10, 64)
	if err != nil {
		response.WriteError(w, http.StatusBadRequest, "invalid_id", "User ID must be a valid integer")
		return
	}

	// Parse request body
	var req service.UpdateUserRequest
	if err := json.NewDecoder(r.Body).Decode(&req); err != nil {
		response.WriteError(w, http.StatusBadRequest, "invalid_body", "Request body must be valid JSON")
		return
	}
	defer r.Body.Close()

	// Set ID from URL (prevents mismatched ID in body)
	req.ID = id

	// Validate request
	if err := h.service.ValidateUpdateRequest(req); err != nil {
		if validationErr, ok := err.(*service.ValidationError); ok {
			response.WriteValidationError(w, convertValidationErrors(validationErr))
			return
		}
		response.WriteError(w, http.StatusBadRequest, "invalid_request", err.Error())
		return
	}

	// Update user
	user, err := h.service.Update(ctx, req)
	if err == service.ErrNotFound {
		response.WriteError(w, http.StatusNotFound, "user_not_found", "User does not exist")
		return
	}
	if err == service.ErrDuplicateEmail {
		response.WriteError(w, http.StatusConflict, "email_exists", "Email address already in use")
		return
	}
	if err == service.ErrDuplicateUsername {
		response.WriteError(w, http.StatusConflict, "username_exists", "Username already taken")
		return
	}
	if err != nil {
		h.logger.Error("Failed to update user", "id", id, "error", err)
		response.WriteError(w, http.StatusInternalServerError, "internal_error", "Failed to update user")
		return
	}

	response.WriteJSON(w, http.StatusOK, user)
}

// Delete handles DELETE /users/{id}.
func (h *UserHandler) Delete(w http.ResponseWriter, r *http.Request) {
	ctx := r.Context()

	// Extract and validate ID
	idStr := chi.URLParam(r, "id")
	id, err := strconv.ParseInt(idStr, 10, 64)
	if err != nil {
		response.WriteError(w, http.StatusBadRequest, "invalid_id", "User ID must be a valid integer")
		return
	}

	// Delete user
	err = h.service.Delete(ctx, id)
	if err == service.ErrNotFound {
		response.WriteError(w, http.StatusNotFound, "user_not_found", "User does not exist")
		return
	}
	if err != nil {
		h.logger.Error("Failed to delete user", "id", id, "error", err)
		response.WriteError(w, http.StatusInternalServerError, "internal_error", "Failed to delete user")
		return
	}

	// 204 No Content indicates successful deletion with no response body
	w.WriteHeader(http.StatusNoContent)
}

// Helper functions

func parseQueryInt(r *http.Request, key string, defaultValue int) (int, error) {
	value := r.URL.Query().Get(key)
	if value == "" {
		return defaultValue, nil
	}

	parsed, err := strconv.Atoi(value)
	if err != nil {
		return 0, err
	}

	return parsed, nil
}

func convertValidationErrors(err *service.ValidationError) []response.ValidationError {
	var errors []response.ValidationError
	for field, message := range err.Fields {
		errors = append(errors, response.ValidationError{
			Field:   field,
			Message: message,
		})
	}
	return errors
}
```

This handler implementation demonstrates several important patterns. Input validation occurs at multiple levels: parameter parsing validates types, range checks validate values, and service-layer validation applies business rules. Error handling differentiates client errors (400, 404, 409) from server errors (500), providing appropriate status codes. Logging captures errors for debugging without exposing internal details to clients. Response formatting remains consistent across all endpoints.

### Testing Handlers with httptest

Handler tests verify request processing, error handling, and response formatting without running actual HTTP servers. The `httptest` package provides tools for creating requests and recording responses, enabling fast, isolated handler testing.

  

```go
// internal/handler/user_handler_test.go
package handler

import (
	"bytes"
	"encoding/json"
	"net/http"
	"net/http/httptest"
	"testing"

	"github.com/go-chi/chi/v5"
)

func TestUserHandler_List(t *testing.T) {
	// Create mock service
	mockService := &MockUserService{
		users: []*User{
			{ID: 1, Email: "user1@example.com", Username: "user1"},
			{ID: 2, Email: "user2@example.com", Username: "user2"},
		},
	}

	handler := NewUserHandler(mockService, &MockLogger{})

	tests := []struct {
		name       string
		query      string
		wantStatus int
		wantCount  int
	}{
		{
			name:       "default pagination",
			query:      "",
			wantStatus: http.StatusOK,
			wantCount:  2,
		},
		{
			name:       "custom limit",
			query:      "?limit=1&offset=0",
			wantStatus: http.StatusOK,
			wantCount:  2,
		},
		{
			name:       "limit too high",
			query:      "?limit=200",
			wantStatus: http.StatusBadRequest,
		},
		{
			name:       "invalid limit",
			query:      "?limit=abc",
			wantStatus: http.StatusBadRequest,
		},
	}

	for _, tt := range tests {
		t.Run(tt.name, func(t *testing.T) {
			req := httptest.NewRequest(http.MethodGet, "/users"+tt.query, nil)
			rr := httptest.NewRecorder()

			handler.List(rr, req)

			if rr.Code != tt.wantStatus {
				t.Errorf("Status = %d; want %d", rr.Code, tt.wantStatus)
			}

			if tt.wantStatus == http.StatusOK {
				var response map[string]interface{}
				json.NewDecoder(rr.Body).Decode(&response)

				users := response["users"].([]interface{})
				if len(users) != tt.wantCount {
					t.Errorf("User count = %d; want %d", len(users), tt.wantCount)
				}
			}
		})
	}
}

func TestUserHandler_Get(t *testing.T) {
	user := &User{ID: 1, Email: "test@example.com", Username: "testuser"}
	mockService := &MockUserService{user: user}
	handler := NewUserHandler(mockService, &MockLogger{})

	tests := []struct {
		name       string
		id         string
		setupMock  func(*MockUserService)
		wantStatus int
	}{
		{
			name:       "user found",
			id:         "1",
			setupMock:  func(m *MockUserService) { m.user = user },
			wantStatus: http.StatusOK,
		},
		{
			name:       "user not found",
			id:         "999",
			setupMock:  func(m *MockUserService) { m.err = service.ErrNotFound },
			wantStatus: http.StatusNotFound,
		},
		{
			name:       "invalid id",
			id:         "abc",
			setupMock:  func(m *MockUserService) {},
			wantStatus: http.StatusBadRequest,
		},
	}

	for _, tt := range tests {
		t.Run(tt.name, func(t *testing.T) {
			tt.setupMock(mockService)

			req := httptest.NewRequest(http.MethodGet, "/users/"+tt.id, nil)
			rr := httptest.NewRecorder()

			// Set up chi context with URL parameter
			rctx := chi.NewRouteContext()
			rctx.URLParams.Add("id", tt.id)
			req = req.WithContext(context.WithValue(req.Context(), chi.RouteCtxKey, rctx))

			handler.Get(rr, req)

			if rr.Code != tt.wantStatus {
				t.Errorf("Status = %d; want %d", rr.Code, tt.wantStatus)
			}

			if tt.wantStatus == http.StatusOK {
				var result User
				json.NewDecoder(rr.Body).Decode(&result)

				if result.Email != user.Email {
					t.Errorf("Email = %q; want %q", result.Email, user.Email)
				}
			}
		})
	}
}

func TestUserHandler_Create(t *testing.T) {
	mockService := &MockUserService{}
	handler := NewUserHandler(mockService, &MockLogger{})

	tests := []struct {
		name       string
		body       interface{}
		setupMock  func(*MockUserService)
		wantStatus int
	}{
		{
			name: "valid user",
			body: map[string]string{
				"email":    "new@example.com",
				"username": "newuser",
				"password": "SecureP@ss123",
			},
			setupMock: func(m *MockUserService) {
				m.user = &User{ID: 1, Email: "new@example.com"}
			},
			wantStatus: http.StatusCreated,
		},
		{
			name:       "invalid json",
			body:       "invalid json",
			setupMock:  func(m *MockUserService) {},
			wantStatus: http.StatusBadRequest,
		},
		{
			name: "duplicate email",
			body: map[string]string{
				"email":    "existing@example.com",
				"username": "newuser",
				"password": "SecureP@ss123",
			},
			setupMock: func(m *MockUserService) {
				m.err = service.ErrDuplicateEmail
			},
			wantStatus: http.StatusConflict,
		},
	}

	for _, tt := range tests {
		t.Run(tt.name, func(t *testing.T) {
			tt.setupMock(mockService)

			var bodyBytes []byte
			if str, ok := tt.body.(string); ok {
				bodyBytes = []byte(str)
			} else {
				bodyBytes, _ = json.Marshal(tt.body)
			}

			req := httptest.NewRequest(http.MethodPost, "/users", bytes.NewReader(bodyBytes))
			req.Header.Set("Content-Type", "application/json")
			rr := httptest.NewRecorder()

			handler.Create(rr, req)

			if rr.Code != tt.wantStatus {
				t.Errorf("Status = %d; want %d", rr.Code, tt.wantStatus)
			}

			if tt.wantStatus == http.StatusCreated {
				location := rr.Header().Get("Location")
				if location == "" {
					t.Error("Location header should be set for created resources")
				}
			}
		})
	}
}

func TestUserHandler_Update(t *testing.T) {
	mockService := &MockUserService{}
	handler := NewUserHandler(mockService, &MockLogger{})

	tests := []struct {
		name       string
		id         string
		body       map[string]string
		setupMock  func(*MockUserService)
		wantStatus int
	}{
		{
			name: "successful update",
			id:   "1",
			body: map[string]string{
				"email":    "updated@example.com",
				"username": "updated",
			},
			setupMock: func(m *MockUserService) {
				m.user = &User{ID: 1, Email: "updated@example.com"}
			},
			wantStatus: http.StatusOK,
		},
		{
			name: "user not found",
			id:   "999",
			body: map[string]string{
				"email":    "updated@example.com",
				"username": "updated",
			},
			setupMock: func(m *MockUserService) {
				m.err = service.ErrNotFound
			},
			wantStatus: http.StatusNotFound,
		},
	}

	for _, tt := range tests {
		t.Run(tt.name, func(t *testing.T) {
			tt.setupMock(mockService)

			bodyBytes, _ := json.Marshal(tt.body)
			req := httptest.NewRequest(http.MethodPut, "/users/"+tt.id, bytes.NewReader(bodyBytes))
			req.Header.Set("Content-Type", "application/json")
			rr := httptest.NewRecorder()

			// Set up chi context
			rctx := chi.NewRouteContext()
			rctx.URLParams.Add("id", tt.id)
			req = req.WithContext(context.WithValue(req.Context(), chi.RouteCtxKey, rctx))

			handler.Update(rr, req)

			if rr.Code != tt.wantStatus {
				t.Errorf("Status = %d; want %d", rr.Code, tt.wantStatus)
			}
		})
	}
}

func TestUserHandler_Delete(t *testing.T) {
	mockService := &MockUserService{}
	handler := NewUserHandler(mockService, &MockLogger{})

	tests := []struct {
		name       string
		id         string
		setupMock  func(*MockUserService)
		wantStatus int
	}{
		{
			name:       "successful deletion",
			id:         "1",
			setupMock:  func(m *MockUserService) { m.err = nil },
			wantStatus: http.StatusNoContent,
		},
		{
			name:       "user not found",
			id:         "999",
			setupMock:  func(m *MockUserService) { m.err = service.ErrNotFound },
			wantStatus: http.StatusNotFound,
		},
		{
			name:       "invalid id",
			id:         "abc",
			setupMock:  func(m *MockUserService) {},
			wantStatus: http.StatusBadRequest,
		},
	}

	for _, tt := range tests {
		t.Run(tt.name, func(t *testing.T) {
			tt.setupMock(mockService)

			req := httptest.NewRequest(http.MethodDelete, "/users/"+tt.id, nil)
			rr := httptest.NewRecorder()

			// Set up chi context
			rctx := chi.NewRouteContext()
			rctx.URLParams.Add("id", tt.id)
			req = req.WithContext(context.WithValue(req.Context(), chi.RouteCtxKey, rctx))

			handler.Delete(rr, req)

			if rr.Code != tt.wantStatus {
				t.Errorf("Status = %d; want %d", rr.Code, tt.wantStatus)
			}
		})
	}
}
```

These tests comprehensively verify handler behavior. Table-driven tests cover success cases, various error conditions, and edge cases. Mock services enable testing without database dependencies. `httptest.NewRequest` and `httptest.NewRecorder` enable testing HTTP semantics without network overhead. Context manipulation sets up URL parameters as chi would in production.

  

## Section 5: Middleware Patterns

Middleware functions wrap handlers to provide cross-cutting concerns—functionality needed across many endpoints. Logging, authentication, rate limiting, and CORS handling are classic middleware use cases. Middleware enables you to write these concerns once and apply them consistently.

### Understanding Middleware Composition

Middleware in Go follows a simple pattern: a function that accepts a handler and returns a handler. The returned handler performs some operation before and/or after calling the wrapped handler. This pattern composes elegantly—multiple middleware wrap each other to create pipelines.

```go
// Middleware signature
func Middleware(next http.Handler) http.Handler {
	return http.HandlerFunc(func(w http.ResponseWriter, r *http.Request) {
		// Before handler
		next.ServeHTTP(w, r)
		// After handler
	})
}
```

### Request Logging Middleware

Request logs are most useful when they are structured and complete enough to correlate with metrics and traces. Capture method, route, status, latency, request id, and principal information where available. Consistent log shape is what makes post-incident analysis fast and reliable.


Logging middleware records information about every request, enabling debugging and monitoring. Production logging middleware captures request method, path, status code, response size, and duration.

  

```go
// internal/middleware/logger.go
package middleware

import (
	"log"
	"net/http"
	"time"
)

// responseWriter wraps http.ResponseWriter to capture status code.
type responseWriter struct {
	http.ResponseWriter
	statusCode int
	written    int
}

func (rw *responseWriter) WriteHeader(code int) {
	rw.statusCode = code
	rw.ResponseWriter.WriteHeader(code)
}

func (rw *responseWriter) Write(b []byte) (int, error) {
	n, err := rw.ResponseWriter.Write(b)
	rw.written += n
	return n, err
}

// Logger logs HTTP requests with timing and status information.
func Logger(logger *log.Logger) func(http.Handler) http.Handler {
	return func(next http.Handler) http.Handler {
		return http.HandlerFunc(func(w http.ResponseWriter, r *http.Request) {
			start := time.Now()

			// Wrap response writer to capture status
			wrapped := &responseWriter{
				ResponseWriter: w,
				statusCode:     http.StatusOK,
			}

			// Call next handler
			next.ServeHTTP(wrapped, r)

			// Log request details
			duration := time.Since(start)
			logger.Printf(
				"%s %s %d %d bytes %v",
				r.Method,
				r.URL.Path,
				wrapped.statusCode,
				wrapped.written,
				duration,
			)
		})
	}
}
```

### Authentication Middleware

Authentication middleware defines a hard trust boundary. Keep it strict about token parsing and validation, and keep handlers free of auth parsing logic so authorization decisions stay consistent. Centralized auth checks reduce drift and close security gaps that appear when logic is duplicated.


Authentication middleware verifies that requests include valid credentials. Authenticated requests proceed to handlers; unauthenticated requests receive 401 responses immediately.

  

```go
// internal/middleware/auth.go
package middleware

import (
	"context"
	"net/http"
	"strings"

	"your-module/internal/auth"
	"your-module/internal/response"
)

// contextKey represents context keys for this package.
type contextKey string

const (
	userIDKey   contextKey = "user_id"
	userRoleKey contextKey = "user_role"
)

// RequireAuth verifies JWT tokens and adds user information to context.
func RequireAuth(tokenService auth.TokenService) func(http.Handler) http.Handler {
	return func(next http.Handler) http.Handler {
		return http.HandlerFunc(func(w http.ResponseWriter, r *http.Request) {
			// Extract authorization header
	

Production-Ready-Go-Final_Manuscript.md
Displaying Production-Ready-Go-Final_Manuscript.md.
