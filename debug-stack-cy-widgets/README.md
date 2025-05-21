# dummy-stack

This dummy stack is meant for debugging only.
It can be used to check:
- Markdown rendering — Check this `README.md` file that showcase GitHub flavored markdown and compare it to [how GitHub renders it](https://github.com/Thomas-lhuillier/catalog-repo/blob/stacks/debug-stack/README.md)
- Terminal output styles — Run pipeline jobs to echo debugging content
- Pipeline resources and jobs, with combination of properties (parallel, do, try, on_success, on_failure…)

## Running a local worker on staging
In order run jobs on staging, you will need to deploy a local docker worker and expose it to the staging concourse server. Generally it's best to tag your local worker to avoid having your worker flooded by other jobs.

Use the following command to run a local worker.
To get the values for `CYCLOID_WORKER_TEAM` and `CYCLOID_WORKER_KEY`, open the modal for deploying a docker worker on the staging console workers page. 

```bash
export CYCLOID_WORKER_TEAM="replace_me"
export CYCLOID_WORKER_KEY="replace_me"
export TAG="replace_me"

docker run -it \
  --rm \
  --privileged \
  --name cycloid-worker \
  --env SCHEDULER_PORT=32224 \
  --env SCHEDULER_HOST=concourse.staging.cycloid.io \
  --env TEAM_ID=$CYCLOID_WORKER_TEAM \
  --env WORKER_KEY=$CYCLOID_WORKER_KEY \
  --env CONCOURSE_TAG=$TAG \
  cycloid/local-worker --baggageclaim-driver=overlay
```

---

---

---

# Markdown rendering crash test

> Markdown is a lightweight markup language that you can use to add formatting elements to plaintext text documents. Created by [John Gruber](https://daringfireball.net/projects/markdown/) in 2004, Markdown is now one of the world’s most popular markup languages.
> 
> - https://www.markdownguide.org/getting-started/#whats-markdown

## Headers 

```md
# This is an h1 tag
## This is an h2 tag 
### This is an h3 tag   
#### This is an h4 tag 
##### This is an h5 tag
###### This is an h6 tag
```

# This is an h1 tag
## This is an h2 tag 
### This is an h3 tag   
#### This is an h4 tag 
##### This is an h5 tag
###### This is an h6 tag
  
## Emphasis

```md
*This text will be italic*
_This will also be italic_
**This text will be bold**
__This will also be bold__
~~This text will be crossed out (strikethrough)~~ 
_You **can** combine them_
***All this text is bold and italic***
```

*This text will be italic*
_This will also be italic_
**This text will be bold**
__This will also be bold__
~~This text will be crossed out (strikethrough)~~ 
_You **can** combine them_
***All this text is bold and italic***

## Lists

### Unordered

```md
* Item 1
* Item 2
  * Item 2a
  * Item 2b
```

* Item 1
* Item 2
  * Item 2a
  * Item 2b


```md
- Item 1
- Item 2
  - Item 2a
  - Item 2b
```

- Item 1
- Item 2
  - Item 2a
  - Item 2b

### Ordered

```md
1. Item 1
1. Item 2
1. Item 3
   1. Item 3a
   1. Item 3b
```

1. Item 1
1. Item 2
1. Item 3
   1. Item 3a
   1. Item 3b

## Images 

```md
Format:  ![Alt Text](url)
Example: ![Image of Yaktocat](https://octodex.github.com/images/yaktocat.png)
```

![Image of Yaktocat](https://octodex.github.com/images/yaktocat.png)

## Links 

```md
http://github.com - automatic!
```

http://github.com - automatic!

```md
[GitHub](http://github.com)
```

[GitHub](http://github.com)

## Blockquotes

```md
As Kanye West said:

> We're living the future so
> the present is our past.
```

As Kanye West said:

> We're living the future so
> the present is our past.

Blockquotes can be nested.

```md
> Dorothy followed her through many of the beautiful rooms in her castle.
>
>> The Witch bade her clean the pots and kettles and sweep the floor and keep the fire fed with wood.
```

> Dorothy followed her through many of the beautiful rooms in her castle.
>
>> The Witch bade her clean the pots and kettles and sweep the floor and keep the fire fed with wood.

## Horizontal Rules

Horizontal rules can be created using three or more asterisks `\*\*\*`, dashes `\-\-\-`, or underscores `\_\_\_` on a line by themselves.

***

---

___

## Inline code

```md
I think you should use an `<addr>` element here instead.
```

I think you should use an `<addr>` element here instead.

## Fenced Code Blocks 

### No highlighting 

````md
```
if (isAwesome){
  return true
}
```
````

```
if (isAwesome) {
  return true
}
```

### Highlighting 

````md
```javascript 
if (isAwesome){
  return true
}
```
````

```javascript
if (isAwesome) {
  return true
}
```

## Tables 

```md
| First Header  | Second Header |
| ------------- | ------------- |
| Content Cell  | Content Cell  |
| Content Cell  | Content Cell  |
```

| First Header  | Second Header |
| ------------- | ------------- |
| Content Cell  | Content Cell  |
| Content Cell  | Content Cell  |

```md
| Left-aligned | Center-aligned | Right-aligned |
| :---         |     :---:      |          ---: |
| git status   | git status     | git status    |
| git diff     | git diff       | git diff      |
```

| Left-aligned | Center-aligned | Right-aligned |
| :---         |     :---:      |          ---: |
| git status   | git status     | git status    |
| git diff     | git diff       | git diff      |

Your Markdown does't have to be pretty. 

There must be at least 3 dashes separating each header cell. The outer pipes (`|`) are optional, and you don't need to make the table columns line up prettily.

```md
Less | Pretty | Markdown 
--- | --- | ---
1 | 2 | 3 
*Still* | `renders` | **as expected**
4 | 5 | 6
```

Less | Pretty | Markdown 
--- | --- | ---
1 | 2 | 3 
*Still* | `renders` | **as expected**
4 | 5 | 6

## Blackslash escape

Markdown allows you to use backslash escapes to generate literal characters which would otherwise have special meaning in Markdown’s formating syntax.

| Name                  | Markdown  | Result |
| --------------------- | --------- | ------ |
| backslash             | `\\`      | \\     |
| backtick              | `` \` ``  | \`     |
| asterisk              | `\*`      | \*     |
| underscore            | `\_`      | \_     |
| curly braces          | `\{\}`    | \{\}   |
| square brackets       | `\[\]`    | \[ \]  |
| parentheses           | `\(\)`    | \(\)   |
| hash mark             | `\#`      | \#     |
| plus sign             | `\+`      | \+     |
| minus sign (hyphen)   | `\-`      | \-     |
| dot                   | `\.`      | \.     |
| exclamation mark      | `\!`      | \!     |

## Task Lists

```md
- [x] this is a complete item 
- [ ] this is an incomplete it
```

- [x] this is a complete item 
- [ ] this is an incomplete it

## Inline HTML

Markdown also supports raw HTML.

```html
<dl>
  <dt>First Term</dt>
  <dd>This is the definition of the first term.</dd>
  <dt>Second Term</dt>
  <dd>This is one definition of the second term. </dd>
  <dd>This is another definition of the second term.</dd>
</dl>
```

<dl>
  <dt>First Term</dt>
  <dd>This is the definition of the first term.</dd>
  <dt>Second Term</dt>
  <dd>This is one definition of the second term. </dd>
  <dd>This is another definition of the second term.</dd>
</dl>

```html
<p>Markdown and HTML does *not* work **well**. Use <i>HTML</i> <b>tags</b> instead.</p>
```

<p>Markdown in HTML does *not* work **well**. Use <i>HTML</i> <b>tags</b> instead.</p>

## Emoji

```md
:+1: :sparkles: :camel: :tada: :rocket: :metal:
```

:+1: :sparkles: :camel: :tada: :rocket: :metal:
