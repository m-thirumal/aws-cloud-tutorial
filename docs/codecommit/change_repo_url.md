## Change codecommit Repository URL

1. Copy url from the codecommit
2. Delete remote url
```
git remote set-url --delete codecommit {old_URL}
```
you may get the following error but ignore it.
```
fatal: Will not delete all non-push URLs
```
3. Add new remote url
```
git remote set-url --add codecommit {new_URL}
```
4. Check the URL
```
git remote -v
```
5. Repeat the setp 2
```
git remote set-url --delete codecommit {old_URL}
```
