# Commit and push after meaningful changes

Whenever you make a meaningful change to code, configuration, build files, or docs, commit and push it immediately. Do this in the same turn, without waiting to be asked.

## What counts as meaningful
- A bug fix, feature, refactor, or build/config change that you have made and validated (for example, the build or tests pass).
- Skip commits for scratch edits, failed or half-finished experiments, and generated or build artifacts.

## Procedure
1. Run the relevant validation (build, lint, tests) first. Do not commit changes that break it.
2. Stage only the files you changed. Never use `git add -A` or `git commit -a` blindly, and never stage untracked build output.
3. Write a concise commit message: an imperative summary line, plus a short body explaining why when it is not obvious.
4. Push to the current branch's remote immediately after committing.
5. Report the commit hash and the branch you pushed to.

## Submodules
- Commit and push inside the submodule first, then commit the updated submodule pointer in the parent repo, then push the parent. Never push a parent that references a submodule commit that has not been pushed.
- A submodule on a detached HEAD must be put on a named branch before committing.
- If a submodule's `origin` is an upstream you don't own, create a fork under the user's account, add it as a remote, push there, and update `.gitmodules` to point at the fork.
- Existing forks: `modules/s2geometry` and `modules/common` push to the `fork` remote, branch `ppc64le-support`.

## Safety
- Never force-push, rewrite published history, or push to a branch you did not create or are not already working on without asking.
- Never commit secrets, tokens, or credentials. Do not print tokens in output. `GH_TOKEN` is available via `source ~/.bashrc`.
- If the push fails (auth, non-fast-forward, no remote), stop and report the error. Do not work around it destructively.
