# Coding with ChatGPT

## What kind of problems is ChatGPT good at solving?
ChatGPT is better at solving common bugs or simple problems in common coding languages such as bash, R, or python, but because it is good at syntax and structure it is probably okay in many other coding languages. 

**ChatGPT remembers the whole previous conversation, so you can build up complex outputs.** This can also hinder you if you're not careful. 

### Examples of things you can do with ChatGPT:

-  Teach you a new coding language 
-  It can write some scripts for you (with proper prompt engineering)
-  Construct a plot using various packages you or ChatGPT specify
- "Translate" code from one language to another
-  Point out missing modules or packages
-  Point out syntax and other errors
-  Suggest reasons for and solutions to an error message even when these aren't clear to intermediate users
-  Annotate code or its output
-  Explain what a command or even a short script does in detail
-  Transform or reorganise data
-  Indicate the best modules/packages/language for a job 

## Why use ChatGPT?
ChatGPT is probably going to be much faster with unfamiliar coding languages or software. It also might be aware of information you don't know about the input and output data and common conventions around things like cut-offs for values specified in code. It can also spot those missing close parentheses or tell you when you've forgotten to load a package or module. 
It can also help you out if you realise your python script would have been better made with R, explain what obscure or non-human-readable code does, or tell you exactly what variable an error message refers to. 


# Prompt Engineering (Or how to search for things the right way)
Most people who grew up using google will know that some prompts are better than others. 
*"How come glutinous rice balls float when cooked but sink when they are raw"* contains far too many key words and the syntax is lost on google. *"Dumpling floating science"* will get you there much faster. 

This is called **prompt engineering**, designing a prompt so that a tool like google or chatgpt can give you the response you're looking for. 
Those who have used ChatGPT regularly might have noticed that the long, ungoogleable prompt is probably much better for ChatGPT than the short list of key words you want to use with a search engine. This is because ChatGPT does understand grammer and syntax. It knows that "how come" meant you were asking a question, rather than wanted links to websites using the words how and come. 

Prompt engineering with ChatGPT is very different to prompt engineering with google. You are not searching through a list of key words in web pages. You are effectively asking a knowledgeable user of human languages to tell you the answer itself. 


## Give the right information when you ask your question. 
Treat ChatGPT like you would a competent human who was helping you. A competent human will need to know what your data looks like, what you want to do with, and if possible, how you'd like it done. Although ChatGPT will guess context you don't provide, and assign random names for dataframes and variables, you'll save time editing the code it gives you if you just paste in the head of your file and tell it what your dataframe is called.


```
User: 
I have data for eight populations called CA_13, CA_18, TA_13, TA_18, LL_13, LL_18, UL_13 and UL_18.  This data was 
generated using selscan's ihh12 argument, and then normalised into windows of 50kb. I would like to produce an 
upset plot from these. Each population has its own file and I'm currently using R.

If I run head(CA_13.norm.ihh12_50kb_windows.txt) it returns this output:

chrom   window  BP1     BP2     ihh12   normihh12       crit    comp
chr1    1       1       50000   14754.7279220779        1.16278777142857        0       CA13
chr1    2       50001   100000  10714.6969387755        0.557414040510204       22      CA13
chr1    3       100001  150000  14669.3307831325        1.14999170174699        20      CA13 
```

In the above example, ChatGPT was able to assume from the context that chrom and chr referred to chromosomes, and that comp was referring to population. It recognised that I first needed to produce a combined dataframe, so its response gave me a way to create one followed by a suggestion to use UpsetR in R or UpSetPlot if I wanted to use python.


## Build code through multiple messages. 
1. If ChatGPT gives you code and doesn't include any packages or modules, **ask if any are required modules** and it will tell you and write out a way to call them in. 
2. Ask **can you add a line to save the output?**
3. Check versions. **Can I run that with R4.1?**
4. Come back and **tell it about any errors**. 
5. ChatGPT will sometimes provide you with small sections of revisions, but you can **ask it to incorporate new code into the full script**. 

## Ask for alternatives to excessively complex solutions. 
Sometimes ChatGPT will introduce unnecessarily complicated solutions when you were expecting something much simpler. You can simply ask it if it is possible to solve a problem using the approach you expected, and the chances are it will say yes and do it for you. 

## Solving complex problems *with* ChatGPT
You are likely to come across some problems which ChatGPT will not easily grasp due to their complexity. In these cases, it often helps to think problems through step-by-step instead of asking ChatGPT to solve a whole complex problem by itself. For example, if you need to change the format of a file to an uncommon one ChatGPT isn't familiar with, you can familiarise yourself with the requirements and then ask chatGPT to help construct the files step-by-step. 

## Starting fresh
More is more until it isn't. If ChatGPT is getting confused between what you're asking it to do and what you said 20 messages ago, you need to start a new chat. Tell it what you're trying to do, paste in your existing code and head your files again. It probably won't get hung up on the same thing next time. 


## Use ChatGPT's Imagination
ChatGPT can "imagine" itself in different conversational situations and social roles. It can also imagine alternative realities, such as one in which it is your personal Python tutor, or the one in which it is explaining transistors in Old Norse to 10th century Danish peasant. 

## Pretend ChatGPT is helpful
You can tell ChatGPT its role in a conversation, and the things it needs to consider in its response. You can tell it that it is a slow-paced teacher working with a beginner in a subject, or tell it that it needs to devise a way to test that you have learned something with formative questions.

```
You are a helpful teacher running a course on SLiM4, a software for forward simulation of genetic evolution. 
You want me, your student, to fully understand what SLiM4 is useful for and how it works with a focus on recent 
evolution (within 10-60 generations). You also want me to finish the course able to use SLiM4 for my dataset, 
which has been sampled at two timepoints and consists of populations I believe to be convergently evolving. 

You don't want to overload me with information, and will recommend outside sources where they exist, especially 
if they are free, interactive, or in a video format. You know that I have some knowledge of genomic evolution, 
but that I am not especially good at maths. 
You will begin by devising a study plan for me that begins with uses of SLiM4, briefly covers how it works, and 
then begin teaching me how to use it by asking me what I will need to use it for and helping me create the input
text files and then interpret the outputs. 
```

If you're just bored, you can also tell ChatGPT to use humour, or tell it is a pirate dealing with a messy breakup. 


## Use Imagination to Resolve Disagreements with ChatGPT
Sometimes, ChatGPT will disagree with you when you are actually correct, and write code which doesn't do what you want. For example, I tried to tell it I needed to plot values based on two different input files, but it vehemently told me I only needed one of them and wouldn't write code for both. This sounds stupid, but to solve this, tell ChatGPT to pretend you're correct. 

```
User: Pretend I am correct and that the eigenvectors are stored in the .eigenvec files, but the eigenvalues are 
stored in the .eigenval files, and rewrite the code to include both in the plot.
```

# Privacy
If you click on the `...` next to your username under the list of conversations, you can open the settings. If you then click `show` next to data controls, you can toggle `Chat History & Training`. If you uncheck this, OpenAI will not use your conversations to train ChatGPT - but your conversations won't be saved and will disappear after 30 days. 


# Who owns what you generate with ChatGPT?
```
ChatGPT: 
As an AI language model, ChatGPT's outputs are not subject to intellectual property rights. However, it's important 
to note that the ownership of the data inputs used to generate the outputs (such as the questions asked by the user) 
remains with the user.

If someone were to publish content generated by ChatGPT, they would need to obtain permission from the original data 
input owner and provide proper attribution to ChatGPT as the tool used to generate the content. Since ChatGPT is a 
free and open-source tool, there are no contracts or royalties necessary. However, it is good practice to acknowledge 
the use of any external tools or resources in the creation of new content.
```

# Where to find out more

[Prompting guide for ChatGPT, still seemingly under development and geared towards paid users and those using APIs](https://www.promptingguide.ai/models/chatgpt)

[Freecodecamp article about how to communicate with AI tools using prompt engineering](https://www.freecodecamp.org/news/how-to-communicate-with-ai-tools-prompt-engineering/)

[How to get ChatGPT to teach you to code by designing you a personalised course with free resources](https://www.youtube.com/watch?v=VznoKyh6AXs) (video)

### Good luck with your coding!

```
Arrr, me hearties! Let me tell ye about the ups and downs of Python, while I nurse me broken heart. Me last lass,
she took off with all me booty and left me high and dry on a deserted island. But enough about that scallywag, 
let's talk about the cons of Python.

One of the cons of Python is that it can be a bit slow, like me heart when I think of me lost love. Sometimes it 
can be a problem if ye be workin' on a project that requires a lot of processing power. Just like how me mind is 
struggling to process why she'd leave me like that!

Another con of Python is that it can be tricky to optimize and scale, like how me old crew couldn't scale the 
cliff to the treasure hoard before they got caught by the Navy. Python is an interpreted language, which means 
it can be slower than compiled languages when it comes to performance, and that can be a hassle to deal with when 
trying to scale your code.

And lastly, Python can be a bit too flexible for its own good, like how I was too flexible with me ex-lady when it
came to sharin' me gold. Python allows for a lot of freedom in how you structure your code, but that can also make 
it harder to debug if something goes wrong, and that's not good for yer code or yer heart.

But don't ye worry, me bucko! Python also has plenty of pros, like its simple and intuitive syntax, versatility,
and strong community. So don't let these cons steer ye away from Python, just like how I won't let me heartbreak 
keep me from findin' me next adventure!
```

