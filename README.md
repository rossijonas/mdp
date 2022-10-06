<h1 align="center">mdp (Markdown Preview)</h1>

*<p align="center">A Markdown Preview CLI Tool Built in Go</p>*

<p align="center">[![Actions Status](https://github.com/rossijonas/mdp/workflows/Test/badge.svg)](https://github.com/rossijonas/mdp/actions)[![Actions Status](https://github.com/rossijonas/mdp/workflows/Build/badge.svg)](https://github.com/rossijonas/mdp/actions)</p>

## About

Use the `mdp` CLI tool to preview a Markdown file in the browser.

### Features:

- Cross platform:  Linux / Macos / Windows.

- Convert a Markdown file into an HTML file.

- Support custom templates.

- `mdp` uses [bluemonday](https://github.com/microcosm-cc/bluemonday) to sanitize the Markdown content creating a safe HTML file.

_(This is an exercise from the book "Powerful Command-Line Applications in Go".)_

## Installation

### Requirements:

- [Go](https://go.dev/) version 1.18.6 (or above)

### How to install:

- Run: 

  ```
  $ go install github.com/rossijonas/mdp@latest
  ```

## Usage

### Preview a Markdown file in the browser:

```
$ mdp -file MyFile.md
```

### Convert a Markdown file into an HTML file:

Using the `-s` (skip preview) flag, `mdp` generates an HTML file from the given Markdown file and saves the output file in `/tmp` directory.

```
$ mdp -s -file MyFile.md
/tmp/mdp4030496412.html  # the HTML file path is printed to the terminal
```

### Use a custom template file to generate the HTML:

A custom template file may be used to provide custom styles and layouts. 

`mdp` accepts a Go [html/template](https://pkg.go.dev/html/template) file provided using the `-t` flag.

```
$ mdp -file MyFile.md -t template.tmpl
```
The content of the markdown file must be defined in the template file inside de `<body>` tags as `{{ .Body }}`.

  Ex.: `custom.tmpl`

  ```
  ...
    </head>
    <body>
      {{ .Body }}
    </body>
    <footer>
      <p>© 2022</p>
    </footer>
  ```

## Backlog

- Add example Gif to README file.

- Add test case testing an alternate template file.

- Update the default template by adding another field that shows the name of the file being previewed.

- Allow the user to specify a default template using an environment variable.

