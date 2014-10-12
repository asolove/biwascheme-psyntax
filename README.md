Trying to get the portable syntax-case system working in BiwaScheme.

An adventure.

- Got Biwa Scheme working via npm.
- Added the psyntax-r6rs codebase, nothing works because of missing ikarus.
  - `wget https://github.com/liutanyu/ikarus-0.0.3`
    - `./configure` fails from missing libgmp
    - `brew install gmp`
    - `./configure && make && make install` success!
  - `make` psyntax-r6rs succeeds in first target: Happy Happy Joy Joy. 
  - `biwas ./psyntax-r6rs/psyntax.pp` fails from malformed identifiers. e.g. 
  (define #{make-parameter |AKXjRGEA>%V699g&|} '#f)
    - Create ./psyntax-r6rs/pre-built/psyntax-biwa.pp with petite definitions, start fixing what's missing.
      - Define void and eval-core just to get to the point of running the file.
  - `biwas ./psyntax-r6rs/pre-built/psyntax-biwa.pp psyntax-r6rs/examples/hello-world.ss` to test actual expansion working.
    - Change command line interface because running inside biwa inside node.
    - Now missing with-input-from-file when trying to load the hello-world program.
      - Rewrote psyntax's main to just execute inline code instead of loading from a file.
  - `biwas ./psyntax-r6rs/pre-built/psyntax-biwa.pp` with inline code.
    - Executes but missing (error).
      - Biwa doesn't seem to have an error system so just print out the debug info and blow up.
    - Executes further but missing dynamic-wind.
      - Ugh.
    - Now runs through, just can't find the dependency, since it doesn't exist.