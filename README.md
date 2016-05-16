diffsem
=======

This bash script compares the current state of files in a git repository
with a specified commit. Unlike a `git diff`, however, the resulting 
output is a set of files containing the full* source code of all modified
files, where each new or modified line is prepended by a "+". Deleted lines are
not shown.

Written out of a need to present modified source code with highlighted changes 
for a university assignment.

*May silently break for files longer than 100 000 lines.

## Installation
```
cd <directory of your choice>
git clone https://github.com/janibonnevier/diffsem.git
ln -s <said directory of choice>/diffsem /usr/bin/
```

## Usage

`diffsem <repo> <pattern> <commit>`

- `<repo>` - the path to the git repository
- `<pattern>` - grep pattern matching the filenames/paths to be compared
- `<commit>` - the commit to compare with

The generated text files are placed in ./diff (that is, a directory 'diff' 
within the current working directory). Previously generated files are not 
deleted upon a rerun.

### Examples
Compare all files in `repo` to commit `58d92203a2e`:  
`diffsem /path/to/repo * 58d92203a2e`

Compare the contents of the `src` directory of `repo` to commit `58d92203a2e`:  
`diffsem /path/to/repo /src/ 58d92203a2e`

Compare the contents of the `src` and `test` directories of `repo` to commit `58d92203a2e`:  
`diffsem /path/to/repo '/src/\|/test/' 58d92203a2e`  

Compare all .c files in `repo` to commit `58d92203a2e`:  
`diffsem /path/to/repo .c$ 58d92203a2e`

## Dependencies

- git

## History

None.

## License

Copyright (c) 2016 Jani Bonnevier

Released under the terms of the MIT License, see the file "LICENSE".

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
SOFTWARE.
