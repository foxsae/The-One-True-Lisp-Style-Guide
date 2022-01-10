# The One True Lisp Style Guide 
##### (aka The lowest Common Lisp denominator)

## Purpose: To create a subset of style recommendations for Common Lisp based upon the points of agreement found in other style guides.

### Note: Despite the "tongue in cheek" title this is not actually a serious attempt to create yet another Lisp programming style guide, rather it is an attempt to find agreement among a number of different Lisp style guides and then reduce them to one line injunctions, purely for my own interests. However, if this itself does turn into a generally accepted simplified Lisp style guide then I will try not to be too disappointed with that result. 

![I honestly didn't think you could even USE emoji in variable names. Or that there were so many different crying ones.](https://imgs.xkcd.com/comics/code_quality.png)

## Sources

(PNKP) [Tutorial on Good Lisp Programming Style by Peter Norvig and Kent Pitman](https://courses.cs.northwestern.edu/325/readings/luv-slides.pdf) (pdf)

(LLSG) [The lisp-lang.org style guide](https://lisp-lang.org/style-guide/) (www)

(GCLS) [The Google Common Lisp style guide](https://google.github.io/styleguide/lispguide.xml) (www)

(ALCL) [The Ariel Labs Common Lisp style guide](http://labs.ariel-networks.com/cl-style-guide.html) (www)

(LPCM) [Lisp programming style from Carnegie Mellon University Lisp Group](https://www.cs.cmu.edu/Groups/AI/html/faqs/lang/lisp/part1/faq-doc-4.html) (www)

(CLHS) [Common Lisp Hyper Spec](http://www.lispworks.com/documentation/lw60/CLHS/Front/index.htm)

(CLtL) [Common Lisp the Language - Steele](https://www.cs.cmu.edu/Groups/AI/html/cltl/clm/clm.html)

## RESULTS SO FAR...

#### These results are a work in progress. I will accept changes to them if you can show points where there is general agreement between any two or more of the guides from the Sources. If you know of an important Common Lisp style guide that should be included in the Sources please let me know. 

### 1. Documentation
  * **Consensus:** Docstrings are very important. Docstrings are more important than comments. 
### 2. Comment Conventions
  * **Consensus:** (1) ; in-line comment. (2) ;; top-level form/function comment. (3) ;;; in-between forms/functions/regions comment. (4) ;;;; header comment.
### 3. Line Length
  * **Consensus:**: Limit the line length, less than 100, but shorter is better.
### 4. Naming Conventions
  * **Consensus:** Names should be complete words, brief, lowercase, separated by "-". Use notations for \*specials\* and \+constants\+.
### 5. Defining Functions
  * **Consensus:**: Avoid having both \&OPTIONAL and \&KEY arguments if at all possible.
### 6. Special Variables
  * **Consensus:** Use special variables sparingly.
### 7. Indentation
  * **Consensus:** Use the indentation "standard" provided by a properly calibrated editor.
### 8. Functional Style
  * **Consensus:** Write single-purpose functions.
### 9. Eval Usage
  * **Consensus:** Eval is a red flag.
### 10. Macros
  * **Consensus:**: It is better to use a macro than to define one, but the best is to understand one.
### 11. Usage of :use
  * **Consensus:** Unless you truly need all the symbols, :import-from is better than :use.
  * **Note:** Package-local nicknames are now available on all major implementations, and are considered best practice.
### 12. Error Detection: Understanding conditions vs errors
  * **Consensus:** All errors are conditions; not all conditions are errors.
### 13. Library Usage
  * **Consensus:** It's well spoken of. 
### 14. Recursion
  * **Consensus:**  Favor iteration over recursion. Recursion is good for recursive data structures.
### 15. Type Checking
  * **Consensus:** If you know the type, you should make it explicit. This may help the compiler and those who need to read your code.
### 16. Conditional Expressions
  * **Consensus:** Rather than using an "if" without an "else" it is better to use either "when" or "unless". Use "cond" for multi-brach statements.
### 17. Predicates
  * **Consensus:** Predicates should be suffixed with "p" or "-p" depending on if the word has hyphens in it already, and return "t" or "nil".

# LONG FORM EXPLANATIONS FROM SOURCES

## 1. DOCUMENTATION

## Consensus: Docstrings are very important. Docstrings are more important than comments. 

(LPCM)
 * If it isn't clear from the name of a function or variable what its purpose is, document it with a documentation string and a comment. 
 * In fact, even if the purpose is evident from the name, it is still worth documenting your code.
 * Include documentation strings in your code. This lets users get help while running your program without having to resort to the source code or printed documentation. 


(PNKP)
* Documentation strings are better than comments.
* Say what it is for, not just what it does.
* If you're thinking of something useful that others might want to know when they read your code and that might not be instantly apparent to them make it a comment.
* Documentation should be organized around tasks the user needs to do, not around what your program happens to provide. Adding aocumentation strings to eacdh function usually doesn't tell the reader how to use your program, but hints in the right place can be bery effective.

(ALCL)
* All comments are optional. Usually, comments are for writer of the program and it is you in most of the times. If you think that it should be known by users, it must be included in docstring, not comment.
* Comments should end with period
* Docstring is always needed for every parts. Don't forget Packages and ASDF Systems.
* You can omit only if it is obvious what to do.

(GCLS)
 * Document everything.
 * You should use document strings on all visible functions to explain how to use your code.
 * Unless some bit of code is painfully self-explanatory, document it with a documentation string (also known as docstring).
 
 (LLSG)
 * Docstrings everywhere.
 * Common Lisp allows you to add docstrings to functions, packages, classes and individual slots, and you should use this.


## 2. COMMENT CONVENTIONS

## Consensus: (1) ; in-line comment. (2) ;; top-level form/function comment. (3) ;;; in-between forms/functions/regions comment. (4) ;;;; header comment.

(LPCM)
* Comment your code. Use three semicolons in the left margin before the definition for major explanations. Use two semicolons that float with the code to explain the routine that follows. Two semicolons may also be used to explain the following line when the comment is too long for the single semicolon treatment. Use a single semicolon to the right of the code to explain a particular line with a short comment. The number of semicolons used roughly corresponds with the length of the comment. Put at least one blank line before and after top-level expressions.

(PNKP)
* Obey comment conventions.
* ; for inline comment.
* ;; for in-function comment.
* ;;; for between-function comment.
* ;;;; for section header (for outline mode).

(GCLS)
* File headers and important comments that apply to large sections of code in a source file should begin with four semicolons.
* You should use three semicolons to begin comments that apply to just one top-level form or small group of top-level forms.
* Inside a top-level form, you should use two semicolons to begin a comment if it appears between lines.
* You should use one semicolon if it is a parenthetical remark and occurs at the end of a line. 
* You should use spaces to separate the comment from the code it refers to so the comment stands out. 
* You should try to vertically align consecutive related end-of-line comments.

(LLSG)
* Comments that start with four semicolons, ;;;;, should appear at the top of a file, explaining its purpose.
* Comments starting with three semicolons, ;;;, should be used to separate regions of the code.
* Comments with two semicolons, ;;, should describe regions of code within a function or some other top-level form. 
* Single-semicolon comments, ;, should just be short notes on a single line.

(CLHS)
* Comments that begin with a single semicolon are all aligned to the same column at the right (sometimes called the 'comment column'). The text of such a comment generally applies only to the line on which it appears.
* Comments that begin with a quadruple semicolon are all aligned to the left margin, and generally contain only a short piece of text that serve as a title for the code which follows, and might be used in the header or footer of a program that prepares code for presentation as a hardcopy document.

## 3. LINE LENGTH

## Consensus: Limit the line length, less than 100, but shorter is better.

(LPCM)
* Don't use line lengths greater than 80 characters.
* In fact, use a line length of 72 characters.

(GCLS)
* No more than 100 characters.

(LLSG)
* Lines should not exceed 100 columns.

(NPKP)
* 80-column maximum width.

## 4. NAMING CONVENTIONS

## Consensus: Names should be complete words, brief, lowercase, separated by "-". Use notations for \*specials\* and \+constants\+.

(LPCM)
* If you find yourself having trouble fitting everything in even with line breaking and relaxing the rules, either your function names are too long or your code isn't very modular. You should perceive this as a signal that you need to break up your big definitions into smaller chunks, each with a clearly defined purpose, and possibly replace long function names with concise but apt shorter ones.

(PNKP)
* Be consistent with capitalization most prefer like-this, not LikeThis.
* \*special-variable\*.
* \+constant\+.
* Minimize abbreviations.
* Most words have many possible abbreviations but only one correct spelling. Spell out names so they are easier to read, remember, and find.
* A good test (for a native English speaker) is: Would you say the word aloud in conversation?

(ALCL)
* Surround class name with \< and \>.
* Surround constants with \+.
* Surround special vars with \*.

(LLSG) 
* Names are lowercase, separated by single dashes (-), and they are complete words. That is, you should write user-count rather than user-cnt and make-text-node is better mk-txt-node.
* Special variables (Mutable globals) should be surrounded by asterisks. These are called earmuffs.
* Constants should be surrounded with plus signs.
  
(GCLS)
* You should use lower case. You should follow the rules for Spelling and Abbreviations You should follow punctuation conventions.
* Use lower case for all symbols. Consistently using lower case makes searching for symbol names easier and is more readable.
* The names of global constants should start and end with plus characters.
  
## 5. DEFINING FUNCTIONS

## Consensus: Avoid having both \&OPTIONAL and \&KEY arguments if at all possible.
  
(GCLS)
* You should avoid having both &OPTIONAL and &KEY arguments, unless it never makes sense to specify keyword arguments when the optional arguments are not all specified. You must not have non-NIL defaults to your &OPTIONAL arguments when your function has both &OPTIONAL and &KEY arguments
  
(PNKP)
* Don't mix &optional and &key.

## 6. SPECIAL VARIABLES

## Consensus: Use special variables sparingly.

(LPCM)
* In general, avoid unnecessary use of special variables.
* Although assignment statements can't always be avoided in production code, good programmers take advantage of Lisp's functional programming style before resorting to SETF and SETQ. For example, they will nest function calls instead of using a temporary variable and use the stack to pass multiple values. When first learning to program in Lisp, try to avoid SETF/SETQ and their cousins as much as possible. And if a temporary variable is necessary, bind it to its first value in a LET statement, instead of letting it become a global variable by default. (If you see lots of compiler warnings about declaring variables to be special, you're probably making this mistake. If you intend a variable to be global, it should be defined with a DEFVAR or DEFPARAMETER statement, not left to the compiler to fix.)

(GCLS)
* Use special variables sparingly.
* Using Lisp "special" (dynamically bound) variables as implicit arguments to functions should be used sparingly, and only in cases where it won't surprise the person reading the code, and where it offers significant benefits.

(PNKP)
* Watch out for global state like setq and property lists.
  
 ## 7. INDENTATION
 
 ## Consensus: Use the indentation "standard" provided by a properly calibrated editor.
 
(NPKP)
* Don't try to indent yourself. Instead let the editor do it. A near-standard form as evolved.

(LPCM)
* Indentation is two lines per form.
* There are, however, some exceptions. In the if special form, both branches must be on the same line.

(GCLS)
* Indent your code the way a properly configured GNU Emacs does.
* Maintain a consistent indentation style throughout a project.
* Indent carefully to make the code easier to understand.

(LPCM)
* Use proper indentation -- you should be able to understand the structure of your definitions without noticing the parentheses. 

## 8. FUNCTIONAL STYLE

## Consensus: Write single-purpose functions.

(LPCM)
* Write short functions, where each function provides a single, well-defined operation. Small functions are easier to read, write, test, debug, and understand.

(GCLS)
* You should avoid side-effects when they are not necessary.
* Avoid modifying local variables, try rebinding instead
* In the spirit of a mostly pure functional style, which makes testing and maintenance easier, we invite you to consider how to do things with the fewest assignments required.

(PNKP)
* Every function should have: A single specific purpose.

## 9. EVAL USAGE

## Consensus: Eval is a red flag.

(LPCM)
* EVAL. Novices almost always misuse EVAL. When experts use EVAL, they often would be better off using APPLY, FUNCALL, or SYMBOL-VALUE. Use of EVAL when defining a macro should set off a warning bell -- macro definitions are already evaluated during expansion. See also the answer to question 3-12. The general rule of thumb about EVAL is: if you think you need to use EVAL, you're probably wrong.

(PNKP)
* Some red flags: Any use of eval

(GCLS)
* You must not use EVAL at runtime.
* Places where it is actually appropriate to use EVAL are so few and far between that you must consult with your reviewers; it's easily misused.

## 10. MACROS

## Consensus: It is better to use a macro than to define one, but the best is to understand one.

(LPCM) 
* Never use a macro instead of a function for efficiency reasons.
* Don't define a macro where a function definition will work just as well -- remember, you can FUNCALL or MAPCAR a function but not a macro.
* Don't create a new iteration macro when an existing function or macro will do.

(ALCL)
* You know Macro is one of the strongest feature in Common Lisp. But it is also a dangerous thing. You should avoid using Macro if it is possible.
* This is a really important warning. If you feel it is needed once, you should think this well again. How do other languages manage it? They really manage the problems without macros.

(GCLS)
* Use macros when appropriate, which is often. Define macros when appropriate, which is seldom.

(PNKP)
* Some Red Flags: The absence of an &environment parameter in a macro that uses setf to call macroexpand.
* Avoid common mistakes: understand macros.
* Avoid common mistakes: recompile after changing macros or inline functions.
* You should be able to do the following: macroexpand any expression.

## 11. USAGE OF :USE

## Consensus: Unless you truly need all the symbols, :import-from is better than :use.
## Note: Package-local nicknames are now available on all major implementations, and are considered best practice.

(ALCL)
* Don't use :use unnecessarily. It is often hard to understand where a function came from. We recommend using :import-from for instead.
* We allow you to use :use only if most of symbols are needed or it is obvious.

(LLSG)
* Unless you are really going to need all (or most of) the symbols in a package, it is strongly recommended that you write a manual :import-from list as opposed to using :use.

## 12. ERROR DETECTION: UNDERSTANDING CONDITIONS VS ERRORS

## Consensus: All errors are conditions; not all conditions are errors.

(NPKP)
* Learn the difference between errors and conditions. All errors are conditions; not all conditions are errors.
* Strike a balance between tolerance and pickiness that is appropriate to your application.

(GCLS)
* ERROR should always be called with an explicit condition type.
* There are a few places where handling all conditions is appropriate, but they are rare. The problem is that handling all conditions can mask program bugs. If you do need to handle "all conditions", you MUST handle only ERROR, not T and not SERIOUS-CONDITION. (This is notably because CCL's process shutdown depends on being able to signal process-reset and have it handled by CCL's handler, so we must not interpose our own handler.)

## 13. LIBRARY USAGE

## Consensus: It's well spoken of. 

(LLSG)
* Look for libraries that solve the problems you are trying to solve before embarking on a project. Making a project with no dependencies is not some sort of virtue. It doesn’t aid portability and it doesn’t help when it comes to turning a Lisp program into an executable.

(PNKP)
* Be opportunistic; use existing tools
* Libraries may have access to low-level efficiency hacks, and are often fine-tuned. BUT they may be too general, hence inefficient. Write a specific version when efficiency is a problem. 

(GCLS)
* You MUST NOT start a new library unless you established that none is already available that can be fixed or completed into becoming what you need. That's a rule against the NIH syndrome ("Not Invented Here"), which is particularly strong amongst Lisp hackers.
* Whichever library, old or new, you pick, you MUST get permission to incorporate third-party code into the code base. You must discuss the use of such library in the appropriate mailing-list, and have your code reviewed by people knowledgeable in the domain and/or the Lisp library ecosystem (if any). Please be ready to argue why this particular solution makes sense as compared to other available libraries.
* Some libraries are distributed under licenses not compatible with the software you're writing, and must not be considered available for use. Be aware of these issues, or consult with people who are.

## 14. RECURSION

## Consensus: Favor iteration over recursion. Recursion is good for recursive data structures.

(PNKP)
* Recursion is good for recursive data structures.

(GCLS)
* You should favor iteration over recursion.

## 15. TYPE CHECKING

## Consensus: If you know the type, you should make it explicit. This may help the compiler and those who need to read your code.

(PNKP)
* If you know type information, declare it. Don't do what some people do and only declare things you know the compiler will use.

(ALCL)
* Add :type to each slots for Class

(LPCM)
* Use type declarations liberally in time-critical code, but only if you are a seasoned Lisp programmer. Appropriate type declarations help the compiler generate more specific and optimized code. It also lets the reader know what assumptions were made

(GCLS)
* If you know the type of something, you should make it explicit in order to enable compile-time and run-time sanity-checking.

(LLSG)
* Types are documentation, and Common Lisp allows you to declare the type of class slots.

## 16. CONDITIONAL EXPRESSSIONS

## Consensus: Rather than using an "if" without an "else" it is better to use either "when" or "unless". Use "cond" for multi-brach statements. 

(PNKP)
* Use the most specific conditional: 
* If for two-branch expression
* when, unless for one branch statement
* and, or for boolean value only
* cond for multi-branch statement or expression

(ALCL)
* Use WHEN, UNLESS if possible
* Don't use if without "else" expression. when is more precise for it.

(LLSG)
* Use if when you have a true branch and a false branch.
* Use when or unless when you’re only interested in one condition branch.
* Use cond when you have several conditional branches.
* If you have an if expression with no else part, you should use when instead, and when you have an expression like (if (not <condition>) ...) with no else part, you should use unless.
 
 (GCLS)
 * Use WHEN and UNLESS when there is only one alternative. Use IF when there are two alternatives and COND when there are several.
 
 ## 17. PREDICATES
 
 ## Consensus: Predicates should be suffixed with "p" or "-p" depending on if the word has hyphens in it already, and return "t" or "nil".
 
 (PNKP)
 * Be consistent in names: -p
 
 (LLSG)
 * Predicates should be suffixed with:
 * "p" If the rest of the function name is a single word, e.g: abstractp, bluep, evenp.
 * "-p" If the rest of the function name is more than one word, e.g largest-planet-p, request-throttled-p.
 
 (GCLS)
 * Names of predicate functions and variables end with a "P".
 * You should name boolean-valued functions and variables with a trailing "P" or "-P", to indicate they are predicates. Generally, you should use "P" when the rest of the function name is one word and "-P" when it is more than one word.
 
 (CLtL)
 * A predicate is a function that tests for some condition involving its arguments and returns nil if the condition is false, or some non-nil value if the condition is true. 
 * By convention, the names of predicates usually end in the letter p (which stands for "predicate").
 * If the name of the predicate is formed by adding a p to an existing name, such as the name of a data type, a hyphen is placed before the final p if and only if there is a hyphen in the existing name.
 
 (LPCM)
 * If you intend for a function to be a predicate, have it return T for true, not just non-NIL. If there is nothing worth returning from a function, returning T is conventional. But if a function is intended to be more than just a predicate, it is better to return a useful value.
 
 
 




