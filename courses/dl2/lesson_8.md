# Lesson 8:  Part 2 Intro, Object Detection
(19-Mar-2018, live)  
 
- [Wiki: Part 2 / Lesson 8](http://forums.fast.ai/t/part-2-lesson-8-in-class/13556)
- [Lesson 8 video](https://youtu.be/Z0ssNAbe81M) 
  - video length:  2:01:14
- http://course.fast.ai/lessons/lesson8.html
- Notebook:  
   * [pascal.ipynb](https://github.com/fastai/fastai/blob/master/courses/dl2/pascal.ipynb)

---

## Staff
* Intro by [David Uminsky](https://www.usfca.edu/faculty/david-uminsky), Director of Data Institute of USF 
* [Jeremy Howard](https://www.usfca.edu/data-institute/about-us/researchers), Distinguished Scholar in Deep Learning

### Notes
* 600 international fellows around the world
* Rachel & Jeremy will be in room 153, 10am to 6pm each day (not for mentoring, possible projects)

---
## Object Detection
* creating much richer convolutional structures
* what is a picture of and where it is in the picture


## Learning
* Jeremy trying to pick topics that will help us learn foundational topics (richer CNN)
* can't possibly cover hundreds of interesting things done with deep learning

## Park 1 Takeaways
* we don't call this deep learning, but differential programming
* Part 1 was setting up a differential function, a loss function and pressing Go
* If you can configure a loss function that configures score, how good a task is, you're kind of done
* [playground.tensorflow.org](http://playground.tensorflow.org/#activation=tanh&batchSize=10&dataset=circle&regDataset=reg-plane&learningRate=0.03&regularizationRate=0&noise=0&networkShape=4,2&seed=0.71280&showTestData=false&discretize=false&percTrainData=50&x=true&y=true&xTimesY=false&xSquared=false&ySquared=false&cosX=false&sinX=false&cosY=false&sinY=false&collectStats=false&problem=classification&initZero=false&hideText=false)
  * play interactively where you can create and play with your functions manually

## Transfer Learning - definition
Transfer learning or inductive transfer is a research problem in machine learning that focuses on storing knowledge gained while solving one problem and applying it to a different but related problem.[1] For example, knowledge gained while learning to recognize cars could apply when trying to recognize trucks. This area of research bears some relation to the long history of psychological literature on transfer of learning, although formal ties between the two fields are limited.
 


### Transfer Learning
* the most important thing to learn to do to use deep learning effectively
* it makes nearly everything easier, faster and more accurate
* fastai library is all focused on transfer learning
* network that does thing A, remove last layer or so, replace it with a few random layers at the end, fine tune those layers to do thing B, taking advantage of the features the original network learned
<img src="../../images/lesson8_transfer_learning.png" align="center"  height="300" width="500" >   

---

## Embeddings
embeddings allow us to use categorical data
<img src="../../images/lesson8_embeddings.png" align="center"  height="300" width="550" >   

## Part 1 to Part 2
* rather than fastai and PyTorch being obscure, will learn enough to understand the source code
* object oriented python important to study and understand
* will introduce Python debugger, using editor to jump to code
* details on coding technique
* detailed walk-throughs of papers
* if you come across something you don't know, it is not hard, it is something you need to learn
* be careful of taking code from online resources, it may just good enough to have run their experiments, but difficult to generalize, be ready to do some debugging

<img src="../../images/lesson8_part1_2.png" align="center"  height="300" width="550" >   

## Motivation
* idea is to start with an empty notebook
* don't copy and paste code from notebook; TYPE IT OUT
* make sure you can repeat the process
* practice, practice
* if you don't understand a step, can ask on the forums, propose a hypothesis for why you think it doesn't work

<img src="../../images/lesson8_motivation.png" align="center"  height="300" width="550" >   


## Deep Learning Box
* if you wish, and have financial resources, can build your own deep learning toolbox
* if it is a good time, in your study cycle for it
* budget:  $1000 - $1500 for your own box
* RAM:  try to get 32GB
* PCI Lanes:  don't need to have 16 lanes to feed your GPU, you need 8 lanes
* Build:  you can buy the parts and put it together, or get someplace to do it for you

<img src="../../images/lesson8_dl_box.png" align="center"  height="300" width="550" >   

## Reading Papers
* each week we will be reading papers
* in academic papers, people love using Greek letters
* Adam is momentum and momentum on the square of the gradient
* papers include theoretical reasoning for why things work, lot of conferences and journals don't like to accept papers without theoretical justification
* Jeffrey Hinton: a decade or 2 ago, no conferences would accept neural network papers, then 1 abstract theoretical result came out, and journals started accepting neural network research
* we need to learn to read papers
* take a paper, put in effort to understand it, and then write a blog to explain it in code and normal English
* lots of people who do that get a following and great job offers
* understanding papers --->  useful skill
* it's hard to read or understand something that you cannot vocalize, which means if you don't know the names of the Greek letters, it's hard to follow
* spend some time to understand Greek letters

<img src="../../images/lesson8_paper.png" align="center"  height="300" width="550" >   

## Opportunities in this Class
* cutting edge research, almost no one else knows about 
* write blogs, incorporate research into a library
* communicating what you are doing is very helpful
* can get feedback on draft blogs on the forums

<img src="../../images/lesson8_opps.png" align="center"  height="300" width="550" >   


## Part 2:  What We Will Study 
* Generative Models
  * CNNs beyond classification
  * NLP beyond classification
* Large datasets

### Part 1 output
* number
* category

### Part 2 output
* top left, bottom right of image
* what object is
* complete picture
* enhanced version of input image
* entire original input paragraph, translated into French

<img src="../../images/lesson8_part2.png" align="center"  height="300" width="550" >   

### Notes
* requires different way of thinking about things
* almost all data will be text or image  (no audio yet, no more time series (most in ML course))
* we will be looking at some larger datasets
* don't be put off if you have limited computing resources
  - can use smaller datasets
  - can cut down on batch size

---
# Object Detection
* multiple items in an image we are classifying
* saying what we see, we also have bounding boxes around what we see
* bounding box:  box, rectangle, rectangle has the object entirely in it, but is no bigger than it has to be
* bounding box around horse, slightly imperfect, to be expected
* take data that is labeled this way and on labeled data, generate classes of object and bounding box
* labeling this kind of data is generally more expensive
* **ImageNet:**  here are the 1000 classes, tell me which it is
* **Object Detection:**  here is a list of classes, tell me everything that is in the image and where it is

<img src="../../images/lesson8_obj_det.png" align="center"  height="300" width="550" >   

## Stage 1
* classify and localize the largest object in each image
1.  What it is
2.  Where it is

<img src="../../images/lesson8_stage1.png" align="center"  height="300" width="550" >   

## Notebook:  Pascal
* [pascal.ipynb](https://github.com/fastai/fastai/blob/master/courses/dl2/pascal.ipynb)
* all notebooks are in [dl2 folder](https://github.com/fastai/fastai/tree/master/courses/dl2)
* `torch.cuda.set_device(3)` pick number of GPUs to use (of course, it depends on how many you have to use)

## Dataset:  Pascal
### The PASCAL VOC project:
* Provides standardised image data sets for object class recognition
* Provides a common set of tools for accessing the data sets and annotations
* Enables evaluation and comparison of different methods 
* Ran challenges evaluating performance on object class recognition (from 2005-2012, now finished)

### Notes
* Pascal VOC (Visual Object Classes):  http://host.robots.ox.ac.uk/pascal/VOC/
* we're using 2007 version of data
* you can use the 2012 version; it's bigger, will get better results
* some people combine the two, need to be careful, there can be leakage between the validation datasets

<img src="../../images/lesson8_nb_pascal.png" align="center"  height="300" width="550" >   

---
### PATH
* this gives you object oriented access to the files
* pathlib object has an `open` method
* load the .json files which don't contain the images, but the bounding boxes and the classes of the object
* json - the most standard way to pass around hierarchical structured data
```python
PATH = Path('data/pascal')
list(PATH.iterdir())
```

## Coding
* requires tenacity

## Editor
* [Visual Studio Code](https://code.visualstudio.com) is a great editor out there, it is FREE
  - best editor out there (unless you are willing to put time in to learn Vim or Emacs)
  - if you download a recent version of Anaconda, it will offer to download Visual Studio for you
  - good choice of editor if you are not sure

### Steps
- do `git clone` of fastai library
- File / Open Folder / open fastai github library
- For interpreter: can select fastai environment
  
You can use Visual Studio Code (vscode - open source editor that comes with recent versions of Anaconda, or can be installed separately), or most editors and IDEs, to find out all about the open_image function. vscode things to know:  
* Command palette (Ctrl-shift-p)
* Select interpreter (for fastai env)
* Select terminal shell
* Go to symbol (Ctrl-t)
* Find references (Shift-F12)
* Go to definition (F12)
* Go back (alt-left)
* View documentation
* Hide sidebar (Ctrl-b)
* Zen mode (Ctrl-k,z)

### [OpenCV](https://opencv.org) open image
`open_image` 
- cv2 is the open cv library
- torch vision library uses PyTorch tensors for all of its data augmentation
- a lot of people use [PIL](http://python-pillow.org) (pillow - Python Imaging Library) that adds support for opening, manipulating, and saving many different image file formats.
- Jeremy did a lot of testing; found open cv is 5-10x faster than Torch Vision
- Jeremy did satellite competition with another student, Torch Vision was very slow
- PIL is faster than Torch Vision, but not as fast as open cv; PIL is not as thread-safe
- Python has GIL (global interpreter lock) which means that two threads cannot do pythonic things at the same time, which makes Python, not a great language, for modern programming
- open cv releases the GIL
- one of the reasons the fastai library is so amazingly fast is that we don't use multiple processsors for data augmentation, we use multiple threads, reason we can do multiple threads is that is we use open cv
- unfortunately, open cv is a crappy API, poorly documented
- for these reasons, don't use PyTorch or Pillow for your data augmentation


## Matplotlib
- matplotlib so named because it was originally a clone of matlab's plotting library
- unfortunately matlab's plotting library is awful, but what was used at the time
- so, matplotlib added a second API, an object oriented library, but there's no tutorials on that
- Jeremy will show us how to use this API and some simple tricks
- `plt.subplots` is a handy wrapper, it returns 2 things, one is an axis object
- instead of saying `plt.<>`, now say `ax.<>`  where `<>` is 'something'

<img src="../../images/lesson8_matplotlib.png" align="center"  height="300" width="550" >   

## Step 1:  Largest Item Classifier
- Jeremy didn't have much experience in object detection before preparing for this course
- find the biggest object in each image and classify it
- younger students figure out the whole big solution they want, speculative ideas, spend 6 months on it, and day before presentation doesn't work
- Kaggle approach:  half an hour each day, make it better than the day before
- go through each of the bounding boxes in image and get the biggest one
- lambda functions used everywhere, a one-off function
- `sorted` python function
```python

def get_lrg(b):
    if not b: raise Exception()
    b = sorted(b, key=lambda x: np.product(x[0][-2:]-x[0][:2]), reverse=True)
    return b[0]
```
- dictionary comprehension is like list comprehension but it goes inside curly brackets
```python
trn_lrg_anno = {a: get_lrg(b) for a,b in trn_anno.items()}
```

<img src="../../images/lesson8_step1.png" align="center"  height="300" width="550" >   


## Coding
- lots of people write lines and lines of code, without checking what it is doing, and at the very end, they have an error and do not know where it is
- handy method for creating a directory
```python
(PATH/'tmp').mkdir(exist_ok=True)
CSV = PATH/'tmp/lrg.csv'
```
- why create a csv file?  makes it easy, create a csv, put in a temp folder and use what we already have
- easiest way to create a csv file is to create a pandas dataframe
- code below:  dictionary does not have order, so order of columns matters here
```python
df = pd.DataFrame({'fn': [trn_fns[o] for o in trn_ids],
    'cat': [cats[trn_lrg_anno[o][1]] for o in trn_ids]}, columns=['fn','cat'])
df.to_csv(CSV, index=False)
```
- 

## Back to "Dogs and Cats"!
```python
f_model = resnet34
sz=224
bs=64
```
```python
tfms = tfms_from_model(f_model, sz, aug_tfms=transforms_side_on, crop_type=CropType.NO)
md = ImageClassifierData.from_csv(PATH, JPEGS, CSV, tfms=tfms, bs=bs)
```
- `crop_type=CropType.NO` this is different from before:  may remember the default strategy for `224 x 224` image, is to first resize it so the smallest side is 224, and then take a **random square crop** during training, and then during validation, we take a **center crop**, unless we do data augmentation, in which case we take a few random/center crops.
- for **bounding boxes** we don't want to do that, unlike in Image Net where the thing we care about is pretty much in the middle and pretty big, a lot of the stuff in object detection is quite small and close to the edge, so we could crop it out, and that would be bad.
- `crop_type = CropType.NO` this means don't crop; to make it square instead, it squishes it (picture can look strangely...)
- generally speaking, a lot of computer vision models work better if you crop rather than squish, but they still work if you squish
- in this case, we definitely don't want to crop, so this perfect
- if you had very long or very tall images, that might be more difficult to model

### Model Loader
- main thing to know about a data loader is it is an iterator
- each time you get the next iterator, you get a mini batch
- the mini batch you get is whatever size you asked for
- by default, the batch size is 64; `bs = 64`
- in python, the way to get the next item in iterator is with `next(iter`
- for any python iterator, we have to say: *start at the beginning of the sequence, please*
- if you want to grab just a single batch, here is the syntax:
```python
x,y=next(iter(md.val_dl))
```
<img src="../../images/lesson8_md.png" align="center"  height="300" width="550" >   

### Show Image 
- we can't send it straight to `shw_img`
```python
shw_img(md.val_ds.denorm(to_np(x))[0]);
```

### `x`
- is not a numpy array
- it is not on the CPU
- its shape is all wrong, it's not `224x224x3` , it should be `3 x 224 x 224`
- size is:  `torch.cuda.FloatTensor of size 64x3x224x224  (GPU 1)]`
- these are not numbers between 0 and 1, because all the standard image nets expect our data to be standard normalized, with mean 0 and standard deviation of 1
- all of our 

<img src="../../images/lesson8_x.png" align="center"  height="300" width="550" >   

### Function:  denormalize
- `shw_img(md.val_ds.denorm(to_np(x))[0]);`
- `.denorm` it doesn't just denormalize, also fixes up the dimension order
- denormalization depends on the transform, the dataset knows what transform what was used to create it
- `md.val_ds.denorm(to_np(x)` :  `md` Model dataset --> takes some dataset, say `val_ds` --> pass it a mini-batch after turning it into a numpy array first

### Learner
```python
learn = ConvLearner.pretrained(f_model, md, metrics=[accuracy])
lean.opt_fn = optim.Adam

lrf = learn.lr_find(1e-5, 100)
```
- the first plot below looks a little weird, not particularly helpfuly
- normally, we would see an uptick on the right side of plot
- the reason we don't see it is because we intentionally removed the first two points and last two points
- last few points shoot plot up to infinity, it's not very useful
- sometimes when you have very few mini-batches, that is not a good idea
- a lot of people ask on forums how to fix it: `learn_sched.plot(n_skip=5, n_skip_end=1)`
- second plot shows it 
- if your dataset is really tiny, you can use a smaller batch size, if you only have 3 or 4 batches worth, there is nothing to see

```python
learn.sched.plot()
```
<img src="../../images/lesson_08/lesson08_lr_find.png" align="center"  height="300" width="550" > 

```python
learn_sched.plot(n_skip=5, n_skip_end=1)
```

<img src="../../images/lesson_08/lesson8_lr_find2.png" align="center"  height="300" width="550" > 
 
### Learning
#### Pick a learning rate
```python
lr = 2e-2
```
#### Fit, after one epoch, accuracy is 0.8048
```python
learn.fit(lr, 1, cycle_len=1)
```

#### Unfreeze a couple of layers
```python
lrs = np.array([lr/1000, lr/100, lr])
learn.freeze_to(-2)
```
```python
lrf = learn.lr_find(lrs/1000)
learn.sched.plot()
```
#### Fit, after another epoch, accuracy is 0.8210
```python
learn.fit(lrs/5, 1, cycle_len=1)
```
<img src="../../images/lesson_08/lesson8_learning.png" align="center"  height="300" width="550" > 


#### Unfreeze the whole thing, accuracy is 0.8128 (not really improved
```python
learn.unfreeze()
```
```python
learn.fit(lrs/5, 1, cycle_len=2)
```
<img src="../../images/lesson_08/lesson8_learning2.png" align="center"  height="300" width="550" > 

- Why are we stuck at 81% ?
- It makes sense, unlike ImageNet or dogs vs cats, where each image has one major theme, a lot of the PASCAL datasets have lots of little things (items to classify), and so a largest classifier is not going to do great. 
- We need to be able to see the results
- After working with this data for a while, Jeremy knows what the 20 classes are (person riding bike, dog on sofa, etc)

### Save model
```python
learn.save('clas_one')
```
```python
learn.load('clas_one')
```

### Visualize the data
- if you don't understand the code, split it into separate lines, and run each line at a time
- this is an OBVIOUS method, but many students don't do that when they don't follow the code; because if they had done that, they wouldn't be asking for help
- another method is to use the Python debugger
- for those of you who don't know about the Python debugger, it is life-changing

<img src="../../images/lesson_08/lesson8_visualize.png" align="center"  height="300" width="550" > 

## Python Debugger
- unfortunately, no one teaches basic software development skills in an academic program
- "wow, there's something that shows what your code does one step at a time!"
- note:  all programming languages have a debugger
- In Python, the standard debugger is called `pdb`

### 2 Ways to Use Python Debugger
1.  `pdb.set_trace()` to set a breakpoint  
2.  `%debug` magic to trace an error

### Using the debugger
- go inside your Python module, and add these lines: `pdb.set_trace()`
- can set a conditional breakpoint, where error is occurring
- fastai imports `pdb` for you
- to import:  `import pdb`
- it's not the most user-friendly experience
- "holy shit, the debugger even works in a Jupyter notebook!"
- it will also work in the terminal
- when running in Jupyter notebook, and box pops up, type `h` for **help**
- there are lots of tutorials there
- 

### Commands you need to know
- s / n / c
- u / d
- p
- l

###






