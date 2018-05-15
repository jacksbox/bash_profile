### personal bash profile

contains my bash profile settings seperated into different files.

the local folder is ignored by git and contains private env_vars,
access tokens and other things which should not be on github :)

provided that this repository is located inside of `~/.bash`, the `~/.bash_profile` would look like this:

```#!bash
# include basic bash files
for file in ~/.bash/*
do
  filename="$(basename -- "$file")"
  # ignore folders an gitignore
  if [[ -f $file && "$filename" != ".gitignore" && "$filename" != "README.md" && "$filename" != "LICENSE" ]]; then
    source $file
  fi
done

# include local bash files
for file in ~/.bash/local/*
do
  filename="$(basename -- "$file")"
  # ignore folders an gitignore
  if [[ -f $file && "$filename" != ".gitignore" ]]; then
    source $file
  fi
done
```