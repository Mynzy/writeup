## 1. Super ssh

enter this command and enter the password when prompted

<code>ssh <username>@titan.ctf.net -p 54184 </code>


## 2. Bookmarklet

bookmarklet are javascript bookmark. bookmarklet are available in all major browser.

to add bookrmarklet write javascript in the url field of the bookmark modal

after adding the bookmark click the bookmark. [read more](https://www.freecodecamp.org/news/what-are-bookmarklets/)

<img src="./pic/bookmkarlet.png" alt="FEIN FEIN FEIN FEINFEINFEI IFNE">


## 3. Commitment Issues

after unzip the file , try list hidden files <code>.git</code>. you'll notice there is message.txt that might look important.

to solve this , learn few things about [git](https://primer.picoctf.org/#_git_version_control).

first we need to loo into check out the commit, somehow the previos commit contain the flag and got removed.
<img src="./pic/git_log.png" alt="FEIN FEIN FEIN FEIN">

we need to checkout the previous commit
<img src="./pic/git_checkout.png" alt="FEIN FEIN FEIN FEIN">

and cat the message
<img src="./pic/cat.png" alt="ngantuk">

## 4. interencdec

just decode cipher in base64 two times and rot13 with 19 rotation <code>YidkM0JxZGtwQlRYdHFhR3g2YUhsZmF6TnFlVGwzWVROclgyZzBOMm8yYXpZNWZRPT0nCg==</code>

## 5. Time Machine
download the challenge.zip, navigate to drop-in , cat the message and read the clue , enter <code>git log</code> to look into commit history

## 6. Blame Game
its similar to Time Machine nad Commitment Issues , but insteead we want to look into commit history of specific files. You just need to <code>git log message.py</code>, and you will get the flag.
![alt text](./pic/image.png)

## 7. Collaborative Developmentn
As you can see when we change to other branch , the flag.py contains the some part of the flag.
<code>git checkout feature/part-1 && cat flag.py</code>
<img src="./pic/collab.png" alt="ngantuk">

With <code> git branch -a </code> you can see all branch. There are three feature branches and each one has a part of the flag. You can merge them all withou conflicts using command below.

<img src="./pic/collab2.png" alt="ngantuk">

## 8. weirdSnake

this is a re challenge. 
![alt text](./pic/snake1.png)

```py
input_list = [4, 54, 41, 0, 112, 32, 25, 49, 33, 3, 0, 0, 57, 32, 108, 23, 48, 4, 9, 70, 7, 110, 36, 8, 108, 7, 49, 10, 4, 86, 43, 108, 112, 14, 2, 71, 62, 115, 88, 78]
```


![alt text](./pic/snake2.png)
```py
key_str = "J"
key_str = "_" + key_str
key_str = key_str + "o"
key_str = key_str + "3"
key_str = "t" + key_str

```

![alt text](./pic/snake3.png)
```py
key_list = [ord(char) for char in key_str]
while len(key_list) < len(input_list):
    key_list.extend(key_list)
    print(key_list)

```

![alt text](./pic/snake4.png)
```py
result = [a^b for a,b in zip(input_list, key_list)]
```

![alt text](./pic/snake5.png)


so the final code will be 

```py
input_list = [4, 54, 41, 0, 112, 32, 25, 49, 33, 3, 0, 0, 57, 32, 108, 23, 48, 4, 9, 70, 7, 110, 36, 8, 108, 7, 49, 10, 4, 86, 43, 108, 112, 14, 2, 71, 62, 115, 88, 78]
key_str = "J"
key_str = "_" + key_str
key_str = key_str + "o"
key_str = key_str + "3"
key_str = "t" + key_str
key_list = [ord(char) for char in key_str]
while len(key_list) < len(input_list):
    key_list.extend(key_list)
    print(key_list)
result = [a^b for a,b in zip(input_list, key_list)]
result_text = ''.join(map(chr,result))
print(result_text
```

can refer more [here](https://sudorem.dev/posts/pico24-weirdsnake/)