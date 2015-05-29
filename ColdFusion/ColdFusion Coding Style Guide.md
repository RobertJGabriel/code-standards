ColdFusion Coding Style Guide
=============================

**Author:** Adam Presley
**Revisions:**

|Date        |Author           |Revision
|------------|-----------------|----------------------------------------------|
|2015-05-28  |Adam Presley     |Initial creation                              |


1. Whitespace and Formatting
----------------------------

### 1.1 Indentation
* Use hard tabs set to three (3) spaces.
* Do not mix tabs and spaces.

### 1.2 Line Length
* Line length *must not* exceed 120 characters
* Lines *should not* exceed 80 characters

### 1.3 Spaces
* Use spaces after commas in arguments lists
* *Do not use spaces* before commas in argument lists

**Good**
```cfm
public void function sayHi(string name, numeric age) output="false" {

}
```

**Bad**
```cfm
public void function sayHi(string name , numeric age) output="false" {

}
```

* *Do not use spaces* before or after parenthesis when defining and calling
   functions
* *Do* put a space between a parenthesis and **if**, **while**
* *Do* put a space after a closing parenthesis and an open curly brace

**Good**
```cfm
local.sum = add(left=1, right=2);
if (local.sum > 10) {
   // Do stuff
}
```

**Bad**
```cfm
local.sum = add ( left=1, right=2 );
if(local.sum > 10){
   // Do stuff
}
```

* *Do* use spaces between operators and operands in expresions

**Good**
```cfm
local.sum = 1 + 4 + local.somethingElse;
```

**Bad**
```cfm
local.sum = 1+4+local.somethingElse;
```

* *Do not* use spaces around equal signs when calling functions using named
   arguments
* *Do not* use spaces around equal signs when defining default values for
   arguments in function declarations

**Good**
```cfm
public string function doStuff(string name="Adam") output="false" {

}

local.result = doStuff(name="Bob");
```

**Bad**
```cfm
public string function doStuff(string name = "Adam") output="false" {

}

local.result = doStuff(name = "Bob");
```

### 1.4 Curly and Square Braces
* All open curly braces for function declarations, try/catch blocks, while,
   if, and structure variable declarations go on the same line as the
   statement/expression they are attached to
* All closing curly braces go on the next line
* Open curly braces for structures defined inside an array may start on their
   own line
* All open square braces go on the same line as the statement/expression they
   are attached to

**Good**
```cfm
if (isValid) {
   // Do stuff
}

try {
   // dangerous code
} catch {
   // log me!
}

local.claim = {
   id=1,
   token="12345",
   associated=[1, 2, 3],
   nonAssociated=[
      4,
      5,
      6
   ]
};

local.people = [
   {
      name: "Adam",
      age: 36
   }
];
```

**Bad**
```cfm
if (isValid)
{
   // Do stuff
}

try
{
   // dangerous code
}
catch
{
   // log me!
}

local.claim =
{
   id=1,
   token="12345",
   associated=
   [
      1,
      2,
      3
   ],
   nonAssociated=
   [4,5,6]
};

local.people =
[{
   name: "Adam",
   age: 36
}];
```

### 1.5 CFML/Script Conventions
When working with CFML (not CFScript) the following applies.

* ColdFusion tags *must be* **Lower case**
* Tags must either have an equivalent closing tag, or be self-closing
* All tags must be indented one level from their parent. This applies when
   the parent is another CFML tag, or an HTML tag

**Good**
```cfm
<p>
   <cfif viewData.customer.hasModule(name="SomeModule")>
      <cfset text = "Text 1" />
   <cfelse>
      <cfset text = "Text 2" />
   </cfif>

   <cfoutput>#text#</cfoutput>
</p>
```

**Bad**
```cfm
<p><CFIF viewData.customer.hasModule("SomeModule")>
<cfset text = "Text 1"><cfelse><cfset text = "Text 2">
<cfoutput>#text#</cfoutput></p>
```

When working with CF function in both script and CFML, the following applies.

* ColdFusion functions *must be* **Camel case**

**Example**
```cfm
public void function addItemToCart(required CartItem item) output="false" {
   arrayAppend(variables.shoppingCart, item);
}
```

2. Casing and Naming
--------------------

### 2.1 Casing Definitions
* **Lower case** - All digits are lower cased. Example: ```mynamehere```
* **Upper case** - All digits are upper cased. Example: ```MYNAMEHERE```
* **Pascal case** - First letter of each word upper cased, starting with an upper
   case letter. Example: ```MyNameHere```
* **Camel case** - First letter of each word upper cased, starting with a lower
   case letter. Example: ```myNameHere```

### 2.2 Variable Names
* All variable names *must be* in **camel case**

**Example**
```cfm
local.payPeriod = "Bi-weekly";
local.allCustomerSettings = [];
```

### 2.3 Constants
ColdFusion doesn't support true constants, but...

* As a convention use **Upper case** when defining a variable that is intended
   to be used as a constant
* Use underscores between words

**Example**
```cfm
this.VALID_STATES = [
   "Ready",
   "Parsing",
   "EOF"
];
```

### 2.4 Function Names
* Function names *must use* **Camel case**. Example: ```deleteRecordByID()```

### 2.5 Package Names
Much like in Java ColdFusion supports the concept of packages. A component
placed in a directory structure is considered to part of that package. For
example, a component named **PermissionService.cfc** placed in a directory path
of ```/Services/Security``` is considered to be in the *Services.Security*
package.

* Directories designed to be used as package *must use* **Pascal case**

This means that in the above example both the **Services** and the **Security**
directories follow the **Pascal case** convention. Then when instantiating
a component from this package it will look like this.

```cfm
local.permissionService = new Services.Security.PermissionService();
```

### 2.6 Component File Names
* Components (CFC files) *must use* **Pascal case**. Example: ```TokenMapper.cfc```

### 2.7 CFM File Names
* ColdFusion files with a CFM extension *must use* **Camel case**.
   Example: ```permissionManager.cfm```

### 2.8 Abbreviations
Avoid abbreviations when possible. If a given abbreviation is well known to
a given industry or domain it is acceptable to use.

### 2.9 Acronyms
Acronyms are similar to abbreviations. They should be avoided when possible.
However some acronyms, if common enough in your domain, are acceptable.

* Acronyms *must be* **Upper case** in all situations, ***unless*** they are
   at the start of the word. Words, variables, and functions that start with
   an acronym *must be* **Lower case**

**Examples**
```cfm
local.userSSN = "12345";
request.urlPrefix = "http://";
local.workerID = 1;
local.id = 10;
```