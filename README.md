# lilypond-docker
Run 64-bit Lilypond in Frescobaldi on MacOS 10.5 Catalina or Windows via Docker

Based on https://kylebaldw.in/posts/2019/running-lilypond-on-catalina/

In ly-link scripts, added an additional argument to docker: `-v "$HOME/.lily:$HOME/.lily"` to allow for custom Lilypond include files, assumed to be within ~/.lily. Modify accordingly if you keep your Lilypond snippet libraries and stylesheets somewhere else. The include directory gets passed by Frescobaldi as an argument, so it needs to be mounted within the Docker container at the same absolute path.

To get Frescobaldi's Lilypond version detection to work, you need to export the Frescobaldi install path so it can be mounted in Docker (i.e. in Docker File Sharing settings, add Frescobaldi.app). This is because when Frescobaldi calls `lilypond --version` the working directory is the Frescobaldi install location. The ly-link script will try to have Docker mount that location, and it will error if it doesn't have permission.

## To Do

No reason this approach shouldn't also work for Windows, but ly-link scripts will need to be re-written.
