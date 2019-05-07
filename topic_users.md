<!-- .slide: class="chapter" -->
# Users
<br/><br/>

----

<!-- .slide: class="bulletpoints" -->
## Adding and deleting Users
* User/Groups with `1:n` relations
* Identified by unique **uid** bzw. **gid**  
<small>(**`uid`**/**`gid`** < 1000 used to be used by system users/groups)</small>

```bash
# add
$ useradd --uid 1111 --home-dir /tmp --shell /bin/bash zoi-user
# delete
$ userdel zoi-user
```