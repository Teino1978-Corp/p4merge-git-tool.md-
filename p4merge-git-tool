### Setting up from the command line

Being the installation path `"C:Program Files\Perforce\p4merge.exe"`:

```
$ git config --global diff.tool p4merge
$ git config --global difftool.p4merge.path 'C:\Program Files\Perforce\p4merge.exe'
```
```
$ git config --global merge.tool p4merge
$ git config --global mergetool.p4merge.path 'C:\Program Files\Perforce\p4merge.exe'
```

Apparently in earlier versions `mergetool.p4merge.cmd` needed to be provided instead of the path, 
but doesn't work anymore [due to Git trying to support p4merge](http://stackoverflow.com/questions/426026/git-on-windows-how-do-you-set-up-a-mergetool/436040#436040):

> setting mergetool.p4merge.cmd will not work anymore since Git has started 
> trying to support p4merge, see libexec/git-core/git-mergetool--lib. 
> instead it directly uses mergetool.p4merge.path 

### Updating global config file

Alternatively, to add it directly to the config file open `~/.gitconfig` with an editor: 
```
$ git config --global --edit
```

and add or change: 

```
[merge]
	tool = p4merge
[mergetool "p4merge"]
	path = C:\\Program Files\\Perforce\\p4merge.exe

[diff]
	tool = p4merge
[difftool "p4merge"]
	path = C:\\Program Files\\Perforce\\p4merge.exe
```