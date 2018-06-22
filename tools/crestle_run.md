# Getting Crestle Working - for Newbies
fastai.ai Part 1 v2  
Updated:  05-Nov-2017  

### Why does my notebook have all these errors when I try running it in Crestle?
Answer:  the fastai repo in there has outdated materials

### What's the easiest way to fix it?

a)  log into [Crestle](https://www.crestle.com) and `Start Jupyter`    
b)  Hit `New Terminal`   
c)  `ls`  
d)  `cd courses`  
e)  `ls`  (you'll see the fastai course there)  
  
f)  `git pull` (update repo)
  
OR, if you run into errors because you have added files to the repository, etc., this is a quick fix:  
g)  `rm -rf fastai`  (delete this old version)  
h)  `git clone https://github.com/fastai/fastai.git`  (clone, get updated course files)  

>my example
```bash
nbuser@jupyter:~$ ls
README.txt  courses  examples
nbuser@jupyter:~$ cd courses
nbuser@jupyter:~/courses$ ls
fastai
nbuser@jupyter:~/courses$ rm -rf fastai
nbuser@jupyter:~/courses$ git clone https://github.com/fastai/fastai.git
Cloning into 'fastai'...
remote: Counting objects: 1055, done.
remote: Compressing objects: 100% (19/19), done.
remote: Total 1055 (delta 11), reused 17 (delta 9), pack-reused 1026
Receiving objects: 100% (1055/1055), 64.37 MiB | 40.84 MiB/s, done.
Resolving deltas: 100% (598/598), done.
Checking connectivity... done.
Checking out files: 100% (110/110), done.
nbuser@jupyter:~/courses$
```
And, now my [Lesson 1 notebook](https://s.users.crestle.com/u-fqnc8t2x12/notebooks/courses/fastai/courses/dl1/lesson1.ipynb) works!  :boom:




