ergouudeMacBook:practice ergouu$ git init                                                                  -----初始化本地版本库

Initialized empty Git repository in /Users/ergouu/Documents/code/practice/.git/

ergouudeMacBook:practice ergouu$ git remote add origin https://github.com/ergouu/practise.git               ---联接到远程仓库

ergouudeMacBook:practice ergouu$ git push -u origin master                                                  -------push上去，干嘛用的不知道

Enumerating objects: 36, done.
Counting objects: 100% (36/36), done.
Delta compression using up to 4 threads
Compressing objects: 100% (28/28), done.
Writing objects: 100% (36/36), 21.55 KiB | 3.59 MiB/s, done.
Total 36 (delta 5), reused 0 (delta 0)
remote: Resolving deltas: 100% (5/5), done.
To https://github.com/ergouu/practise.git
 * [new branch]      master -> master
Branch 'master' set up to track remote branch 'master' from 'origin'.
ergouudeMacBook:practice ergouu$ ls
A1107	README	in.log	test
ergouudeMacBook:practice ergouu$ 
ergouudeMacBook:practice ergouu$ 
ergouudeMacBook:practice ergouu$ ls
A1107	README	in.log	test
ergouudeMacBook:practice ergouu$ vi README 
ergouudeMacBook:practice ergouu$ 
ergouudeMacBook:practice ergouu$ 
ergouudeMacBook:practice ergouu$ 

ergouudeMacBook:practice ergouu$ git diff      								----应该是compare一下

diff --git a/README b/README
index 66bfca1..79dcd00 100644
--- a/README
+++ b/README
@@ -1 +1,2 @@

 # Practise
+A1107 is the PAT problem

ergouudeMacBook:practice ergouu$ git add -A     							-----track文件

ergouudeMacBook:practice ergouu$ git commit -m "update README"     					-----提交到本地

[master 949d672] update README
 1 file changed, 1 insertion(+)
 
ergouudeMacBook:practice ergouu$ git push origin master       						-------然后Push到远程

Enumerating objects: 5, done.
Counting objects: 100% (5/5), done.
Delta compression using up to 4 threads
Compressing objects: 100% (2/2), done.
Writing objects: 100% (3/3), 368 bytes | 368.00 KiB/s, done.
Total 3 (delta 0), reused 0 (delta 0)
To https://github.com/ergouu/practise.git
   f140609..949d672  master -> master
ergouudeMacBook:practice ergouu$ ls -al
total 16
drwxr-xr-x   7 ergouu  staff  224  3 28 22:16 .
drwxr-xr-x   4 ergouu  staff  128  3 28 22:12 ..
drwxr-xr-x  13 ergouu  staff  416  3 28 22:16 .git
drwxr-xr-x   4 ergouu  staff  128  3 28 21:56 A1107
-rw-r--r--   1 ergouu  staff   36  3 28 22:16 README
-rw-r--r--@  1 ergouu  staff   54  3 27 23:52 in.log
drwxr-xr-x   4 ergouu  staff  128  3 27 23:22 test
ergouudeMacBook:practice ergouu$ ls
A1107	README	in.log	test
ergouudeMacBook:practice ergouu$ ll
-bash: ll: command not found

ergouudeMacBook:practice ergouu$ git checkout -b mess     						-----新建一个叫MESS的Branch

Switched to a new branch 'mess'
ergouudeMacBook:practice ergouu$ git branch
  master
* mess
ergouudeMacBook:practice ergouu$ git add -A
ergouudeMacBook:practice ergouu$ git commit -m "add a new branch nemed mess"
[mess 18836fa] add a new branch nemed mess
 1 file changed, 0 insertions(+), 0 deletions(-)
 create mode 100644 .DS_Store
ergouudeMacBook:practice ergouu$ git push origin mess
Enumerating objects: 4, done.
Counting objects: 100% (4/4), done.
Delta compression using up to 4 threads
Compressing objects: 100% (3/3), done.
Writing objects: 100% (3/3), 696 bytes | 696.00 KiB/s, done.
Total 3 (delta 1), reused 0 (delta 0)
remote: Resolving deltas: 100% (1/1), completed with 1 local object.
remote: 
remote: Create a pull request for 'mess' on GitHub by visiting:
remote:      https://github.com/ergouu/practise/pull/new/mess
remote: 
To https://github.com/ergouu/practise.git
 * [new branch]      mess -> mess
ergouudeMacBook:practice ergouu$ git branch
  master
* mess
ergouudeMacBook:practice ergouu$ git branch
  master
* mess

ergouudeMacBook:practice ergouu$ git reset --hard       						--------版本回退，其实也不知道是干嘛的

HEAD is now at 18836fa add a new branch nemed mess
ergouudeMacBook:practice ergouu$ git branch
  master
* mess
ergouudeMacBook:practice ergouu$ git status
On branch mess
nothing to commit, working tree clean
ergouudeMacBook:practice ergouu$ git checkout master
Switched to branch 'master'
Your branch is up to date with 'origin/master'.
ergouudeMacBook:practice ergouu$ git branch 
* master
  mess
ergouudeMacBook:practice ergouu$ git branch -a
* master
  mess
  remotes/origin/master
  remotes/origin/mess
ergouudeMacBook:practice ergouu$ git add -A
ergouudeMacBook:practice ergouu$ git commit 
On branch master
Your branch is up to date with 'origin/master'.

nothing to commit, working tree clean
ergouudeMacBook:practice ergouu$ git push origin master
To https://github.com/ergouu/practise.git
 ! [rejected]        master -> master (fetch first)
error: failed to push some refs to 'https://github.com/ergouu/practise.git'
hint: Updates were rejected because the remote contains work that you do
hint: not have locally. This is usually caused by another repository pushing
hint: to the same ref. You may want to first integrate the remote changes
hint: (e.g., 'git pull ...') before pushing again.
hint: See the 'Note about fast-forwards' in 'git push --help' for details.
ergouudeMacBook:practice ergouu$ git fetch origin master           					-------听说是从远程拿下来，但是不合并本地库
remote: Enumerating objects: 1, done.
remote: Counting objects: 100% (1/1), done.
remote: Total 1 (delta 0), reused 0 (delta 0), pack-reused 0
Unpacking objects: 100% (1/1), done.
From https://github.com/ergouu/practise
 * branch            master     -> FETCH_HEAD
   949d672..48c2bb8  master     -> origin/master
ergouudeMacBook:practice ergouu$ git status
On branch master
Your branch is behind 'origin/master' by 2 commits, and can be fast-forwarded.
  (use "git pull" to update your local branch)

nothing to commit, working tree clean
ergouudeMacBook:practice ergouu$ git branch
* master
  mess
  
ergouudeMacBook:practice ergouu$ git push origin master         					---------所以还是提交不上去

To https://github.com/ergouu/practise.git
 ! [rejected]        master -> master (non-fast-forward)
error: failed to push some refs to 'https://github.com/ergouu/practise.git'
hint: Updates were rejected because the tip of your current branch is behind
hint: its remote counterpart. Integrate the remote changes (e.g.
hint: 'git pull ...') before pushing again.
hint: See the 'Note about fast-forwards' in 'git push --help' for details.

ergouudeMacBook:practice ergouu$ git pull origin master          					----------从远程拿下来，合并

From https://github.com/ergouu/practise
 * branch            master     -> FETCH_HEAD
Updating 949d672..48c2bb8
Fast-forward
 .DS_Store | Bin 0 -> 6148 bytes
 1 file changed, 0 insertions(+), 0 deletions(-)
 create mode 100644 .DS_Store
ergouudeMacBook:practice ergouu$ 
ergouudeMacBook:practice ergouu$ 
ergouudeMacBook:practice ergouu$ git branch -a
* master
  mess
  remotes/origin/master
  remotes/origin/mess
ergouudeMacBook:practice ergouu$ git branch 
* master
  mess
  
ergouudeMacBook:practice ergouu$ git push origin master        						----------可以PUSH了

Everything up-to-date
ergouudeMacBook:practice ergouu$ git checkout -D mess
error: unknown switch `D'
usage: git checkout [<options>] <branch>
   or: git checkout [<options>] [<branch>] -- <file>...

    -q, --quiet           suppress progress reporting
    -b <branch>           create and checkout a new branch
    -B <branch>           create/reset and checkout a branch
    -l                    create reflog for new branch
    --detach              detach HEAD at named commit
    -t, --track           set upstream info for new branch
    --orphan <new-branch>
                          new unparented branch
    -2, --ours            checkout our version for unmerged files
    -3, --theirs          checkout their version for unmerged files
    -f, --force           force checkout (throw away local modifications)
    -m, --merge           perform a 3-way merge with the new branch
    --overwrite-ignore    update ignored files (default)
    --conflict <style>    conflict style (merge or diff3)
    -p, --patch           select hunks interactively
    --ignore-skip-worktree-bits
                          do not limit pathspecs to sparse entries only
    --ignore-other-worktrees
                          do not check if another worktree is holding the given ref
    --recurse-submodules[=<checkout>]
                          control recursive updating of submodules
    --progress            force progress reporting

ergouudeMacBook:practice ergouu$ git branch -D mess        						--------将本地的MESS库去掉

Deleted branch mess (was 18836fa).
ergouudeMacBook:practice ergouu$ ls
A1107	README	in.log	test
ergouudeMacBook:practice ergouu$ ls -al
total 32
drwxr-xr-x   8 ergouu  staff   256  3 28 22:28 .
drwxr-xr-x   5 ergouu  staff   160  3 28 22:19 ..
-rw-r--r--   1 ergouu  staff  6148  3 28 22:28 .DS_Store
drwxr-xr-x  15 ergouu  staff   480  3 28 22:29 .git
drwxr-xr-x   4 ergouu  staff   128  3 28 21:56 A1107
-rw-r--r--   1 ergouu  staff    36  3 28 22:16 README
-rw-r--r--@  1 ergouu  staff    54  3 27 23:52 in.log
drwxr-xr-x   4 ergouu  staff   128  3 27 23:22 test
ergouudeMacBook:practice ergouu$ git branch
* master
ergouudeMacBook:practice ergouu$ 
ergouudeMacBook:practice ergouu$ 
ergouudeMacBook:practice ergouu$ 
ergouudeMacBook:practice ergouu$ ls
A1107	README	in.log	test
ergouudeMacBook:practice ergouu$ 
ergouudeMacBook:practice ergouu$ 
ergouudeMacBook:practice ergouu$ mkdir PAT
ergouudeMacBook:practice ergouu$ cd PAT
ergouudeMacBook:PAT ergouu$ ls
ergouudeMacBook:PAT ergouu$ ll
-bash: ll: command not found
ergouudeMacBook:PAT ergouu$ ls -al
total 0
drwxr-xr-x  2 ergouu  staff   64  3 28 22:30 .
drwxr-xr-x  9 ergouu  staff  288  3 28 22:30 ..
ergouudeMacBook:PAT ergouu$ touch README
ergouudeMacBook:PAT ergouu$ echo "# TEST">README
ergouudeMacBook:PAT ergouu$ ls
README
ergouudeMacBook:PAT ergouu$ cat README 

# TEST

ergouudeMacBook:PAT ergouu$ git checkout -b PAT
Switched to a new branch 'PAT'
ergouudeMacBook:PAT ergouu$ git branch
* PAT
  master
ergouudeMacBook:PAT ergouu$ git add -A
ergouudeMacBook:PAT ergouu$ git commit -m "initial commit"
[PAT 70a7024] initial commit
 1 file changed, 1 insertion(+)
 create mode 100644 PAT/README
ergouudeMacBook:PAT ergouu$ git push origin PAT
Enumerating objects: 5, done.
Counting objects: 100% (5/5), done.
Delta compression using up to 4 threads
Compressing objects: 100% (2/2), done.
Writing objects: 100% (4/4), 311 bytes | 311.00 KiB/s, done.
Total 4 (delta 1), reused 0 (delta 0)
remote: Resolving deltas: 100% (1/1), completed with 1 local object.
remote: 
remote: Create a pull request for 'PAT' on GitHub by visiting:
remote:      https://github.com/ergouu/practise/pull/new/PAT
remote: 
To https://github.com/ergouu/practise.git
 * [new branch]      PAT -> PAT
ergouudeMacBook:PAT ergouu$ git log
commit 70a7024e3680b121f9307a8524e63ec9302ed887 (HEAD -> PAT, origin/PAT)
Author: xiexun <xunx@zju.edu.cn>
Date:   Thu Mar 28 22:32:15 2019 +0800

    initial commit

commit 48c2bb867fced0b18daffd95bf0e51de7839dfb2 (origin/master, master)
Merge: 949d672 18836fa
Author: ergouu <48860405+ergouu@users.noreply.github.com>
Date:   Thu Mar 28 22:22:41 2019 +0800

    Merge pull request #1 from ergouu/mess
    
    add a new branch nemed mess

commit 18836fa1c20233cd7aaa8b187a12b351da9b737d (origin/mess)
Author: xiexun <xunx@zju.edu.cn>
Date:   Thu Mar 28 22:21:10 2019 +0800

    add a new branch nemed mess

commit 949d6721c0087523f6f4972bee7bb3c64684802f
Author: xiexun <xunx@zju.edu.cn>
ergouudeMacBook:practice ergouu$ git merge
fatal: No remote for the current branch.
ergouudeMacBook:practice ergouu$ git merge master
Already up to date.
ergouudeMacBook:practice ergouu$ git merge master PAT
Already up to date.
ergouudeMacBook:practice ergouu$ git help merge
ergouudeMacBook:practice ergouu$ 
ergouudeMacBook:practice ergouu$ 
ergouudeMacBook:practice ergouu$ 
ergouudeMacBook:practice ergouu$ git branch 
* PAT
  master
ergouudeMacBook:practice ergouu$ git merge PAT
Already up to date.
ergouudeMacBook:practice ergouu$ git merge master
Already up to date.
ergouudeMacBook:practice ergouu$ git push origin master
Everything up-to-date
ergouudeMacBook:practice ergouu$ git checkout master
Switched to branch 'master'
Your branch is up to date with 'origin/master'.
ergouudeMacBook:practice ergouu$ git merge PAT     						-------将PATmerge到master里面去，要先切换到master的BRANCH，再去Merge才有用，但Merge后，在网页上还能再看到PAT的Branch

Updating 48c2bb8..70a7024
Fast-forward
 PAT/README | 1 +
 1 file changed, 1 insertion(+)
 create mode 100644 PAT/README
ergouudeMacBook:practice ergouu$ git push origin master
Total 0 (delta 0), reused 0 (delta 0)
To https://github.com/ergouu/practise.git
   48c2bb8..70a7024  master -> master
   
ergouudeMacBook:practice ergouu$ git branch -d PAT     					   	-------看下面一行命令

Deleted branch PAT (was 70a7024).
ergouudeMacBook:practice ergouu$ git push origin master
Everything up-to-date
ergouudeMacBook:practice ergouu$ 
ergouudeMacBook:practice ergouu$ 
ergouudeMacBook:practice ergouu$ 
ergouudeMacBook:practice ergouu$ git branch -a     						--------本地删除了PAT，远程仓库并没有删掉
* master
  remotes/origin/PAT
  remotes/origin/master
  remotes/origin/mess
  
ergouudeMacBook:practice ergouu$ git remote prune origin      		----------删除远程网页已经删除的Branch，也就是说，MESS在网页上删除了，但在本地用git branch -a还是能看到，用这个命令就可以删除掉

Pruning origin
URL: https://github.com/ergouu/practise.git
 * [pruned] origin/mess
ergouudeMacBook:practice ergouu$ git branch -a
* master
  remotes/origin/PAT
  remotes/origin/master
ergouudeMacBook:practice ergouu$ git remote rm PAT
fatal: No such remote: 'PAT'
ergouudeMacBook:practice ergouu$ git status
On branch master
Your branch is up to date with 'origin/master'.

nothing to commit, working tree clean
ergouudeMacBook:practice ergouu$ git branch -a
* master
  remotes/origin/PAT
  remotes/origin/master
ergouudeMacBook:practice ergouu$ git branch -r
  origin/PAT
  origin/master
ergouudeMacBook:practice ergouu$ git status
On branch master
Your branch is up to date with 'origin/master'.

nothing to commit, working tree clean

ergouudeMacBook:practice ergouu$ git push origin --delete PAT        ---------从客户端直接将远程的PAT分支删除，并且在网页上也看不到想关的分支了

To https://github.com/ergouu/practise.git
 - [deleted]         PAT
ergouudeMacBook:practice ergouu$ 
ergouudeMacBook:practice ergouu$ 
ergouudeMacBook:practice ergouu$ git branch -a
* master
  remotes/origin/master
ergouudeMacBook:practice ergouu$ 
