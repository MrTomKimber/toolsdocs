# Parsing

Parsing is a broad term used to describe the conversion of information provided in one representation into another differently structured representation. 

For example, parsing of a csv file means reading in text strings which are then processed and transformed into records of data each with content associated with a set of fields or attributes. 

Other parsing flows of this type might include reading XML or JSON files and marshalling their data into a form that supports processing, reporting or analysis. The XML or JSON specifications might include schema-describing files, such as XSDs or JSON-Schema documents that can be used to validate the proper formatting and construction of a given input file. Given the possible complexity behind some of these data packaging schemes, tight validation checks can be invaluable prior to running any automated workflow against what could be incorrectly structured input data. 

In addition to reading in data that's provided in increasingly complex structured formats, another common parsing requirement is to consume text that's been written to communicate rules, instructions, specifications or configuration in some formally defined language. These language files must be parsed (in some cases compiled) in order to extract their meaning.

For these language style constructs, parsing is commonly the process of reading in the text written in some language, and converting it into an Abstract Syntax Tree (AST). An AST is often some kind of tree or network structure that enables a program to walk or navigate its different branches, enabling automation or generation of some calculation, function or result. Such processes might include compilation, where a relatively high-level language might be compiled, via an AST, into executable machine code. 

Alternately, an AST enables, given an appropriate dictionary of functions or aliases, the translation of a given formal language into another language. Once complete, a compiler or parser for the new language can be used to run or execute the newly generated code. 

Languages don't need to be written as text, many different objects can be considered parsable. Data models can be parsed, and converted into RDBMS specific DDL code, enabling the model to serve as both the document, the specification and the source of the code for the finished product. And to refer back to the AST concept and use it in reverse, given some DDL, or even a SELECT statement as text, this can be formally parsed and used to construct a pictorial model, enabling the automated documentation of technical assets directly from their code. 

## Simple Parsing Code Snippets

### Common String Manipulations

#### Block Toggling Characters and Common Escaping Patterns



#### Matching Open-Close Block Definitions

Some structures you'll find out in the wild include the concept of defining blocks using separate opening and closing characters. \(Brackets\), \[square brackets\], \{curly braces\}, “opening and closing speech-marks”, \<angle-brackets\> and «guillemets» are all examples of this type of structure found with varying frequency. Simple scanning searches can be used to define blocks such as these, but care should be taken as these structures are commonly nested.

Where bracketing is nested, it usually conveys imporant structure, so for example `(2 + a + b) x c` means something very different to `(2 + a ) + (b x c)` or variations thereof. A common concept for parsing through bracketed content is to match-off appropriately paired opening and closing bracket pairs.

The following code, given a single set of opening/closing characters and some text, will return an array describing the positions of each paired set of braces. It might need further work to handle cases where multiple different pairing schemes (say where parentheses, square and curly brackets are all used) but this should work for single-style paired delimiters like these.

Adopting use of the re library to find the different values extends the flexibility somewhat of the search parameters, e.g. multi-char open-close delimiters can be found like `<--` and `-->`, or `/*` and `*/` which might denote blocks of commentary in different contexts.

``` {.python}
import re

def matching_paired_char_blocks(open_char, close_char, text):

    def next_drop(start, value, levels):
        for v in range(start, len(levels)):
            if levels[v][1]==value-1:
                return levels[v][0]+1
        return None
        
    s=0
    # Get positive increments (i.e. positions where open_char is found
    posincs = [(v.span()[0],1) for i,v in enumerate(re.finditer(open_char, text))]
    # Get negative increments (i.e. positions where close_char is found
    negincs = [(v.span()[0],-1) for i,v in enumerate(re.finditer(close_char, text))]
    # Merge the two sets of increments and sort on position, "zipping" the two lists together
    posincs.extend(negincs)
    levels = [(0,0)]
    for p,d in sorted(posincs, key=lambda x : x[0]):
        s = s + d
        if p == 0:
            levels[0] = (p,s)
        else:
            levels.append((p,s))

    # Iterate over the levels, matching each increment to its associated decrement
    # building a list of open, close, level statements describing the extent of each open/close pair
    l_pairs = []
    last_level=0
    adj=0
    for e, (s, v) in enumerate(levels):
        if v>last_level:
            l_pairs.append((v+adj, s, next_drop(e,v,levels)))
        else:
            if v+adj<0:
                l_pairs.append((None, None, s))
                adj = adj + 1
        last_level = v
    return l_pairs
```




### Regular Expressions

### Formal Grammars

A *formal grammar* is a linguistics concept initially developed by Noam Chomsky in 1956 wherein languages are described as a set consisting of {V, T, P, S} where:

* V are the lanuguage non-terminals, 
* T are the Terminals, 
* P are Production Rules and 
* S describes something called the Start Symbol.

In any such grammar, the Terminal smbols describe the individual words that are reserved in the language. The non-terminal symbols are named higher level structures and phrases that feature in the language, and the Production Rules describe in detail how these non-terminal symbols can be composed from mixtures of terminal and non-terminal symbols. The Start symbol S represents all possible legal phrases and statements expressable within the language. If there is an unbroken link from all the Terminal symbols, through non-terminals described by production-rules, then the grammar is complete and can be parsed using one of a number of strategies.

This approach is useful when parsing languages meant to control computers, programming languages, data definition languages and other DSLs are often made readable using the formal grammar parsing theory. 

