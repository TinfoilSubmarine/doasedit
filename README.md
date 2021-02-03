# doasedit
a Bash script replacement for sudoedit using doas.
[Inspired by this Reddit comment.](https://www.reddit.com/r/linux/comments/l6y7nv/is_doas_a_good_alternative_to_sudo/gl4hs42?utm_source=share&utm_medium=web2x&context=3)

##USE AT YOUR OWN RISK! THIS SCRIPT IS VERY ALPHA.
I've already accidentally deleted a configuration file because of a hole in the
script. That hole has obviously been fixed since then, along with the addition
of several other safety measures, but do know that this script (and most other
scripts like it) is doing something very different from how a file is normally
edited in-place. It creates a temporary copy and then overwrites the original
file at the end.

## doas.conf

You'll want to configure `doas` such that it doesn't ask for password at every
line of the script using `doas`. You can accomplish this with either `nopass`
or `persist`, e.g.:
```
# allow users in group 'admin' to use doas without asking for password 
# (more dangerous)
permit nopass :admin
# allow users in group 'admin' to use doas with password, but not asking for
# some time after first successful authentication
permit persist :admin
```
