Test repo pull/push

The New-Wave Solution
A superior solution—though less well understood, and which requires a bit more OS/tool support—is to use POSIX extended attributes. I’ve only come to this area fairly recently, so my knowledge here isn’t as hot as it could be. But basically, an extended ACL is the ability to set permissions on more than just the 3 default slots (user/group/other).

So once again, create your group, then run:

```bash
setfacl -R -m g:<whatever group>:rwX gitrepo
find gitrepo -type d | xargs setfacl -R -m d:g:<whatever group>:rwX
```


This sets up the extended ACL for the group so that the group members can read/write/access whatever files are already there (the first line); then, also tell all existing directories that new files should have this same ACL applied (the second line).

Hope that gets you on your way.


