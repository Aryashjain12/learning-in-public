Week 1 — OSS, Backend Security & Systems Learning
Repositories Explored
Kerno
SecuScan
AegisAI
Open Source Learning
OSS Contribution Workflow

Learned:

difference between forking and cloning repositories
how pull requests work in open source
why upstream remotes are important
how maintainers review PRs
issue assignment does not always mean issue ownership
assigned issues can still remain open if fixes are not merged
AegisAI Learning
Issue Explored

Issue #226 — Information Exposure via verbose exception messages.

Vulnerable Pattern
except Exception as e:
    raise HTTPException(
        status_code=500,
        detail=str(e)
    )
Why This Is Dangerous

Returning raw exception strings directly to API clients can expose:

filesystem paths
database errors
internal architecture details
implementation logic

This is a backend security vulnerability known as Information Exposure / Information Disclosure.

Secure Backend Pattern
except Exception as e:
    logger.exception("Guard scan failed")

    raise HTTPException(
        status_code=500,
        detail="An internal error occurred."
    )
Important Learning
internal debugging logs should stay server-side
API clients should receive sanitized responses
Python indentation directly affects backend control flow
a security fix can fail review due to implementation mistakes
Kerno Learning
Concepts Explored
Cobra CLI flag testing
Go testing structure
Linux-first development workflows
importance of WSL/Linux environments for systems projects
Problems Faced
Windows PowerShell build failures
understanding existing OSS code structure
navigating unfamiliar backend codebases
understanding how maintainers review production code
Biggest Learning

Most open source work is not writing code from scratch.

A large part of engineering involves:

understanding existing architecture
reading code carefully
following project conventions
debugging implementation issues
making minimal but correct changes
Git & GitHub Learning

Commands explored:

git clone ...
git remote add upstream ...
git checkout -b feature-name
git push origin branch-name
Next Focus Areas
backend security
FastAPI
Linux
Go
observability
systems programming
secure API design