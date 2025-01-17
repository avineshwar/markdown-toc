# Markdown Table of Contents CLI Generator

- [Introduction](#0b79795d3efc95b9976c7c5b933afce2)
- [Usage](#c64518704ce0c0d5501a45763f464276)
  - [CLI](#91af5705f16502125e8b2187e64202c0)
  - [npm package](#15ba410a3a8e5f948e21856c9bb7f622)
- [Example](#0a52730597fb4ffa01fc117d9e71e3a9)

<!-- Table of contents is made with https://github.com/evgeniy-khist/markdown-toc -->

![npm version](https://img.shields.io/npm/v/md-toc-cli)
![npm bundle size](https://img.shields.io/bundlephobia/min/md-toc-cli)
![npm downloads](https://img.shields.io/npm/dt/md-toc-cli)
![Lines of code](https://img.shields.io/tokei/lines/github/evgeniy-khist/markdown-toc)
![Snyk Vulnerabilities for GitHub Repo](https://img.shields.io/snyk/vulnerabilities/github/evgeniy-khist/markdown-toc)
![GitHub licence](https://img.shields.io/github/license/evgeniy-khist/markdown-toc)

## <a id="0b79795d3efc95b9976c7c5b933afce2"></a>Introduction

Automatically insert or update a clickable table of contents (TOC) into your Markdown documents based on its headings using CLI or JavaScript module.

Table of contents is created from level 2-6 headings and inserted after level 1 heading or at the beginning of the file.
It is expected that there are zero or one level 1 heading.

HTML anchor elements are added to level 2-6 headings to make table of content items clickable, e.g. `<a id="..."></a>`.

## <a id="c64518704ce0c0d5501a45763f464276"></a>Usage

### <a id="91af5705f16502125e8b2187e64202c0"></a>CLI

1. Make sure Node.js 14.x LTS or newer is installed.
2. Install md-toc-cli as a global package
   ```bash
   npm i -g md-toc-cli
   ```
3. Insert table of contents to the `README.md` file in the current directory
   ```bash
   md-toc-cli -i
   ```
4. Read the manual

   ```bash
   $ md-toc-cli --help
   ```

   ```
   md-toc-cli [file]

   Automatically insert or update a clickable table of contents (TOC) into your Mar
   kdown documents based on its headings (levels 2-6).

   Positionals:
   file  Markdown file for inserting or updating table of contents in
                                                   [string] [default: "README.md"]

   Options:
         --version         Show version number                            [boolean]
         --help            Show help                                      [boolean]
     -i, --in-place        Edit file in place            [boolean] [default: false]
     -s, --suffix          The extension of a backup copy. If no extension is suppl
                           ied, the original file is overwritten without making a b
                           ackup. This option implies -i.                  [string]
     -t, --tab-width       The number of spaces per indentation-level
                                                              [number] [default: 2]
     -l, --list-item-sign  Sign used front of line items to create an unordered lis
                           t       [string] [choices: "-", "*", "+"] [default: "-"]
     -n, --no-attribution  Do not add an attribution "Table of contents is made wit
                           h ..."                        [boolean] [default: false]
   ```

### <a id="15ba410a3a8e5f948e21856c9bb7f622"></a>npm package

1. Make sure Node.js 14.x LTS or newer is installed.
2. Install md-toc-cli
   ```bash
   npm i md-toc-cli
   ```
3. Import md-toc-cli
   ```javascript
   const markdownToc = require('md-toc-cli');
   ```
4. Programmatically insert or update the table of contents in a Markdown file
   ```javascript
   await markdownToc.insertOrUpdateTocInFile('README.md', {
     inPlace: false,
     suffix: 'orig',
     tabWidth: 2,
     listItemSymbol: '-',
     noAttribution: false,
   });
   ```
5. Or programmatically insert or update the table of contents in a string with a Markdown content
   ```javascript
   await markdownToc.insertOrUpdateToc(markdownContent, {
     tabWidth: 2,
     listItemSymbol: '-',
     noAttribution: false,
   });
   ```

## <a id="0a52730597fb4ffa01fc117d9e71e3a9"></a>Example

1. Create file `test.md` as follows

   ```markdown
   # Heading 1

   ## Heading 2a

   ### Heading 3aa

   #### Heading 4a

   ##### Heading 5a

   ###### Heading 6a

   ### Heading 3ab

   ## Heading 2b

   ### Heading 3b

   #### Heading 4b

   ## Heading 2c

   ### Heading 3c
   ```

2. Insert table of contents to `test.md` and backup the original file
   ```bash
   md-toc-cli test.md -i -s 'orig'
   ```
3. A backup `test.md.orig` is created for original file `test.md`.
4. A clickable table of contents is inserted into `test.md`

   ```markdown
   # Heading 1

   - [Heading 2a](#62bae9069304b425d6174518f6e08820)
   - [Heading 3aa](#9faaae3ddf5880387d6abbd7854997a8)
     - [Heading 4a](#3cbd898c604d920d4ce96821528c8b1a)
       - [Heading 5a](#cf5e1d8b5dd85fa053ec416763f6bebd)
       - [Heading 6a](#eab2de38622860a06fe06ad545aaf6de)
   - [Heading 3ab](#ce97d28cdc95ab9f084992b83358ae06)
   - [Heading 2b](#4fd8e2d675f1736846acf45b5bcd5db1)
   - [Heading 3b](#c8ec0f1c9a499a10aa077fef74fe2d55)
     - [Heading 4b](#937661bf28aaa176c9d101c6453ad1c5)
   - [Heading 2c](#2f26fb85484044281e7a9d848c8b4eac)
   - [Heading 3c](#190610646bd9620804f17518443a4d54)

   <!-- Table of contents is made with https://github.com/evgeniy-khist/markdown-toc -->

   ## <a id="62bae9069304b425d6174518f6e08820"></a>Heading 2a

   ### <a id="9faaae3ddf5880387d6abbd7854997a8"></a>Heading 3aa

   #### <a id="3cbd898c604d920d4ce96821528c8b1a"></a>Heading 4a

   ##### <a id="cf5e1d8b5dd85fa053ec416763f6bebd"></a>Heading 5a

   ###### <a id="eab2de38622860a06fe06ad545aaf6de"></a>Heading 6a

   ### <a id="ce97d28cdc95ab9f084992b83358ae06"></a>Heading 3ab

   ## <a id="4fd8e2d675f1736846acf45b5bcd5db1"></a>Heading 2b

   ### <a id="c8ec0f1c9a499a10aa077fef74fe2d55"></a>Heading 3b

   #### <a id="937661bf28aaa176c9d101c6453ad1c5"></a>Heading 4b

   ## <a id="2f26fb85484044281e7a9d848c8b4eac"></a>Heading 2c

   ### <a id="190610646bd9620804f17518443a4d54"></a>Heading 3c
   ```

5. Make any change to the level 2-6 headings (e.g. delete level 5-6 headings and rename level 3 headings).
6. Update the table of contents in `test.md`
   ```bash
   md-toc-cli test.md -i
   ```
7. The table of contents in `test.md` is updated according to level 2-6 headings.
