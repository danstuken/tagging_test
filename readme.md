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

## What's the difference between lightweight and annotated tags?

Lightweight tags are meant for local or private tags, they are not pushed to remotes and they just contain a commit's SHA-1
An annotated tag can be used for a release, they contain the SHA-1 of an annotation object that contains date, tagger, message and the commit's SHA-1

So we want to use annotated tags.

## A problem though.
All of the tags in this repo just point to commit's not other objects.
What gives?

Try: 
1) creating the tag object: hub api -X POST /repos/danstuken/tagging_test/git/tags -F....
   a) returns SHA-1 of created object
2) creating tag ref for tag object: hub api -X POST /repos/danstuken/tagging_test/git/refs -F....<sha-1> from previous.
