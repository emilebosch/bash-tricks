bash-tricks
===========

Just some bash tricks that i learned

Checking error codes from out SSH, just works like every thing else.

```
ssh ${options} -t $server "which docker && which nginx" || die "Docker or NGINX doesnt seem to be installed. Please run provison."
```

Checking for files remotely:

```
ssh ${options} -t $server "test -e $image" || {
 echo "File doesnt exist"
}
```

Making SSH STFU (and bit insecure)

```
options="-i ./storage/keys/id_rsa -o StrictHostKeyChecking=no -o UserKnownHostsFile=/dev/null -o LogLevel=error"
```

Checking for arguments:

```
test -z $1 && echo "name required, listing branches" 1>&2 &&  git branch -a && exit 1
```

Default params:

```
branch=${1:-`git rev-parse --abbrev-ref HEAD`} #given branch or current
```