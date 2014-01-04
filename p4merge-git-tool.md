Setting up [p4merge](http://www.perforce.com/product/components/perforce-visual-merge-and-diff-tools)
as diff and merge tool on Windows. Tried for Git version `1.8.4.msysgit.0`. 

Two alternatives are explained: using the command line, and directly editing the config file.

### Setting up from the command line

Being the installation path `"C:Program Files\Perforce\p4merge.exe"`, just run:
```
$ git config --global diff.tool p4merge
$ git config --global difftool.p4merge.path 'C:\Program Files\Perforce\p4merge.exe'
```
```
$ git config --global merge.tool p4merge
$ git config --global mergetool.p4merge.path 'C:\Program Files\Perforce\p4merge.exe'
```

#### Possible error if other approaches have been tried before

Apparently in earlier versions `mergetool.p4merge.cmd` needed to be provided instead of the path, 
but doesn't work anymore [due to Git trying to support p4merge](http://stackoverflow.com/questions/426026/git-on-windows-how-do-you-set-up-a-mergetool/436040#436040):

> setting `mergetool.p4merge.cmd` will not work anymore since Git has started 
> trying to support p4merge, see `libexec/git-core/git-mergetool--lib`. 
> instead it directly uses `mergetool.p4merge.path`

If that option is already set (check if `git config --global --get mergetool.p4merge.cmd` prints a value), 
it needs to be removed: 

```
$ git config --global --unset mergetool.p4merge.cmd
```

The same applies to `difftool.p4merge.cmd`.

### Editing the global configuration file

Open `~/.gitconfig` (`git config --global --edit`) and add or change: 

```
[merge]
	tool = p4merge
[mergetool "p4merge"]
	path = C:\\Program Files\\Perforce\\p4merge.exe
```
```
[diff]
	tool = p4merge
[difftool "p4merge"]
	path = C:\\Program Files\\Perforce\\p4merge.exe
```

As before, if inside `[mergetool "p4merge"]` or `[difftool "p4merge"]` there is 
a `cmd` option, it needs to be removed so that Git doesn't try to execute it.
