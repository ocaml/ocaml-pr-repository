# ocaml-pr-repository -- opam remotes for OCaml Pull Requests

The OCaml compiler is developed openly at <https://github.com/ocaml/ocaml>, with
new changes discussed on the pull requests tracker at <https://github.com/ocaml/ocaml/pulls>.

It can be convenient to quickly try out a proposed patch and rapidly get a
package development environment up and running, without having to manually
recompile everything.

This repository contains a set of opam1-format compiler descriptions that are
dynamically generated daily from the list of active PRs in the OCaml GitHub
repository.  They let you switch to any active PR using the
[opam](https://opam.ocaml.org) package manager very easily:

## Usage

First add this repository to your opam package universe:

    $ opam repo add ocaml-pr https://github.com/ocaml/ocaml-pr-repository.git

Then list all the available compilers to find your PR

    $ opam switch --all
    [...]
    -- 4.06.0+pr944                  Added some missing numeric C99-functions to Pervasives
    -- 4.06.0+pr964                  Add Pervasives.pi
    -- 4.06.0+pr974                  Enable msvc64 asmcomp tests
    -- 4.06.0+pr975                  Make the testsuite more paranoid about the results
    -- 4.06.0+trunk+afl              4.06 release branch with afl-fuzz instrumentation
    -- 4.06.0+trunk+flambda          4.06 release branch with flambda activated
    -- 4.06.0+trunk+fp               4.06 release branch with frame-pointers

Then switch to the PR you want to try out:

    $ opam switch 4.06.0+pr944
    $ eval `opam config env`

And that's all you need to do to use the patched compiler.  Once you have
tested the patch, don't forget to comment on the pull request with anything
you've learnt from the usage of the patch.
