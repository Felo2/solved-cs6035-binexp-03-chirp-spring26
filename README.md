# solved-cs6035-binexp-03-chirp-spring26
**TO GET THIS SOLUTION VISIT:** [[SOLVED] CS6035 binexp 03_chirp Spring26](https://www.ankitcodinghub.com/product/cs6035-binexp-03_chirp-spring26-solved/)


---

📩 **If you need this solution or have special requests Email:** ankitcoding@gmail.com 
📱 **WhatsApp:** +1 419 877 7882  
📄 **Get a quote instantly using this form:** [Ask Homework Questions](https://www.ankitcodinghub.com/services/ask-homework-questions/)

*We deliver fast, professional, and affordable academic help.*

---

<h2>Description</h2>



<div class="kk-star-ratings kksr-auto kksr-align-center kksr-valign-top" data-payload="{&quot;align&quot;:&quot;center&quot;,&quot;id&quot;:&quot;145130&quot;,&quot;slug&quot;:&quot;default&quot;,&quot;valign&quot;:&quot;top&quot;,&quot;ignore&quot;:&quot;&quot;,&quot;reference&quot;:&quot;auto&quot;,&quot;class&quot;:&quot;&quot;,&quot;count&quot;:&quot;1&quot;,&quot;legendonly&quot;:&quot;&quot;,&quot;readonly&quot;:&quot;&quot;,&quot;score&quot;:&quot;5&quot;,&quot;starsonly&quot;:&quot;&quot;,&quot;best&quot;:&quot;5&quot;,&quot;gap&quot;:&quot;4&quot;,&quot;greet&quot;:&quot;Rate this product&quot;,&quot;legend&quot;:&quot;5\/5 - (1 vote)&quot;,&quot;size&quot;:&quot;24&quot;,&quot;title&quot;:&quot;CS6035 binexp  03_chirp Spring26&quot;,&quot;width&quot;:&quot;138&quot;,&quot;_legend&quot;:&quot;{score}\/{best} - ({count} {votes})&quot;,&quot;font_factor&quot;:&quot;1.25&quot;}">

<div class="kksr-stars">

<div class="kksr-stars-inactive">
            <div class="kksr-star" data-star="1" style="padding-right: 4px">


<div class="kksr-icon" style="width: 24px; height: 24px;"></div>
        </div>
            <div class="kksr-star" data-star="2" style="padding-right: 4px">


<div class="kksr-icon" style="width: 24px; height: 24px;"></div>
        </div>
            <div class="kksr-star" data-star="3" style="padding-right: 4px">


<div class="kksr-icon" style="width: 24px; height: 24px;"></div>
        </div>
            <div class="kksr-star" data-star="4" style="padding-right: 4px">


<div class="kksr-icon" style="width: 24px; height: 24px;"></div>
        </div>
            <div class="kksr-star" data-star="5" style="padding-right: 4px">


<div class="kksr-icon" style="width: 24px; height: 24px;"></div>
        </div>
    </div>

<div class="kksr-stars-active" style="width: 138px;">
            <div class="kksr-star" style="padding-right: 4px">


<div class="kksr-icon" style="width: 24px; height: 24px;"></div>
        </div>
            <div class="kksr-star" style="padding-right: 4px">


<div class="kksr-icon" style="width: 24px; height: 24px;"></div>
        </div>
            <div class="kksr-star" style="padding-right: 4px">


<div class="kksr-icon" style="width: 24px; height: 24px;"></div>
        </div>
            <div class="kksr-star" style="padding-right: 4px">


<div class="kksr-icon" style="width: 24px; height: 24px;"></div>
        </div>
            <div class="kksr-star" style="padding-right: 4px">


<div class="kksr-icon" style="width: 24px; height: 24px;"></div>
        </div>
    </div>
</div>


<div class="kksr-legend" style="font-size: 19.2px;">
            5/5 - (1 vote)    </div>
    </div>
<h2 id="step-e4-exercise-3" class="akch-demoted-h1">Step E.4: Exercise 3</h2>
<h2 id="03_chirp-15-pts">03_chirp [15 pts]</h2>
<h3 id="resources">Resources</h3>
<ul>
<li><a href="https://www.geeksforgeeks.org/c/format-specifiers-in-c/">Format String Specifiers</a></li>
</ul>
<h3 id="challenge-instructions">Challenge Instructions</h3>
There have been a number of defensive upgrades made to binary security over the years designed to protect against memory corruption vulnerabilities like the stack-based buffer overflow.

In this challenge, we’ll cross-examine a few in particular:&nbsp;<code class="language-plaintext highlighter-rouge">stack canaries</code>&nbsp;and&nbsp;<code class="language-plaintext highlighter-rouge">PIE</code>.

<h4 id="what-are-stack-canaries">What are stack canaries?</h4>
When you’ve been performing basic buffer overflow exploits to hijack the control flow of a binary, this has typically been done by simply overwriting the&nbsp;<code class="language-plaintext highlighter-rouge">ret</code>&nbsp;address stored in the stack that the function’s instructor pointer would reference.

Stack canaries frustrate this process by doing a couple things:

<ol>
<li>At compile time, the source code is slightly modified around these ret operations; the compilers inject some additional operations in order to protect/preserve the integrity of the address referenced by the&nbsp;<code class="language-plaintext highlighter-rouge">ret</code>&nbsp;operation.</li>
<li>The way that the address is protected is that a runtime-determined random value (aka the “canary”) is inserted in-between that address and the rest of the calling function’s frame. When the function terminates, that random value is checked by the binary to determine if it’s changed; if it has, then the binary presumes that an overflow has taken place and terminates the whole process.</li>
</ol>
There are a few rules/behaviors that stack canaries follow that are worth being mindful of.

<ul>
<li>In our 64-bit system, stack canaries are always sized 8 bytes.</li>
<li>Stack canaries are set when the program starts up and do not change after. The same stack canary is even passed along to any child processes it spawns (i.e. they do not create their own stack canaries). Stack canaries are only reset when the process restarts.</li>
<li>The relative position of stack canaries within the stack do not change run-over-run (though the absolute address may change due to things like ASLR); stack canaries will always be positioned between all other variables within a function and the return address.</li>
</ul>
<h4 id="what-is-pie">What is PIE?</h4>
Position Independent Executables (PIE) is a hardening measure that binaries can likewise embrace at compile-time. In brief, PIE randomizes the address space of the binary’s assembly at runtime making it practically impossible to statically reference particular instructions in our exploits.

Below is a screenshot of the same binary objdump compiled with and without PIE:

<img data-recalc-dims="1" decoding="async" data-src="https://i0.wp.com/github.gatech.edu/pages/cs6035-tools/cs6035-tools.github.io/Projects/BinExp/si_chirp/pie-no-pie.png?w=980&amp;ssl=1" alt="A side-by-side comparison of the objdump output between the same code compiled with and without PIE." src="data:image/svg+xml;base64,PHN2ZyB3aWR0aD0iMSIgaGVpZ2h0PSIxIiB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciPjwvc3ZnPg==" class="lazyload">

In the case of the PIE-compiled binary, instead of addresses the&nbsp;<code class="language-plaintext highlighter-rouge">objdump</code>&nbsp;dumps&nbsp;<em>offsets</em>.

Like stack canaries, PIE has a few rules/behaviors that are worth being mindful of:

<ul>
<li>At runtime, a PIE base address is randomly set and all of the binary’s instructions are offset from that base address. Each individual instruction is not seeded with its own randomized value, but are instead offset from this base address.</li>
<li>The PIE base address typically ends in 000 due to memory pages being the units of randomization, sized at 0x1000 bytes. For example, it might look like: 0x5b930239a000.</li>
</ul>
<h4 id="memory-leaks--format-strings">Memory Leaks &amp; Format Strings</h4>
On their face, both of these protections may seem insurmountable:

<ol>
<li>We don’t know the value of the canary at runtime, so overflowing it with anything other than itself will prevent our exploit.</li>
<li>We don’t know the value of the PIE base address at runtime, so even if we were to correctly set the canary, we couldn’t reliably execute other code in the binary.</li>
</ol>
The big condition on both of the above is that we cannot know these values. If we did, then we could overcome both of these problems. This is why vulnerabilities like&nbsp;<code class="language-plaintext highlighter-rouge">memory leaks</code>&nbsp;are very concerning.

Memory leaks can manifest in a number of ways, but one of the most common is by way of&nbsp;<code class="language-plaintext highlighter-rouge">format-string vulnerabilities</code>. When&nbsp;<code class="language-plaintext highlighter-rouge">printf()</code>&nbsp;is called to print a string, it doesn’t simply print the string; it goes to an address on the stack and prints the contents that address points to. If&nbsp;<code class="language-plaintext highlighter-rouge">printf()</code>&nbsp;implicitly trusts user input…

<div class="table-wrapper">
<table>
<tbody>
<tr>
<td>Implicit Trust</td>
<td>Explicitly defined</td>
</tr>
<tr>
<td><code class="language-plaintext highlighter-rouge">printf(userinput)</code></td>
<td><code class="language-plaintext highlighter-rouge">printf("%s", userinput)</code></td>
</tr>
</tbody>
</table>
</div>
…then the user can forcefully decide what type of data is being rendered by&nbsp;<code class="language-plaintext highlighter-rouge">printf()</code>. As an example, this might look like…

<strong>userinput =</strong>&nbsp;<code class="language-plaintext highlighter-rouge">"%x"</code>&nbsp;→&nbsp;<strong>printf(</strong><code class="language-plaintext highlighter-rouge">userinput</code><strong>)</strong>&nbsp;→&nbsp;<strong>printf(</strong><code class="language-plaintext highlighter-rouge">"%x"</code><strong>)</strong>

This is a problem! By passing a format specifier (<code class="language-plaintext highlighter-rouge">%x</code>) as a placeholder value but not specifying what’s meant to go there (i.e.&nbsp;<code class="language-plaintext highlighter-rouge">printf("%x", somevariable)</code>) the&nbsp;<code class="language-plaintext highlighter-rouge">printf()</code>&nbsp;function by default reads values off of the top of the stack instead. We can leak multiple sequential values (e.g. “%x %x %x %x…”) or even particular values (i.e. the 5th value via “%4$x”).

Note: the “%x” format specifier returns hex representations of whatever’s next off the stack, but there are other format specifiers we might choose to use instead that may be more useful/insightful.

Using this mechanism, you can leak the stack memory at&nbsp;<em>runtime</em>&nbsp;which – as we mentioned earlier, sets us up to compromise the binary in its entirety.

<h3 id="guidance">Guidance</h3>
<ul>
<li>Your goal for this challenge is to exploit a format-string vulnerability in order to leak both the stack canary AND a PIE address, then perform a buffer overflow.</li>
<li>You can use GDB to identify any canaries and the PIE base address. This is useful in affirming that you’ve correctly identified/calculated them through a memory leak. The GDB commands are:
<ul>
<li><code class="language-plaintext highlighter-rouge">canary</code></li>
<li><code class="language-plaintext highlighter-rouge">piebase</code></li>
</ul>
</li>
<li>By default GDB disables ASLR, which affects PIE behavior. If you don’t change this, you might be stumped as to why the PIE base address always appears as something like 0x555555554000. If you want a more representative experience, you need to turn this feature off before running the binary in ASLR with the following GDB command:
<ul>
<li><code class="language-plaintext highlighter-rouge">set disable-randomization off</code></li>
</ul>
</li>
<li>Because setting breakpoints at random addresses is practically impossible, you can instead make use of setting breakpoints by offset in GDB via:
<ul>
<li><code class="language-plaintext highlighter-rouge">breakrva 0x&lt;offset&gt;</code></li>
<li>As an example, we can break on the “call” operation from the earlier screenshot with&nbsp;<code class="language-plaintext highlighter-rouge">breakrva 0x17f0</code>.</li>
</ul>
</li>
<li>Addresses that start with 0x7ff generally (but not always) are associated with external library functions (i.e. libc). These are NOT useful in calculating your PIE base as they are separately randomized.</li>
</ul>
