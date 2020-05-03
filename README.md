# review notes for react

- goals
- topics
- coding
- more learning

## goals

to get a react dev environment running on your machine, and write a few lines of code

we're building a login page - pretty simple, but room to do features if you want


## topics

- using the command line
- using create-react-app
- coding our app
- using git from the command line

coding lesson will follow the topics review


### using the command line

to open a command line prompt

linux: Ctrl + Alt + t

mac: Cmd + space ... terminal

windows: start menu -> git bash

on windows you'll have needed to install "git for windows" which comes with "git bash"

if you don't have it, just google "git for windows" (the download is from git-scm.com)

---

using the command line is a deep and interesting topic, for now we'll learn what we'll need:

`~` is your home directory. I pronounce this "squiggle".

`~/code` is a directory called `code` inside your home directory. this is where code goes

<img src='https://i.imgur.com/WWIvV7S.png' height=226 width=464 />

before your command, the prompt will tell you who you are (nik) what computer you're on (rico is the name of my computer) then the present working directory (~)


`cd` - this is the program that changes which directory you're in. you'll need to tell it which directory you want to go to

eg: `cd ~/code` will move your present working directory to `~/code`

eg: `cd code` will move you into the code directory, as long as you were in ~ before


now if you try `cd code`, it might not work

<img src='https://i.imgur.com/48GPTAY.png' height=135 width=732 />

so we'll have to make the directory



`ls` - this is the program that lists files and directories in your pwd

`mkdir` - this is the program which makes directories

eg: `mkdir code`


if `cd code` didn't work, let's figure out why

do `ls`

you'll see a list of files and directories... if none of them is called `code`, then that's why the command failed! we can't `cd` into a directory which doesn't exist

to fix this we can run

`mkdir code` which will make a directory called `code` in our present working directory.

now we can `cd code` and we should see that our pwd is ~/code



### using create-react-app

now that we're inside our code directory (where code goes), we can start a project

we're going to use a program called `create-react-app` which, you guessed it, will create a project that "has react"

what does it mean to "have react"?

it means the project (directory) has the programs installed which will turn your code (react code) into code the browser can run (vanilla javascript)

chief among those programs are `webpack` and `babel` - but there's a few others - none of which we'll really have to learn much about now, we'll just be happy that they do their job correctly :D

---

to use create-react-app, we need node installed, so we'll check that we have `node` installed correctly

in a command prompt, do `which npx`

`which` is a program which tells us the file a program actually runs. Here we're asking which file the program named `npx` will run.

if we have such a program, `which` will tell us a filename. If we don't have `npx`, which will return nothing (and go directly to the next line)

usually, the `which` program is used to determine IF we have a program installed

<img src='https://i.imgur.com/bhYCp4u.png' height=159 width=486 />

`npx` is a program which comes with `node` which will run `create-react-app` for us (create-react-app is a special program available through `npx`)


[download node from here if you haven't already](https://nodejs.org/en/download/)

you may have to close your command prompt and reopen it after the download completes

once `which npx` returns with some file location (as in the image) we're ready to create an app


`cd ~/code` (just to make sure we're in the right place)

`npx create-react-app test-app`

<img src='https://i.imgur.com/5v747hI.png' height=156 width=756 />



this should take a minute to download everything

once it's done, we can see the new directory

`ls`

the directory is named `test-app` because we told `create-react-app` to name it that

and we can `cd` into the project directory

`cd test-app`

and we can see what files we have

`ls`


<img src='https://i.imgur.com/dxnWCIW.png' height=140 width=886 />


we'll review each of these files in time - for now it's important to know that your code goes in `src` (the source code directory)


now, our final test, we'll run the "local dev server" (webpack and babel and all the other programs which work together to let us code on our own machine)

to do that, the command we will issue is

`npm start`

`npm` is `npx`'s older brother - `npx ...` runs programs from the internet, `npm start` runs the programs we have in this project directory.

here, `npm start` should compile the code (which is the default code from create-react-app still), and say "Compiled successfully"

now that it's running, you can go to [http://localhost:3000](http://localhost:3000) and see the default react app in your browser



### coding our app

now that we have a react app running we can write our own code

(make sure to leave it running in your command line... if you want to kill it, hit ctrl + c, to restart it, `npm start` again)


let's take a look at the files in our src directory

`ls src`

<img src='https://i.imgur.com/3MmR7WP.png' height=152 width=783 />


for now, our main concern will be with `App.js`

let's give it a read

<sub>./src/App.js</sub>
```jsx
import React from 'react';
import logo from './logo.svg';
import './App.css';

function App() {
  return (
    <div className="App">
      <header className="App-header">
        <img src={logo} className="App-logo" alt="logo" />
        <p>
          Edit <code>src/App.js</code> and save to reload.
        </p>
        <a
          className="App-link"
          href="https://reactjs.org"
          target="_blank"
          rel="noopener noreferrer"
        >
          Learn React
        </a>
      </header>
    </div>
  );
}

export default App;
```

we import React (needed for JSX)

we import a logo image (part of the default page... we can get rid of this later)

we import our css file (of course)

we declare a function called `App` which returns some JSX (which you should recognize from the page)

we export our `App` function for other files to use

---

here it might be useful to get the feel of JSX again - just by editing the JSX which renders to the page

as soon as you save (with no bugs), the page should auto-refresh with your new content.

it is in this file that we'll do our coding lesson in the next section, so get comfortable!



### using git from the command line

the last topic to review before jumping int othe code is git - our source control manager

people used to email eachother code. that was bad. now git does that for us.

in this review, we'll make a github repo and push our code to it

to do this, we'll learn how to `commit` code (save it to git)

and we'll learn to `push` code (tell git to send our committed code to github)

---


when we ran `npx create-react-app`, we got a whole react project ready to go

this includes turning out normal project directory into a "git repo"

what is a "git repo"?

it's a normal directory with some extra files which track the historical changes of all of our files

we can see this by running `ls` with the `-a` flag (all files) from the project root


`cd ~/code/test-app`

(if you need)


`ls -a`

<img src='https://i.imgur.com/xo3XiLT.png' width=782 height=159 />


we now see the hidden files (starts with a niquda) including `.git`

inside that directory is a database of local files maintained by the `git` program - how it works is beyond the scope of this lesson - our goal for now is just to use `git`


now that we know for sure our project is a git repo (because it has a .git directory) we can `commit` our changes to the local repo, and `push` them to github


first, let's see if we have any changes

`git status`

<img src='https://i.imgur.com/LgCF0FG.png' width=722 height=134 />

that message means I haven't changed any files yet. So I'll go delete the logo from the page and save the file

<sub>./src/App.js</sub>
```diff
import React from 'react';
-import logo from './logo.svg';
import './App.css';

function App() {
  return (
    <div className="App">
      <header className="App-header">
-        <img src={logo} className="App-logo" alt="logo" />
        <p>
          Edit <code>src/App.js</code> and save to reload.
        </p>
        <a
          className="App-link"
          href="https://reactjs.org"
          target="_blank"
          rel="noopener noreferrer"
        >
          Learn React
        </a>
      </header>
    </div>
  );
}

export default App;
```

now when we do `git status`

<img src='https://i.imgur.com/SX6izzH.png' width=886 height=254 />

we see a file has changed (red)


now we should `commit` that change to git

`git commit -am "deleted logo"`

<img src='https://i.imgur.com/oxlij2H.png' width=848 height=133 />


the `a` flag tells git to commit all the changes

the `m` flag tells git we will supply a commit message

our commit message "deleted logo" tells other devs what we did in this commit


now when we do `git status` we should see "working directory clean" again.

that means we committed our changes to git (the local database) and are ready to send it to github.


... or we would be, but we need to tell git where to save our code to first.

so, go to github, make a new repo

github will show you instructions on starting a project

the instruction we need from there is

`git remote add origin https://github.com/MYUSERNAME/MYPROJECT.git`

except with your username / projectname in there


once you've run that command, you should be able to push code with

`git push origin master`


now, refreshing the github page should bring up your code


git usually feels complicated for the first year or so

but it's actually really simple, and eventually it will win you over




## coding lesson

this lesson will introduce the (new) `useState` method from react

it is a bit like riding a bike - just try it out and see if you can get it moving, soon it'll be like you always understood it all along.

in our App component (the file ./src/App.js), we want to replace the default react app page with a login page for our app (whatever that is)



first, let's import `useState` from react

<sub>./src/App.js</sub>
```jsx
import React, { useState } from 'react';
import './App.css';

//...
```

which we will use to make two reactive variables (one for our username, one for our password)

```jsx
//...

function App() {
  const [username, setUsername] = useState('');
  const [password, setPassword] = useState('');
  
  return (
    <div className="App">

//...
```

the empty strings are our default values.


now, let's make the input boxes our variables will be bound to

```jsx
//...
        <input
            placeholder='Username'
            value={username}
            onChange={e=> setUsername(e.target.value)}
        />
        <input
            placeholder='Password'
            type='password'
            value={password}
            onChange={e=> setPassword(e.target.value)}
        />
//...
```

and a login button at the end of our file

```jsx
//...
        <button onClick={login}>Log in</button>
      </header>
    </div>
  );
}

export default App;
```


there's a bug you say?

of course, we haven't written the `login` function yet.


so just after we declared our variables

```jsx
//... useState declarations

const login = ()=>{
  if( username === 'nik' && password === 'guest')
    console.log('logged in!');
  else console.log('failure');
};

//... jsx
```

of course, your username and password can be different than mine

and yes, this is terrible security!

but - that's all there is to it.

please go ahead and commit / push your work and submit a link to me!



## more learning

https://reactjs.org/docs/hooks-reference.html

https://rangle.io/blog/simplifying-controlled-inputs-with-hooks/