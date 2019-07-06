## Welcome.

My name is Nathan Disidore.
This repo contains my current resume, written in LaTex. This was my first step into the Tex world, written as a personal challenge to mirror an old Word Doc version, in the spirit of portability and why-not-itude.

### Latest.
The latest version is always tagged as the latest release on this github repo and can always be found at the following url:
https://github.com/ndisidore/super-duper-resume/releases/latest

## Development.

### Compiling.

Necessary packages to compile
```bash
sudo dnf install texlive-scheme-basic texlive-collection-fontsrecommended texlive-titlesec texlive-datatool \
                 texlive-bold-extra texlive-cm-mf-extra-bold texlive-cm-lgc texlive-cmbright \
                 texlive-cmexb texlive-cmll texlive-cmpica texlive-cmsrb texlive-cmtiup
```
And then compilation is as easy as
```bash
pdflatex resume.tex
```

### Live Updates.

You can react to changes in the source latex file using `inotifywait` program from `inotify-tools`

```bash
while inotifywait -e close_write resume.tex; do; echo "Changes to source detected, recompiling...."; pdflatex ./resume.tex >| ./compile.log && echo "Compliation successful" || echo "Complition Failed"; done
```

### Linting.

For syntax checking/linting, ensure the `texlive-chktex` package in installed, then run `chktex resume.tex`
For spell checking, ensure the `aspell aspell-en` packages are installed, then run `aspell -t -c resume.tex`
