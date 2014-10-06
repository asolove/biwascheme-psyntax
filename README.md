Trying to get the portable syntax-case system working in BiwaScheme.

An adventure.

- Got Biwa Scheme working via npm.
- Added the psyntax-r6rs codebase, nothing works because of missing ikarus.
  - `wget https://github.com/liutanyu/ikarus-0.0.3`
    - `./configure` fails from missing libgmp
    - `brew install gmp`
    - `./configure && make && make install` success!
  - `make` psyntax-r6rs succeeds in first target: Happy Happy Joy Joy. 