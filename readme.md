# Test Repo

## Repo exists soley for gh api spikes.
This is the second commit.

## Looks like we need to tag and then create a ref
for the same commit sha??

## Trying with just the ref
Adding just the ref (hub api -X POST /repos/danstuken/tagging_test/git/refs -F 'ref=refs/tags/second' -F 'sha=c234a9303ea6c794661a41d2531e6058b9ac9ba2')
creates a tag and release (in gh parlance).

The gh api docs for /repos/<owner>/<repo>/git/tags states:
_Note that creating a tag object does not create the reference that makes a tag in Git. If you want to create an annotated tag in Git, you have to do this call to create the tag object, and then create the refs/tags/[tag] reference. If you want to create a lightweight tag, you only have to create the tag reference - this call would be unnecessary._
