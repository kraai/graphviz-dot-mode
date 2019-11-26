This manual describes how to install and use `graphviz-dot-mode`, an
Emacs package for working with Graphviz DOT-format files.

Copyright © 2017 Daniel Birket.

> Permission is granted to copy, distribute and/or modify this document
> under the terms of the GNU Free Documentation License, Version 1.3 or
> any later version published by the Free Software Foundation; with no
> Invariant Sections, with no Front-Cover Texts, and with no Back-Cover
> Texts. A copy of the license is included in the section entitled GNU
> Free Documentation License.

This is the `graphviz-dot-mode` Manual, edition 0.3.10.a, by Daniel
Birket, updated November 20, 2017, which describes how to install and
use the Emacs package `graphviz-dot-mode`, version 0.3.10, released 25
May 2015, which was written by and Copyright © 2002-2015 Pieter Pareit,
et al. (See <http://ppareit.github.io/graphviz-dot-mode/>)

This document was composed using Emacs v25.2.1 (Richard M. Stallman, et
al. See <https://www.gnu.org/software/emacs/>) and compiled from `.texi`
source with GNU Texinfo v6.4 (Richard M. Stallman, et al. See
<https://www.gnu.org/software/texinfo/>) to `docbook` format (OASIS See
<http://docbook.org>, then converted to this format using Pandoc
v1.19.2.1 (John MacFarlane, et al. <http://pandoc.org>) This format has
no index. Graphviz is by AT&T Labs Research. (See <http://graphviz.org>)

This manual is based upon the comments and doc strings in the
`graphviz-dot-mode.el` source code, which begins with:

    ;;; graphviz-dot-mode.el --- Mode for the dot-language used by graphviz (att).

    ;; Copyright (C) 2002 - 2015 Pieter Pareit <pieter.pareit@gmail.com>

    ;; This program is free software; you can redistribute it and/or
    ;; modify it under the terms of the GNU General Public License as
    ;; published by the Free Software Foundation; either version 2 of
    ;; the License, or (at your option) any later version.

    ;; This program is distributed in the hope that it will be
    ;; useful, but WITHOUT ANY WARRANTY; without even the implied
    ;; warranty of MERCHANTABILITY or FITNESS FOR A PARTICULAR
    ;; PURPOSE.  See the GNU General Public License for more details.
    …

    ;; Authors: Pieter Pareit <pieter.pareit@gmail.com>
    ;;          Rubens Ramos <rubensr AT users.sourceforge.net>
    ;;          Eric Anderson http://www.ece.cmu.edu/~andersoe/
    ;; Maintainer: Pieter Pareit <pieter.pareit@gmail.com>
    ;; Homepage: http://ppareit.github.com/graphviz-dot-mode/
    ;; Created: 28 Oct 2002
    ;; Last modified: 25 May 2015
    ;; Version: 0.3.10
    ;; Keywords: mode dot dot-language dotlanguage graphviz graphs att

Introduction
============

This manual describes how to install and use `graphviz-dot-mode`, an
Emacs package for working with Graphviz DOT-format files. The features
of this package help you to create `.dot` or `.gv` files containing
syntax compatible with the separate Graphviz package and use Graphviz to
convert these files to diagrams.

Graphviz is a set of open source graph visualization tools created by
AT&T Labs Research. A graph is a way of representing information as a
network of connected nodes (shapes) and edges (lines). Graphviz is
documented at <http://graphviz.org>.

The powerful text editor, Emacs, was created in 1976 by Richard
Stallman. It is highly customizable and has 40 years of other
extensions. GNU Emacs is documented at
<https://www.gnu.org/software/emacs/>. XEmacs is documented at
<http://www.xemacs.org>.

Installing
==========

This chapter describes how to install `graphviz-dot-mode`.

Recommended Installation
------------------------

The recommended way to install the package `graphviz-dot-mode` is to use
`package.el` and `M-x package-install`.

To install `graphviz-dot-mode`, first add the MELPA Stable archive to
the list of archives used by `package.el` (if it is not already there) by
adding the following lines to your `.emacs` or other Emacs startup file.
Then restart Emacs.

    (require 'package)
    (add-to-list 'package-archives
                 '("melpa-stable" . "https://stable.melpa.org/packages/"))
                 
    (package-initialize)

(For more detailed and comprehensive instructions about using MELPA,
please see <https://melpa.org/#/getting-started>.)

After restarting Emacs, type the following to install
`graphviz-dot-mode`.

`M-x package-install RET graphviz-dot-mode RET`.

When installed this way using the package manager, `graphviz-dot-mode`
will be activated automatically for file names ending in either `.dot`
or `.gv`.

Installing by Hand
------------------

You can manually download and install `graphviz-dot-mode`, but it is
best to use the recommended method above if you don’t already know how
to manually install an Emacs program.

You may download `graphviz-dot-mode.el` from
<http://ppareit.github.io/graphviz-dot-mode/> and follow the
instructions that you find there.

Installing this Info Manual
---------------------------

This section describes how to install this manual so that it may be used
from within Emacs using its `info` reader.

1.  Obtain the file containing the info-format version of this manual,
    `graphviz-dot-mode.info.gz` (See
    <https://github.com/daniel-birket/graphviz-dot-mode>.)

2.  In Emacs, use `C-h v Info-directory-listRET` to display the contents
    of the `Info-directory-list` variable. (This may be the same as the
    INFOPATH environment variable.)

3.  Copy the `graphviz-dot-mode.info.gz` file to one of the directories
    in the `Info-directory-list` variable.

4.  Use `install-info` to add an entry for the new
    `graphviz-dot-mode.info.gz` file into the `dir` file in the info
    directory where you copied the file.

5.  In Emacs, use `C-h i d m graphviz-dot-mode RET` to display this help
    file.

The `Makefile` in the `texinfo` subdirectory of the GitHub archive at
<https://github.com/daniel-birket/graphviz-dot-mode> includes an option
to install the info file with `make install`. You must first modify the
variables in the top of the Makefile to use the correct directories and
files for your system.

You must install GNU Texinfo v6.4 to use `install-info` or the
`Makefile`.

Using `graphviz-dot-mode`
=========================

This chapter describes how to use `graphviz-dot-mode`.

Compiling & Viewing
-------------------

This section describes how to use compile and view functions. See
[Compile & View Variables](#Compile-_0026-View-Variables).

`C-c c` (`compile`)  
This command compiles the current dot file visited by the Emacs buffer.
The output file is in the same directory and has the extension
determined by the variable `graphviz-dot-preview-extension`.

`` C-x ` `` (`next-error`)  
This command will jump to the location in the source file of the next
error from the most recent compile. Use `C-c c` to compile first.

`C-c p` (`graphviz-dot-preview`)  
This command compiles and then (if it compiled successfully) shows the
output of the current dot file visited by the Emacs buffer, provided
that GNU Emacs or XEmacs is running on a graphical display capable of
displaying the graphic file output by `dot`.

See `image-file-name-extensions` in GNU Emacs or `image-formats-alist`
in XEmacs to customize the graphic files that can be displayed.

`C-c v` (`graphviz-dot-view`)  
This command invokes an external viewer specified by the variable
`graphviz-dot-view-command`. If `graphviz-dot-view-edit-command` is `t`,
you will be prompted to enter a new `graphviz-dot-view-command`. If
`graphviz-dot-save-before-view` is `t`, the buffer is saved before the
external viewer command is invoked.

(See <http://graphviz.org/content/resources> for a list of Graphviz
viewers and editors.)

Editing
-------

This section describes how to edit with `graphviz-dot-mode`. See
[Editing Variables](#Editing-Variables).

### Indenting

`C-M-q` (`graphviz-dot-indent-graph`)  
This command will indent the graph, diagraph, or subgraph at point and
any subgraph within it.

`TAB`  
This key will automatically indent the line. It does not perform
completion.

`M-j` (`comment-indent-newline`)  
See [Commenting](#Commenting)

`RET` (`electric-graphviz-dot-terminate-line`)  
If the variable `graphviz-dot-auto-indent-on-newline` is `t`, `RET` will
insert a newline and indent the next line.

`{` (`electric-graphviz-dot-open-brace`)  
If the variable `graphviz-dot-auto-indent-on-braces` is `t`, `{` will
insert a `{`, newline and indent the next line.

`}` (`electric-graphviz-dot-close-brace`)  
If the variable `graphviz-dot-auto-indent-on-braces` is `t`, `}` will
insert a `}`, newline and indent the next line.

`;` (`electric-graphviz-dot-semi`)  
If the variable `graphviz-dot-auto-indent-on-semi` is `t`, `;` will
insert a `;`, newline and indent the next line.

### Completion

`M-t` (`graphviz-dot-complete-word`)  
This command will complete the attribute or value keyword at point. If
more than one completion is possible, a list is displayed in the
minbuffer.

See [Completion Variables](#Completion-Variables)

### Commenting

`M-;` (`comment-dwim`)  
This command will perform the comment command you want (Do What I Mean).
If the region is active and `transient-mark-mode` is on, it will comment
the region, unless it only consists of comments, in which case it will
un-comment the region. Else, if the current line is empty, it will
insert a blank comment line, otherwise it will append a comment to the
line and indent it.

Use `C-u M-;` to kill the comment on the current line.

`C-x C-;` (`comment-line`)  
This command will comment or un-comment the current line.

`M-j` (`comment-indent-newline`)  
This command will break line the at point and indent, continuing a
comment if within one. This indents the body of the continued comment
under the previous comment line.

`C-c C-c` (`comment-region`)  
This command will comment-out the region.

You may also use `M-;` (`comment-dwin`) to comment the region if
`transient-mark-mode` is on.

`C-c C-u` (`graphviz-dot-uncomment-region`)  
This command will un-comment the region.

You may also use `C-u M-;` (`comment-dwin`) to un-comment the region if
`transient-mark-mode` is on.

Customizing
===========

This section describes the customizable variables of
`graphviz-dot-mode`. You may customize variables by typing

`M-x graphviz-dot-customize RET`  
This function invokes the Emacs customization facility to allow you to
view and change the `graphviz-dot-mode` variables below.

Compile & View Variables
------------------------

This section describes variables related to compiling and viewing. See
[Compiling & Viewing](#Compiling-_0026-Viewing)

graphviz-dot-dot-program`graphviz-dot-dot-program`  
string, default: “dot”

This variable determines the command name (and path, if necessary) used
to invoke the Graphviz `dot` program. The `C-c
c` (`compile`) function invokes this command.

graphviz-dot-preview-extension`graphviz-dot-preview-extension`  
string, default “png”

This variable determines the file extension used for the `C-c c`
(`compile`) and `C-c p` (`graphviz-dot-preview`) functions. The format
for the compile command is

`dot -T<extension> <filename>.dot > <filename>.<extension>`

graphviz-dot-save-before-view`graphviz-dot-save-before-view`  
boolean, default `t`

This variable controls whether the buffer will be saved to the visited
file before the `C-c v` (`graphviz-dot-view`) function invokes the
external dot-file viewer command. Set this boolean variable to `t`
(true) or `nil` (false).

graphviz-dot-view-command`graphviz-dot-view-command`  
string, default: “doted %s”

This variable determines the command name (and path, if necessary) used
to invoke an external dot-file viewer program. The `C-c v`
(`graphviz-dot-view`) function invokes this command. The name of the
file visited by the buffer will be substituted for `%s` in this string.

(See <http://graphviz.org/content/resources> for a list of Graphviz
viewers and editors.)

graphviz-dot-view-edit-command`graphviz-dot-view-edit-command`  
boolean, default: `nil`

This variable controls whether you will be prompted for the external
dot-file viewer command name when you use `C-c v` `graphviz-dot-view`.
Set this to `t` (true) to be prompted to edit the viewer command
variable `graphviz-dot-view-command` every time you use `C-c v` or `nil`
to avoid the prompt.

Editing Variables
-----------------

This section describes variables related to editing. See
[Editing](#Editing)

### Indenting Variables

This subsection describes variables related to indenting.

graphviz-dot-auto-indent-on-braces`graphviz-dot-auto-indent-on-braces`  
`{` `}` boolean, default `nil`

This variable controls whether the functions
`electric-graphviz-dot-open-brace` and
`electric-graphviz-dot-close-brace` are called when `{` and `}` are
typed. Set this boolean variable to `t` (true) or `nil` (false).

graphviz-dot-auto-indent-on-newline`graphviz-dot-auto-indent-on-newline`  
boolean, default `t`

This variable controls whether the function
`electric-graphviz-dot-terminate-line` is called when a line is
terminated with a newline. Set this boolean variable to `t` (true) or
`nil` (false).

graphviz-dot-auto-indent-on-semi`graphviz-dot-auto-indent-on-semi`  
boolean, default `t`

This variable controls whether the function `electric-graphviz-dot-semi`
is called when a semicolon `;` is typed. Set this boolean variable to
`t` (true) or `nil` (false).

graphviz-dot-indent-width`graphviz-dot-indent-width`  
integer, default: `default-tab-width`

This variable determines the indentation used in `graphviz-dot-mode`
buffers.

### Completion Variables

This subsection describes variables related to completion.

graphviz-dot-delete-completions`graphviz-dot-delete-completions`  
boolean, default: `nil`

This variable controls whether the completion buffer is automatically
deleted when a key is pressed. Set this boolean variable to `t` (true)
or `nil` (false).

graphviz-dot-toggle-completions`graphviz-dot-toggle-completions`  
boolean, default: `nil`

This variable controls whether repeated use of `M-t`
`graphviz-dot-complete-word` will toggle the display of possible
completions in the minibuffer. If this variable is set to `nil`, when
there are more than one possible completions, a buffer will display all
completions. Set this boolean variable to `t` (true) or `nil` (false).

Keyword Variables
-----------------

This section describes the variables containing DOT-language keywords,
which may change if Graphviz is updated. You may update these variables
after new releases of Graphvizfrom
<http://www.graphviz.org/doc/schema/attributes.xml> .

graphviz-dot-attr-keywords`graphviz-dot-attr-keywords`  
list of strings, default: (“graph” “digraph” … )

This variable holds a list of keywords for attribute names in a graph.
This is used by the `M-t` auto completion function. The actual
completion tables are built when the mode is loaded, so changes to this
variable are not immediately visible.

graphviz-dot-value-keywords`graphviz-dot-value-keywords`  
list of strings, default: (“true” “false” … )

This variable holds a list of keywords for attribute values in a graph.
This is used by the `M-t` auto completion function. The actual
completion tables are built when the mode is loaded, so changes to this
variable are not immediately visible.

Mode Hook
---------

graphviz-dot-mode-hook`graphviz-dot-mode-hook`  
list of functions, default: `nil`

This variable determines which functions are called when
`graphviz-dot-mode` starts. To use it, add a line like below to your
`.emacs` or other startup file.

    (add-hook 'graphviz-dot-mode-hook 'my-hook)

Credits
=======

`graphviz-dot-mode` was written by:

-   Pieter Pareit <pieter.pareit@gmail.com>

-   Rubens Ramos <rubensr@users.sourceforge.net>

-   Eric Anderson <http://www.ece.cmu.edu/~andersoe/>

Other contributors are noted in the version history in the
`graphviz-dot-mode.el` file and the commit history on GitHub.

The source code is maintained on GitHub at
<https://github.com/ppareit/graphviz-dot-mode> by Pieter Pareit
(<pieter.pareit@gmail.com>). Please email software comments, suggestions
and corrections there.

This manual is maintained on GitHub at
<https://github.com/daniel-birket/graphviz-dot-mode> by Daniel Birket
(<danielb@birket.com>). Please submit document errata to the issue
tracker there.

GNU General Public License 2.0
==============================

Version 2, June 1991
    Copyright © 1989, 1991 Free Software Foundation, Inc.
    51 Franklin Street, Fifth Floor, Boston, MA  02110-1301, USA

    Everyone is permitted to copy and distribute verbatim copies
    of this license document, but changing it is not allowed.

**Preamble**

The licenses for most software are designed to take away your freedom to
share and change it. By contrast, the GNU General Public License is
intended to guarantee your freedom to share and change free software—to
make sure the software is free for all its users. This General Public
License applies to most of the Free Software Foundation’s software and
to any other program whose authors commit to using it. (Some other Free
Software Foundation software is covered by the GNU Lesser General Public
License instead.) You can apply it to your programs, too.

When we speak of free software, we are referring to freedom, not price.
Our General Public Licenses are designed to make sure that you have the
freedom to distribute copies of free software (and charge for this
service if you wish), that you receive source code or can get it if you
want it, that you can change the software or use pieces of it in new
free programs; and that you know you can do these things.

To protect your rights, we need to make restrictions that forbid anyone
to deny you these rights or to ask you to surrender the rights. These
restrictions translate to certain responsibilities for you if you
distribute copies of the software, or if you modify it.

For example, if you distribute copies of such a program, whether gratis
or for a fee, you must give the recipients all the rights that you have.
You must make sure that they, too, receive or can get the source code.
And you must show them these terms so they know their rights.

We protect your rights with two steps: (1) copyright the software, and
(2) offer you this license which gives you legal permission to copy,
distribute and/or modify the software.

Also, for each author’s protection and ours, we want to make certain
that everyone understands that there is no warranty for this free
software. If the software is modified by someone else and passed on, we
want its recipients to know that what they have is not the original, so
that any problems introduced by others will not reflect on the original
authors’ reputations.

Finally, any free program is threatened constantly by software patents.
We wish to avoid the danger that redistributors of a free program will
individually obtain patent licenses, in effect making the program
proprietary. To prevent this, we have made it clear that any patent must
be licensed for everyone’s free use or not licensed at all.

The precise terms and conditions for copying, distribution and
modification follow.

**TERMS AND CONDITIONS FOR COPYING, DISTRIBUTION AND MODIFICATION**

1.  This License applies to any program or other work which contains a
    notice placed by the copyright holder saying it may be distributed
    under the terms of this General Public License. The “Program”,
    below, refers to any such program or work, and a “work based on the
    Program” means either the Program or any derivative work under
    copyright law: that is to say, a work containing the Program or a
    portion of it, either verbatim or with modifications and/or
    translated into another language. (Hereinafter, translation is
    included without limitation in the term “modification”.) Each
    licensee is addressed as “you”.

    Activities other than copying, distribution and modification are not
    covered by this License; they are outside its scope. The act of
    running the Program is not restricted, and the output from the
    Program is covered only if its contents constitute a work based on
    the Program (independent of having been made by running the
    Program). Whether that is true depends on what the Program does.

2.  You may copy and distribute verbatim copies of the Program’s source
    code as you receive it, in any medium, provided that you
    conspicuously and appropriately publish on each copy an appropriate
    copyright notice and disclaimer of warranty; keep intact all the
    notices that refer to this License and to the absence of any
    warranty; and give any other recipients of the Program a copy of
    this License along with the Program.

    You may charge a fee for the physical act of transferring a copy,
    and you may at your option offer warranty protection in exchange for
    a fee.

3.  You may modify your copy or copies of the Program or any portion of
    it, thus forming a work based on the Program, and copy and
    distribute such modifications or work under the terms of Section 1
    above, provided that you also meet all of these conditions:

    1.  You must cause the modified files to carry prominent notices
        stating that you changed the files and the date of any change.

    2.  You must cause any work that you distribute or publish, that in
        whole or in part contains or is derived from the Program or any
        part thereof, to be licensed as a whole at no charge to all
        third parties under the terms of this License.

    3.  If the modified program normally reads commands interactively
        when run, you must cause it, when started running for such
        interactive use in the most ordinary way, to print or display an
        announcement including an appropriate copyright notice and a
        notice that there is no warranty (or else, saying that you
        provide a warranty) and that users may redistribute the program
        under these conditions, and telling the user how to view a copy
        of this License. (Exception: if the Program itself is
        interactive but does not normally print such an announcement,
        your work based on the Program is not required to print an
        announcement.)

    These requirements apply to the modified work as a whole. If
    identifiable sections of that work are not derived from the Program,
    and can be reasonably considered independent and separate works in
    themselves, then this License, and its terms, do not apply to those
    sections when you distribute them as separate works. But when you
    distribute the same sections as part of a whole which is a work
    based on the Program, the distribution of the whole must be on the
    terms of this License, whose permissions for other licensees extend
    to the entire whole, and thus to each and every part regardless of
    who wrote it.

    Thus, it is not the intent of this section to claim rights or
    contest your rights to work written entirely by you; rather, the
    intent is to exercise the right to control the distribution of
    derivative or collective works based on the Program.

    In addition, mere aggregation of another work not based on the
    Program with the Program (or with a work based on the Program) on a
    volume of a storage or distribution medium does not bring the other
    work under the scope of this License.

4.  You may copy and distribute the Program (or a work based on it,
    under Section 2) in object code or executable form under the terms
    of Sections 1 and 2 above provided that you also do one of the
    following:

    1.  Accompany it with the complete corresponding machine-readable
        source code, which must be distributed under the terms of
        Sections 1 and 2 above on a medium customarily used for software
        interchange; or,

    2.  Accompany it with a written offer, valid for at least three
        years, to give any third party, for a charge no more than your
        cost of physically performing source distribution, a complete
        machine-readable copy of the corresponding source code, to be
        distributed under the terms of Sections 1 and 2 above on a
        medium customarily used for software interchange; or,

    3.  Accompany it with the information you received as to the offer
        to distribute corresponding source code. (This alternative is
        allowed only for noncommercial distribution and only if you
        received the program in object code or executable form with such
        an offer, in accord with Subsection b above.)

    The source code for a work means the preferred form of the work for
    making modifications to it. For an executable work, complete source
    code means all the source code for all modules it contains, plus any
    associated interface definition files, plus the scripts used to
    control compilation and installation of the executable. However, as
    a special exception, the source code distributed need not include
    anything that is normally distributed (in either source or binary
    form) with the major components (compiler, kernel, and so on) of the
    operating system on which the executable runs, unless that component
    itself accompanies the executable.

    If distribution of executable or object code is made by offering
    access to copy from a designated place, then offering equivalent
    access to copy the source code from the same place counts as
    distribution of the source code, even though third parties are not
    compelled to copy the source along with the object code.

5.  You may not copy, modify, sublicense, or distribute the Program
    except as expressly provided under this License. Any attempt
    otherwise to copy, modify, sublicense or distribute the Program is
    void, and will automatically terminate your rights under this
    License. However, parties who have received copies, or rights, from
    you under this License will not have their licenses terminated so
    long as such parties remain in full compliance.

6.  You are not required to accept this License, since you have not
    signed it. However, nothing else grants you permission to modify or
    distribute the Program or its derivative works. These actions are
    prohibited by law if you do not accept this License. Therefore, by
    modifying or distributing the Program (or any work based on the
    Program), you indicate your acceptance of this License to do so, and
    all its terms and conditions for copying, distributing or modifying
    the Program or works based on it.

7.  Each time you redistribute the Program (or any work based on the
    Program), the recipient automatically receives a license from the
    original licensor to copy, distribute or modify the Program subject
    to these terms and conditions. You may not impose any further
    restrictions on the recipients’ exercise of the rights granted
    herein. You are not responsible for enforcing compliance by third
    parties to this License.

8.  If, as a consequence of a court judgment or allegation of patent
    infringement or for any other reason (not limited to patent issues),
    conditions are imposed on you (whether by court order, agreement or
    otherwise) that contradict the conditions of this License, they do
    not excuse you from the conditions of this License. If you cannot
    distribute so as to satisfy simultaneously your obligations under
    this License and any other pertinent obligations, then as a
    consequence you may not distribute the Program at all. For example,
    if a patent license would not permit royalty-free redistribution of
    the Program by all those who receive copies directly or indirectly
    through you, then the only way you could satisfy both it and this
    License would be to refrain entirely from distribution of the
    Program.

    If any portion of this section is held invalid or unenforceable
    under any particular circumstance, the balance of the section is
    intended to apply and the section as a whole is intended to apply in
    other circumstances.

    It is not the purpose of this section to induce you to infringe any
    patents or other property right claims or to contest validity of any
    such claims; this section has the sole purpose of protecting the
    integrity of the free software distribution system, which is
    implemented by public license practices. Many people have made
    generous contributions to the wide range of software distributed
    through that system in reliance on consistent application of that
    system; it is up to the author/donor to decide if he or she is
    willing to distribute software through any other system and a
    licensee cannot impose that choice.

    This section is intended to make thoroughly clear what is believed
    to be a consequence of the rest of this License.

9.  If the distribution and/or use of the Program is restricted in
    certain countries either by patents or by copyrighted interfaces,
    the original copyright holder who places the Program under this
    License may add an explicit geographical distribution limitation
    excluding those countries, so that distribution is permitted only in
    or among countries not thus excluded. In such case, this License
    incorporates the limitation as if written in the body of this
    License.

10. The Free Software Foundation may publish revised and/or new versions
    of the General Public License from time to time. Such new versions
    will be similar in spirit to the present version, but may differ in
    detail to address new problems or concerns.

    Each version is given a distinguishing version number. If the
    Program specifies a version number of this License which applies to
    it and “any later version”, you have the option of following the
    terms and conditions either of that version or of any later version
    published by the Free Software Foundation. If the Program does not
    specify a version number of this License, you may choose any version
    ever published by the Free Software Foundation.

11. If you wish to incorporate parts of the Program into other free
    programs whose distribution conditions are different, write to the
    author to ask for permission. For software which is copyrighted by
    the Free Software Foundation, write to the Free Software Foundation;
    we sometimes make exceptions for this. Our decision will be guided
    by the two goals of preserving the free status of all derivatives of
    our free software and of promoting the sharing and reuse of software
    generally.

12. BECAUSE THE PROGRAM IS LICENSED FREE OF CHARGE, THERE IS NO WARRANTY
    FOR THE PROGRAM, TO THE EXTENT PERMITTED BY APPLICABLE LAW. EXCEPT
    WHEN OTHERWISE STATED IN WRITING THE COPYRIGHT HOLDERS AND/OR OTHER
    PARTIES PROVIDE THE PROGRAM “AS IS” WITHOUT WARRANTY OF ANY KIND,
    EITHER EXPRESSED OR IMPLIED, INCLUDING, BUT NOT LIMITED TO, THE
    IMPLIED WARRANTIES OF MERCHANTABILITY AND FITNESS FOR A PARTICULAR
    PURPOSE. THE ENTIRE RISK AS TO THE QUALITY AND PERFORMANCE OF THE
    PROGRAM IS WITH YOU. SHOULD THE PROGRAM PROVE DEFECTIVE, YOU ASSUME
    THE COST OF ALL NECESSARY SERVICING, REPAIR OR CORRECTION.

13. IN NO EVENT UNLESS REQUIRED BY APPLICABLE LAW OR AGREED TO IN
    WRITING WILL ANY COPYRIGHT HOLDER, OR ANY OTHER PARTY WHO MAY MODIFY
    AND/OR REDISTRIBUTE THE PROGRAM AS PERMITTED ABOVE, BE LIABLE TO YOU
    FOR DAMAGES, INCLUDING ANY GENERAL, SPECIAL, INCIDENTAL OR
    CONSEQUENTIAL DAMAGES ARISING OUT OF THE USE OR INABILITY TO USE THE
    PROGRAM (INCLUDING BUT NOT LIMITED TO LOSS OF DATA OR DATA BEING
    RENDERED INACCURATE OR LOSSES SUSTAINED BY YOU OR THIRD PARTIES OR A
    FAILURE OF THE PROGRAM TO OPERATE WITH ANY OTHER PROGRAMS), EVEN IF
    SUCH HOLDER OR OTHER PARTY HAS BEEN ADVISED OF THE POSSIBILITY OF
    SUCH DAMAGES.

**Appendix: How to Apply These Terms to Your New Programs**

If you develop a new program, and you want it to be of the greatest
possible use to the public, the best way to achieve this is to make it
free software which everyone can redistribute and change under these
terms.

To do so, attach the following notices to the program. It is safest to
attach them to the start of each source file to most effectively convey
the exclusion of warranty; and each file should have at least the
“copyright” line and a pointer to where the full notice is found.

    one line to give the program's name and a brief idea of what it does.
    Copyright (C) yyyy  name of author

    This program is free software; you can redistribute it and/or modify
    it under the terms of the GNU General Public License as published by
    the Free Software Foundation; either version 2 of the License, or
    (at your option) any later version.

    This program is distributed in the hope that it will be useful,
    but WITHOUT ANY WARRANTY; without even the implied warranty of
    MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
    GNU General Public License for more details.

    You should have received a copy of the GNU General Public License
    along with this program; if not, write to the Free Software
    Foundation, Inc., 51 Franklin Street, Fifth Floor, Boston, MA  02110-1301, USA.

Also add information on how to contact you by electronic and paper mail.

If the program is interactive, make it output a short notice like this
when it starts in an interactive mode:

    Gnomovision version 69, Copyright (C) year name of author
    Gnomovision comes with ABSOLUTELY NO WARRANTY; for details type `show w'.
    This is free software, and you are welcome to redistribute it
    under certain conditions; type `show c' for details.

The hypothetical commands ‘`show w`’ and ‘`show c`’ should show the
appropriate parts of the General Public License. Of course, the commands
you use may be called something other than ‘`show w`’ and ‘`show c`’;
they could even be mouse-clicks or menu items—whatever suits your
program.

You should also get your employer (if you work as a programmer) or your
school, if any, to sign a “copyright disclaimer” for the program, if
necessary. Here is a sample; alter the names:

    Yoyodyne, Inc., hereby disclaims all copyright interest in the program
    `Gnomovision' (which makes passes at compilers) written by James Hacker.

    signature of Ty Coon, 1 April 1989
    Ty Coon, President of Vice

This General Public License does not permit incorporating your program
into proprietary programs. If your program is a subroutine library, you
may consider it more useful to permit linking proprietary applications
with the library. If this is what you want to do, use the GNU Lesser
General Public License instead of this License.

GNU Free Documentation License
==============================

Version 1.3, 3 November 2008
    Copyright © 2000, 2001, 2002, 2007, 2008 Free Software Foundation, Inc.
    http://fsf.org/

    Everyone is permitted to copy and distribute verbatim copies
    of this license document, but changing it is not allowed.

1.  PREAMBLE

    The purpose of this License is to make a manual, textbook, or other
    functional and useful document free in the sense of freedom: to
    assure everyone the effective freedom to copy and redistribute it,
    with or without modifying it, either commercially or
    noncommercially. Secondarily, this License preserves for the author
    and publisher a way to get credit for their work, while not being
    considered responsible for modifications made by others.

    This License is a kind of “copyleft”, which means that derivative
    works of the document must themselves be free in the same sense. It
    complements the GNU General Public License, which is a copyleft
    license designed for free software.

    We have designed this License in order to use it for manuals for
    free software, because free software needs free documentation: a
    free program should come with manuals providing the same freedoms
    that the software does. But this License is not limited to software
    manuals; it can be used for any textual work, regardless of subject
    matter or whether it is published as a printed book. We recommend
    this License principally for works whose purpose is instruction or
    reference.

2.  APPLICABILITY AND DEFINITIONS

    This License applies to any manual or other work, in any medium,
    that contains a notice placed by the copyright holder saying it can
    be distributed under the terms of this License. Such a notice grants
    a world-wide, royalty-free license, unlimited in duration, to use
    that work under the conditions stated herein. The “Document”, below,
    refers to any such manual or work. Any member of the public is a
    licensee, and is addressed as “you”. You accept the license if you
    copy, modify or distribute the work in a way requiring permission
    under copyright law.

    A “Modified Version” of the Document means any work containing the
    Document or a portion of it, either copied verbatim, or with
    modifications and/or translated into another language.

    A “Secondary Section” is a named appendix or a front-matter section
    of the Document that deals exclusively with the relationship of the
    publishers or authors of the Document to the Document’s overall
    subject (or to related matters) and contains nothing that could fall
    directly within that overall subject. (Thus, if the Document is in
    part a textbook of mathematics, a Secondary Section may not explain
    any mathematics.) The relationship could be a matter of historical
    connection with the subject or with related matters, or of legal,
    commercial, philosophical, ethical or political position regarding
    them.

    The “Invariant Sections” are certain Secondary Sections whose titles
    are designated, as being those of Invariant Sections, in the notice
    that says that the Document is released under this License. If a
    section does not fit the above definition of Secondary then it is
    not allowed to be designated as Invariant. The Document may contain
    zero Invariant Sections. If the Document does not identify any
    Invariant Sections then there are none.

    The “Cover Texts” are certain short passages of text that are
    listed, as Front-Cover Texts or Back-Cover Texts, in the notice that
    says that the Document is released under this License. A Front-Cover
    Text may be at most 5 words, and a Back-Cover Text may be at most 25
    words.

    A “Transparent” copy of the Document means a machine-readable copy,
    represented in a format whose specification is available to the
    general public, that is suitable for revising the document
    straightforwardly with generic text editors or (for images composed
    of pixels) generic paint programs or (for drawings) some widely
    available drawing editor, and that is suitable for input to text
    formatters or for automatic translation to a variety of formats
    suitable for input to text formatters. A copy made in an otherwise
    Transparent file format whose markup, or absence of markup, has been
    arranged to thwart or discourage subsequent modification by readers
    is not Transparent. An image format is not Transparent if used for
    any substantial amount of text. A copy that is not “Transparent” is
    called “Opaque”.

    Examples of suitable formats for Transparent copies include plain
    ASCII without markup, Texinfo input format, LaTEX input format, SGML
    or XML using a publicly available DTD, and standard-conforming
    simple HTML, PostScript or PDF designed for human modification.
    Examples of transparent image formats include PNG, XCF and JPG.
    Opaque formats include proprietary formats that can be read and
    edited only by proprietary word processors, SGML or XML for which
    the DTD and/or processing tools are not generally available, and the
    machine-generated HTML, PostScript or PDF produced by some word
    processors for output purposes only.

    The “Title Page” means, for a printed book, the title page itself,
    plus such following pages as are needed to hold, legibly, the
    material this License requires to appear in the title page. For
    works in formats which do not have any title page as such, “Title
    Page” means the text near the most prominent appearance of the
    work’s title, preceding the beginning of the body of the text.

    The “publisher” means any person or entity that distributes copies
    of the Document to the public.

    A section “Entitled XYZ” means a named subunit of the Document whose
    title either is precisely XYZ or contains XYZ in parentheses
    following text that translates XYZ in another language. (Here XYZ
    stands for a specific section name mentioned below, such as
    “Acknowledgements”, “Dedications”, “Endorsements”, or “History”.) To
    “Preserve the Title” of such a section when you modify the Document
    means that it remains a section “Entitled XYZ” according to this
    definition.

    The Document may include Warranty Disclaimers next to the notice
    which states that this License applies to the Document. These
    Warranty Disclaimers are considered to be included by reference in
    this License, but only as regards disclaiming warranties: any other
    implication that these Warranty Disclaimers may have is void and has
    no effect on the meaning of this License.

3.  VERBATIM COPYING

    You may copy and distribute the Document in any medium, either
    commercially or noncommercially, provided that this License, the
    copyright notices, and the license notice saying this License
    applies to the Document are reproduced in all copies, and that you
    add no other conditions whatsoever to those of this License. You may
    not use technical measures to obstruct or control the reading or
    further copying of the copies you make or distribute. However, you
    may accept compensation in exchange for copies. If you distribute a
    large enough number of copies you must also follow the conditions in
    section 3.

    You may also lend copies, under the same conditions stated above,
    and you may publicly display copies.

4.  COPYING IN QUANTITY

    If you publish printed copies (or copies in media that commonly have
    printed covers) of the Document, numbering more than 100, and the
    Document’s license notice requires Cover Texts, you must enclose the
    copies in covers that carry, clearly and legibly, all these Cover
    Texts: Front-Cover Texts on the front cover, and Back-Cover Texts on
    the back cover. Both covers must also clearly and legibly identify
    you as the publisher of these copies. The front cover must present
    the full title with all words of the title equally prominent and
    visible. You may add other material on the covers in addition.
    Copying with changes limited to the covers, as long as they preserve
    the title of the Document and satisfy these conditions, can be
    treated as verbatim copying in other respects.

    If the required texts for either cover are too voluminous to fit
    legibly, you should put the first ones listed (as many as fit
    reasonably) on the actual cover, and continue the rest onto adjacent
    pages.

    If you publish or distribute Opaque copies of the Document numbering
    more than 100, you must either include a machine-readable
    Transparent copy along with each Opaque copy, or state in or with
    each Opaque copy a computer-network location from which the general
    network-using public has access to download using public-standard
    network protocols a complete Transparent copy of the Document, free
    of added material. If you use the latter option, you must take
    reasonably prudent steps, when you begin distribution of Opaque
    copies in quantity, to ensure that this Transparent copy will remain
    thus accessible at the stated location until at least one year after
    the last time you distribute an Opaque copy (directly or through
    your agents or retailers) of that edition to the public.

    It is requested, but not required, that you contact the authors of
    the Document well before redistributing any large number of copies,
    to give them a chance to provide you with an updated version of the
    Document.

5.  MODIFICATIONS

    You may copy and distribute a Modified Version of the Document under
    the conditions of sections 2 and 3 above, provided that you release
    the Modified Version under precisely this License, with the Modified
    Version filling the role of the Document, thus licensing
    distribution and modification of the Modified Version to whoever
    possesses a copy of it. In addition, you must do these things in the
    Modified Version:

    1.  Use in the Title Page (and on the covers, if any) a title
        distinct from that of the Document, and from those of previous
        versions (which should, if there were any, be listed in the
        History section of the Document). You may use the same title as
        a previous version if the original publisher of that version
        gives permission.

    2.  List on the Title Page, as authors, one or more persons or
        entities responsible for authorship of the modifications in the
        Modified Version, together with at least five of the principal
        authors of the Document (all of its principal authors, if it has
        fewer than five), unless they release you from this requirement.

    3.  State on the Title page the name of the publisher of the
        Modified Version, as the publisher.

    4.  Preserve all the copyright notices of the Document.

    5.  Add an appropriate copyright notice for your modifications
        adjacent to the other copyright notices.

    6.  Include, immediately after the copyright notices, a license
        notice giving the public permission to use the Modified Version
        under the terms of this License, in the form shown in the
        Addendum below.

    7.  Preserve in that license notice the full lists of Invariant
        Sections and required Cover Texts given in the Document’s
        license notice.

    8.  Include an unaltered copy of this License.

    9.  Preserve the section Entitled “History”, Preserve its Title, and
        add to it an item stating at least the title, year, new authors,
        and publisher of the Modified Version as given on the Title
        Page. If there is no section Entitled “History” in the Document,
        create one stating the title, year, authors, and publisher of
        the Document as given on its Title Page, then add an item
        describing the Modified Version as stated in the previous
        sentence.

    10. Preserve the network location, if any, given in the Document for
        public access to a Transparent copy of the Document, and
        likewise the network locations given in the Document for
        previous versions it was based on. These may be placed in the
        “History” section. You may omit a network location for a work
        that was published at least four years before the Document
        itself, or if the original publisher of the version it refers to
        gives permission.

    11. For any section Entitled “Acknowledgements” or “Dedications”,
        Preserve the Title of the section, and preserve in the section
        all the substance and tone of each of the contributor
        acknowledgements and/or dedications given therein.

    12. Preserve all the Invariant Sections of the Document, unaltered
        in their text and in their titles. Section numbers or the
        equivalent are not considered part of the section titles.

    13. Delete any section Entitled “Endorsements”. Such a section may
        not be included in the Modified Version.

    14. Do not retitle any existing section to be Entitled
        “Endorsements” or to conflict in title with any Invariant
        Section.

    15. Preserve any Warranty Disclaimers.

    If the Modified Version includes new front-matter sections or
    appendices that qualify as Secondary Sections and contain no
    material copied from the Document, you may at your option designate
    some or all of these sections as invariant. To do this, add their
    titles to the list of Invariant Sections in the Modified Version’s
    license notice. These titles must be distinct from any other section
    titles.

    You may add a section Entitled “Endorsements”, provided it contains
    nothing but endorsements of your Modified Version by various
    parties—for example, statements of peer review or that the text has
    been approved by an organization as the authoritative definition of
    a standard.

    You may add a passage of up to five words as a Front-Cover Text, and
    a passage of up to 25 words as a Back-Cover Text, to the end of the
    list of Cover Texts in the Modified Version. Only one passage of
    Front-Cover Text and one of Back-Cover Text may be added by (or
    through arrangements made by) any one entity. If the Document
    already includes a cover text for the same cover, previously added
    by you or by arrangement made by the same entity you are acting on
    behalf of, you may not add another; but you may replace the old one,
    on explicit permission from the previous publisher that added the
    old one.

    The author(s) and publisher(s) of the Document do not by this
    License give permission to use their names for publicity for or to
    assert or imply endorsement of any Modified Version.

6.  COMBINING DOCUMENTS

    You may combine the Document with other documents released under
    this License, under the terms defined in section 4 above for
    modified versions, provided that you include in the combination all
    of the Invariant Sections of all of the original documents,
    unmodified, and list them all as Invariant Sections of your combined
    work in its license notice, and that you preserve all their Warranty
    Disclaimers.

    The combined work need only contain one copy of this License, and
    multiple identical Invariant Sections may be replaced with a single
    copy. If there are multiple Invariant Sections with the same name
    but different contents, make the title of each such section unique
    by adding at the end of it, in parentheses, the name of the original
    author or publisher of that section if known, or else a unique
    number. Make the same adjustment to the section titles in the list
    of Invariant Sections in the license notice of the combined work.

    In the combination, you must combine any sections Entitled “History”
    in the various original documents, forming one section Entitled
    “History”; likewise combine any sections Entitled
    “Acknowledgements”, and any sections Entitled “Dedications”. You
    must delete all sections Entitled “Endorsements.”

7.  COLLECTIONS OF DOCUMENTS

    You may make a collection consisting of the Document and other
    documents released under this License, and replace the individual
    copies of this License in the various documents with a single copy
    that is included in the collection, provided that you follow the
    rules of this License for verbatim copying of each of the documents
    in all other respects.

    You may extract a single document from such a collection, and
    distribute it individually under this License, provided you insert a
    copy of this License into the extracted document, and follow this
    License in all other respects regarding verbatim copying of that
    document.

8.  AGGREGATION WITH INDEPENDENT WORKS

    A compilation of the Document or its derivatives with other separate
    and independent documents or works, in or on a volume of a storage
    or distribution medium, is called an “aggregate” if the copyright
    resulting from the compilation is not used to limit the legal rights
    of the compilation’s users beyond what the individual works permit.
    When the Document is included in an aggregate, this License does not
    apply to the other works in the aggregate which are not themselves
    derivative works of the Document.

    If the Cover Text requirement of section 3 is applicable to these
    copies of the Document, then if the Document is less than one half
    of the entire aggregate, the Document’s Cover Texts may be placed on
    covers that bracket the Document within the aggregate, or the
    electronic equivalent of covers if the Document is in electronic
    form. Otherwise they must appear on printed covers that bracket the
    whole aggregate.

9.  TRANSLATION

    Translation is considered a kind of modification, so you may
    distribute translations of the Document under the terms of section
    4. Replacing Invariant Sections with translations requires special
    permission from their copyright holders, but you may include
    translations of some or all Invariant Sections in addition to the
    original versions of these Invariant Sections. You may include a
    translation of this License, and all the license notices in the
    Document, and any Warranty Disclaimers, provided that you also
    include the original English version of this License and the
    original versions of those notices and disclaimers. In case of a
    disagreement between the translation and the original version of
    this License or a notice or disclaimer, the original version will
    prevail.

    If a section in the Document is Entitled “Acknowledgements”,
    “Dedications”, or “History”, the requirement (section 4) to Preserve
    its Title (section 1) will typically require changing the actual
    title.

10. TERMINATION

    You may not copy, modify, sublicense, or distribute the Document
    except as expressly provided under this License. Any attempt
    otherwise to copy, modify, sublicense, or distribute it is void, and
    will automatically terminate your rights under this License.

    However, if you cease all violation of this License, then your
    license from a particular copyright holder is reinstated (a)
    provisionally, unless and until the copyright holder explicitly and
    finally terminates your license, and (b) permanently, if the
    copyright holder fails to notify you of the violation by some
    reasonable means prior to 60 days after the cessation.

    Moreover, your license from a particular copyright holder is
    reinstated permanently if the copyright holder notifies you of the
    violation by some reasonable means, this is the first time you have
    received notice of violation of this License (for any work) from
    that copyright holder, and you cure the violation prior to 30 days
    after your receipt of the notice.

    Termination of your rights under this section does not terminate the
    licenses of parties who have received copies or rights from you
    under this License. If your rights have been terminated and not
    permanently reinstated, receipt of a copy of some or all of the same
    material does not give you any rights to use it.

11. FUTURE REVISIONS OF THIS LICENSE

    The Free Software Foundation may publish new, revised versions of
    the GNU Free Documentation License from time to time. Such new
    versions will be similar in spirit to the present version, but may
    differ in detail to address new problems or concerns. See
    <http://www.gnu.org/copyleft/>.

    Each version of the License is given a distinguishing version
    number. If the Document specifies that a particular numbered version
    of this License “or any later version” applies to it, you have the
    option of following the terms and conditions either of that
    specified version or of any later version that has been published
    (not as a draft) by the Free Software Foundation. If the Document
    does not specify a version number of this License, you may choose
    any version ever published (not as a draft) by the Free Software
    Foundation. If the Document specifies that a proxy can decide which
    future versions of this License can be used, that proxy’s public
    statement of acceptance of a version permanently authorizes you to
    choose that version for the Document.

12. RELICENSING

    “Massive Multiauthor Collaboration Site” (or “MMC Site”) means any
    World Wide Web server that publishes copyrightable works and also
    provides prominent facilities for anybody to edit those works. A
    public wiki that anybody can edit is an example of such a server. A
    “Massive Multiauthor Collaboration” (or “MMC”) contained in the site
    means any set of copyrightable works thus published on the MMC site.

    “CC-BY-SA” means the Creative Commons Attribution-Share Alike 3.0
    license published by Creative Commons Corporation, a not-for-profit
    corporation with a principal place of business in San Francisco,
    California, as well as future copyleft versions of that license
    published by that same organization.

    “Incorporate” means to publish or republish a Document, in whole or
    in part, as part of another Document.

    An MMC is “eligible for relicensing” if it is licensed under this
    License, and if all works that were first published under this
    License somewhere other than this MMC, and subsequently incorporated
    in whole or in part into the MMC, (1) had no cover texts or
    invariant sections, and (2) were thus incorporated prior to November
    1, 2008.

    The operator of an MMC Site may republish an MMC contained in the
    site under CC-BY-SA on the same site at any time before August 1,
    2009, provided the MMC is eligible for relicensing.

**ADDENDUM: How to use this License for your documents**

To use this License in a document you have written, include a copy of
the License in the document and put the following copyright and license
notices just after the title page:

      Copyright (C)  year  your name.
      Permission is granted to copy, distribute and/or modify this document
      under the terms of the GNU Free Documentation License, Version 1.3
      or any later version published by the Free Software Foundation;
      with no Invariant Sections, no Front-Cover Texts, and no Back-Cover
      Texts.  A copy of the license is included in the section entitled ``GNU
      Free Documentation License''.

If you have Invariant Sections, Front-Cover Texts and Back-Cover Texts,
replace the “with…Texts.” line with this:

        with the Invariant Sections being list their titles, with
        the Front-Cover Texts being list, and with the Back-Cover Texts
        being list.

If you have Invariant Sections without Cover Texts, or some other
combination of the three, merge those two alternatives to suit the
situation.

If your document contains nontrivial examples of program code, we
recommend releasing these examples in parallel under your choice of free
software license, such as the GNU General Public License, to permit
their use in free software.

Functions & Variables
=====================

Keys and Concepts
=================
