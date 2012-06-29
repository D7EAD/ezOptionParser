Overview
--------
[ezOptionParser](http://sourceforge.net/projects/ezoptionparser/) is another command-line parser class for C++ that has features not available in alternative solutions (getopt, boost, argtable, argstream, gflags) and doesn't require a steep learning curve.

Download
--------
[Source Code and Examples](http://sourceforge.net/projects/ezoptionparser/files/)

[ezOptionParser.hpp](ezOptionParser.hpp)

Features
--------
-   Pretty printing of parsed inputs for debugging.
-   Auto usage message creation in three layouts (aligned, interleaved or staggered).
-   Single header file implementation.
-   Dependent only on STL.
-   Arbitrary short and long option names (dash '-' or plus '+' prefixes not required).
-   Arbitrary argument list delimiters.
-   Multiple flag instances allowed.
-   Validation of required options, number of expected arguments per flag, datatype ranges, user defined ranges, membership in lists and case for string lists.
-   Validation criteria definable by strings or constants.
-   Multiple file import with comments.
-   Exports to file, either set options or all options including defaults when available. 
-   MIT license.
-   Minimal learning curve due to many examples.
-   Automated regression and memory tests with valgrind.

Examples
--------
[complete.cpp](complete.html)
A complete example that could be used as a starting point for your own C++ program.

[fileio.cpp](fileio.html)
Shows how to import and export options with files (that can contain comments!).

[full.cpp](full.html)
A full test of all the features. Meant for testing, but can be a source of ideas for what's possible.

[long.cpp](long.html)
Demo of using long flag names.

[multi.cpp](multi.html)
Shows how to handle multiple instances of a flag.

[pretty.cpp](pretty.html)
Demo of pretty printing everything parsed, which can help in debugging.

[short.cpp](short.html)
Short demo of a short flag name.

[usage.cpp](usage.html)
Demo of automatic usage message creation in three builtin layouts.
Here are how the three layouts appear:
[aligned](aligned.html), [interleaved](interleaved.html), [staggered](staggered.html)

[valid.cpp](valid.html)
Demo of using validators defined by strings, which only check if values are within for their datatype limits.

[validrange.cpp](validrange.html)
Demo of using validators with value ranges and lists defined by strings.

[validfast.cpp](validfast.html)
Demo of using validators defined by constants for more efficient execution. These validators only check if values are within for their datatype limits..

[validrangefast.cpp](validrangefast.html)
Demo of using validators with value ranges and lists defined by constants for more efficient execution.

Usage
-----
Copy or include ezOptionParser.hpp to your project and use the "ez" namespace, as shown here:

   #include <stdio.h>
   #include "ezOptionParser.hpp"

   int main(int argc, const char * argv[]) {
      ez::ezOptionParser opt;

      opt.overview = "Demo of pretty printing everything parsed for debugging.";
      opt.syntax = "pretty [OPTIONS]";
      opt.example = "pretty foo bar --print -fake --dummy -list 1:2:16 in1 in2 in3 out\n";

      opt.add(
         "", // Default.
         0, // Required?
         0, // Number of args expected.
         0, // Delimiter if expecting multiple args.
         "Print all inputs and their category.", // Help description.
         "-p",     // Flag token. 
         "-prn",   // Flag token.
         "--print" // Flag token.
      );

      opt.parse(argc, argv);

      if (opt.isSet("-p")) {
         std::string pretty;
         opt.prettyPrint(pretty);
         std::cout << pretty;
      }

      return 0;
   }

Testing
-------
    make
    make memtest
    make clean

Installation
------------
    sudo make install PREFIX=/usr/local

Distribution
------------
    make html
    make clean
    make dist VER=0.1.4

Publishing
----------
    ssh -t rsz,ezoptionparser@shell.sourceforge.net create 
    scp html/* ezOptionParser.hpp rsz,ezoptionparser@shell.sourceforge.net:/home/project-web/ezoptionparser/htdocs
    scp ../ezOptionParser-0.1.4.tar.gz rsz,ezoptionparser@shell.sourceforge.net:/home/frs/project/e/ez/ezoptionparser

Changelog
---------
v0.1.4 (20120629)

-   Fixed file licenses to MIT.

v0.1.3 (20120603)

-   Changed license to MIT.
-   Reformatted readme to markdown.
-   Updated make dist target to be git friendly.

v0.1.2 (20111126)

-   Published.

v0.1.1 (20111011)

-   Published.

v0.1.0 (20111011)

-   Published.

v0.0.0 (20110511)

-   Published.

License
-------
Copyright 2011, 2012 Remik Ziemlinski (see MIT-LICENSE)
