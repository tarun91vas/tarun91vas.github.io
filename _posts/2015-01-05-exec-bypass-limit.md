---
layout: post
title: Bypassing exec() command length limit for windows using PHP
subtitle: Dirty hack
tags: [proc_open, php, cmd, limit]
---

Recently I was working on an application which uses *exec()* function of *php* to execute some commands. Apparently I observed abnormal behavior for long commands, there was no output and no error. After some research, I came across facts below:
<ul>
    <li>On command prompt, total length of the command that you can use cannot exceed more than 2047 or 8191 characters.(windows XP or later). [<a title="MSLink" href="http://support.microsoft.com/kb/830473" target="_blank" shape="rect">Source</a>]</li>
    <li>The maximum command line length for the <em>CreateProcess function</em> is 32767 characters. <em>CreateProcess</em> is the core function for creating processes. If you are reaching <em>CreateProcess</em> by some other means, then the limits may vary.[<a title="link2" href="http://blogs.msdn.com/b/oldnewthing/archive/2003/12/10/56028.aspx" target="_blank" shape="rect">Source</a>]</li>
</ul>
Now the solution is to reach <em>CreateProcess</em> in php. Well, it is not recommended to write software which utilizes such big command lengths for operation. But if you are still stuck with the case , the<strong> proc_open()</strong> function of php is the solution which provides greater degree of control over the program execution. I did not get exact solution to the problem online that’s why I decided to write this article. Refer proc_open() <a title="proc_open" href="http://php.net/manual/en/function.proc-open.php" target="_blank" shape="rect">manual</a> for details.

So you just have to call proc open and enable <em><strong>bypass_shell</strong> </em>to <strong>TRUE</strong>, and it will not take path through command prompt .<strong> </strong>The code is given below:

{% highlight php linenos %}
$cmd="my command";

$descriptorspec = array(
    0 => array("pipe", "r"),  // stdin is a pipe that the child will read from
    1 => array("pipe", "w"),  // stdout is a pipe that the child will write to
    2 => array("pipe", "w")
);

$options=array('bypass_shell' => TRUE);

$process = proc_open($cmd, $descriptorspec, $pipes, NULL, NULL,$options);

if (is_resource($process)) {
    $output=stream_get_contents($pipes[1]);

    fclose($pipes[0]);fclose($pipes[1]);fclose($pipes[2]);

    proc_close($process);
}
{% endhighlight %}

This is just a quick worka around. Hope it helps !
<br clear="none" /><br clear="none" />

