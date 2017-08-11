---
layout: left
---

# `style50`

`style50` is a command-line tool with which you can check your code for consistency with [CS50's style guide](style) (for C). If your code isn't styled consistently, `style50` will summarize the changes you should make to your code, as by highlighting in <span class="bg-green p-1 text-white">green</span> characters you should add and highlighting in <span class="bg-red p-1 text-white">red</span> characters you should delete.

## Usage

To check your code's style, execute

```
style50 file
```

where `file` is the (path to some) file whose style you'd like to check.

## Examples

### Addition

Consider the code below, wherein the call to `printf` isn't properly indented.

```
#include <stdio.h>

int main(void)
{
printf("hello, world\n");
}
```

Given that code as input, `style50` will output

<pre>#include &lt;stdio.h&gt;

int main(void)
{
<span class="bg-green p-0">    </span>printf("hello, world\n");
}</pre>

wherein highlighted in green are four spaces that should be added for style's sake.

### Deletion

Consider the code below, wherein the curly braces are unnecessarily indented.

```
#include <stdio.h>

int main(void)
    {
    printf("hello, world\n");
    }
```

Given that code as input, `style50` will output

<pre>#include &lt;stdio.h&gt;

int main(void)
<span class="bg-red p-0">    </span>{
    printf("hello, world\n");
<span class="bg-red p-0">    </span>}</pre>

wherein highlighted in red are spaces that should be deleted for style's sake.

## Modes

By default, `style50` operates in [`character`](#character) mode, but you can specify other modes with `-o` or `--output`.

Consider the code below for a look at these modes.

```
#include <stdio.h>

int main(void)
{
    printf("hello, world\n");
}
```

### `character`

In `character` mode (the default), `style50` compares its input against CS50's style guide character by character, as in the below.

<pre>#include &lt;stdio.h&gt;

int main(void)
<span class="bg-green p-0">{\n</span>
    <span class="bg-red p-0">{\n</span>
printf("hello, world\n");
<span class="bg-red p-0">    }</span></pre>

### `split`

In `split` mode, `style50` displays its input and output side by side, as in the below.

<pre>#include &lt;stdio.h&gt;               #include &lt;stdio.h&gt;

int main(void)                   int main(void)
    <span class="text-red p-0">{</span>                            <span class="text-green p-0">{</span>
printf("hello, world\n");        <span class="bg-green p-0">    </span>printf("hello, world\n");
    <span class="text-red p-0">}</span>                            <span class="text-green p-0">}</span></pre>

### `unified`

In `unified` mode, `style50` displays its output line by line, akin to [`git-diff`](https://git-scm.com/docs/git-diff), as in the below.

<pre>  #include &lt;stdio.h&gt;
  
  int main(void)
<span class="text-red p-0">-     {</span>
<span class="text-green p-0">+ {</span>
<span class="text-red p-0">- printf("hello, world\n");</span>
<span class="text-green p-0">+     printf("hello, world\n");</span>
<span class="text-red p-0">-     }</span>
<span class="text-green p-0">+ }</span></pre>

## Installation

`style50` is already installed for you in [CS50 IDE](https://cs50.io/), so no need to install it yourself; simply use it as directed!

If you'd like to install `style50` on your own Mac or PC, so that you can check your code's style without using CS50 IDE, you'll need a command-line environment:

- If running Linux or the like, you already have one! Open a terminal window in your usual way.
- If running Mac OS, you already have one! Open **Applications > Utilities > Terminal**.
- If running Windows, you'll need to install the [Windows Subsystem for Linux](https://msdn.microsoft.com/commandline/wsl/about), which is only supported on Windows 10. Once installed, [run `bash`](https://blogs.windows.com/buildingapps/2016/03/30/run-bash-on-ubuntu-on-windows/).

To install `style50` within that command-line environment:

1. [Install Python](https://www.python.org/downloads/) 2.7 or higher, if not already installed.

1. Install `pip`, as via 

   ```
   sudo easy_install pip
   ```

   if not already installed.

1. Execute 

   ```
   sudo pip install style50
   ```
   to install `style50` itself.

## Upgrading

Execute

```
sudo pip install --upgrade style50
```

to upgrade `style50`, once installed.

## Implementation Details

To view the source code for `style50`, see <https://github.com/cs50/style50>.