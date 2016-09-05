# 如何pull request到kubernetes

1. Fork

1.1 Go to https://github.com/kubernetes/kubernetes
1.2 Click the "Fork" button (at the top right)

2. Clone your fork

The commands below require that you have $GOPATH set ($GOPATH docs). We highly recommend you put Kubernetes' code into your GOPATH. Note: the commands below will not work if there is more than one directory in your $GOPATH.  

```
mkdir -p $GOPATH/src/k8s.io
cd $GOPATH/src/k8s.io
# Replace "$YOUR_GITHUB_USERNAME" below with your github username
git clone https://github.com/$YOUR_GITHUB_USERNAME/kubernetes.git
cd kubernetes
git remote add upstream 'https://github.com/kubernetes/kubernetes.git'
```

3. Create a branch and make changes

```
git checkout -b my-feature
# Make your code changes
```

4. Keeping your development fork in sync

```
git fetch upstream
git rebase upstream/master
```

Note: If you have write access to the main repository at github.com/kubernetes/kubernetes, you should modify your git configuration so that you can't accidentally push to upstream:

```
git remote set-url --push upstream no_push
```

5. Committing changes to your fork

Before committing any changes, please link/copy the pre-commit hook into your .git directory. This will keep you from accidentally committing non-gofmt'd Go code. This hook will also do a build and test whether documentation generation scripts need to be executed.  
The hook requires both Godep and etcd on your PATH.

```
cd kubernetes/.git/hooks/
ln -s ../../hooks/pre-commit .
```

Then you can commit your changes and push them to your fork:

```
git commit
git push -f origin my-feature
```

6. Creating a pull request

6.1 Visit https://github.com/$YOUR_GITHUB_USERNAME/kubernetes  
6.2 Click the "Compare & pull request" button next to your "my-feature" branch.  
6.3 Check out the pull request process for more details  

