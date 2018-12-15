# Documenting Barrier

Our primary source of documentation is our barrier/wiki hosted on GitHub. We
encourage people to collaborate on the documentation via pull requests to our
wiki through the
[debauchee/barrier-wiki](https://github.com/debauchee/barrier-wiki) repository.


## local testing before a PR with docker

If you are interested in rendering your documentation changes before doing a
Pull Request we've set it up so you do that.  

1) fork repo on github
2) clone your fork locally 
3) launch gollum in docker passing the branch name
```
docker run -d -P -v `pwd`:/wiki --entrypoint "gollum" adtac/gollum-alpine --allow-uploads --live-preview 
```
4) see your local branch rendered at http://localhost:4567

If you are hacking on a branch you'll need to let gollum know using the `--ref`
parameter with the branch name as an option.  Use our `docker-compose.yml` like so to launch gollum with the current
branch as what it will render:
```
$ WIKI_BRANCH=`basename $(git symbolic-ref -q HEAD)` docker-compose up
```
