# Conventions and Coding Style #
Following Despark's coding style is mandatory. This makes code more readable and allows for easier code sharing and contributing inside the team.
**Following this conventions will make yours and the lives of everybody in the company easier**
## Class Names and File Location ##
Class names in Kohana follow a strict convention to facilitate autoloading. Class names should have uppercase first letters with underscores to separate words. Underscores are significant as they directly reflect the file location in the filesystem.

The following conventions apply:

1.  CamelCased class names should be used when it is undesirable to create a new directory level.
2.  All class file names and directory names must match the case of the class as per PSR-0.
3.  All classes should be in the classes directory. This may be at any level in the cascading filesystem.

### Examples ###
Remember that in a class, an underscore means a new directory. Consider the following examples:



# Coding Standards #
In order to produce highly consistent source code, we ask that everyone follow the coding standards as closely as possible.

## Brackets ##
Please use BSD/Allman Style bracketing.

### Curly Brackets ###
Curly brackets are placed on their own line, indented to the same level as the control statement.

```php
// Correct
if ($a === $b)
{
    ...
}
else
{
    ...
}

// Incorrect
if ($a === $b) {
    ...
} else {
    ...
}
```

### Class Brackets ###
The only exception to the curly bracket rule is, the opening bracket of a class goes on the same line.

```php
// Correct
class Foo {

// Incorrect
class Foo
{
```

### Empty Brackets ###
Don't put any characters inside empty brackets.

```php
// Correct
class Foo {}

// Incorrect
class Foo { }
```

### Array Brackets ###
Arrays may be single line or multi-line.

```php
array('a' => 'b', 'c' => 'd')

array(
    'a' => 'b',
    'c' => 'd',
)
```

#### Opening Parenthesis ####
The opening array parenthesis goes on the same line.

```php
// Correct
array(
    ...
)

// Incorrect:
array
(
    ...
)
```

#### Closing parenthesis ####
##### Single Dimension #####
The closing parenthesis of a multi-line single dimension array is placed on its own line, indented to the same level as the assignment or statement.

```php
// Correct
$array = array(
    ...
)

// Incorrect
$array = array(
    ...
    )
```

##### Multidimensional #####
The nested array is indented one tab to the right, following the single dimension rules.

```php
// Correct
array(
    'arr' => array(
        ...
    ),
    'arr' => array(
        ...
    ),
)

array(
    'arr' => array(...),
    'arr' => array(...),
)
```

#### Arrays as Function Arguments ####

```php
// Correct
do(array(
    ...
))

// Incorrect
do(array(
    ...
    ))
```

As noted at the start of the array bracket section, single line syntax is also valid.

```php
// Correct
do(array(...))

// Alternative for wrapping long lines
do($bar, 'this is a very long line',
    array(...));
```

### Naming Conventions ###
Kohana uses under_score naming, not camelCase naming.

#### Classes ####

```php
// Controller class, uses Controller_ prefix
class Controller_Apple extends Controller {

// Model class, uses Model_ prefix
class Model_Cheese extends Model {

// Regular class
class Peanut {
```

When creating an instance of a class, don't use parentheses if you're not passing something on to the constructor:

```php
// Correct:
$db = new Database;

// Incorrect:
$db = new Database();
```

#### Functions and Methods ####
Functions should be all lowercase, and use under_scores to separate words:

```php
function drink_beverage($beverage)
{
```

#### Variables ####
All variables should be lowercase and use under_score, not camelCase:

```php
// Correct:
$foo = 'bar';
$long_example = 'uses underscores';

// Incorrect:
$weDontWantThis = 'understood?';
```

### Indentation ###
You must use tabs to indent your code. Using spaces for tabbing is strictly forbidden.

Vertical spacing (for multi-line) is done with spaces. Tabs are not good for vertical alignment because different people have different tab widths.

```php
$text = 'this is a long text block that is wrapped. Normally, we aim for '
      .'wrapping at 80 chars. Vertical alignment is very important for '
      .'code readability. Remember that all indentation is done with tabs,'
      .'but vertical alignment should be completed with spaces, after '
      .'indenting with tabs.';
```

### String Definitions ###

Use single quote in string definitions

```php
// Correct:
$str = 'one';

// Incorrect:
$str = "one";
```

You should avoid string interpolation

```php
$date = date('Y-m-d');

// Correct:
$str = 'Today is '.$date.' and I have birthday.';

// Incorrect:
$str = "Today is $date and I have birthday";
```

The only use of string interpolation should be in expressions which contain strings. For example:

```php
// Correct:
DB::expr("IF(`users`.`phone` = '{$phone}', 1, 0)");

// Incorrect:
DB::expr("IF(`users`.`phone` = '".$phone."', 1, 0)");
```

When using interpolation always wrap variable in curly brackets

```php
// Correct:
DB::expr("IF(`users`.`phone` = '{$phone}', 1, 0)");

// Incorrect:
DB::expr("IF(`users`.`phone` = '$phone', 1, 0)");
```

### String Concatenation ###
Do NOT put spaces around the concatenation operator:

```php
// Correct:
$str = 'one'.$var.'two';

// Incorrect:
$str = 'one' . $var . 'two';
$str = 'one'. $var .'two';
```

### Single Line Statements ###
Single-line IF statements should only be used when breaking normal execution (e.g. return or continue):

```php
// Acceptable:
if ($foo == $bar)
    return $foo;

if ($foo == $bar)
    continue;

if ($foo == $bar)
    break;

if ($foo == $bar)
    throw new Exception('You screwed up!');

// Not acceptable:
if ($baz == $bun)
    $baz = $bar + 2;
```

### Comparison Operations ###
Please use AND / OR logical operators for comarison:

```php
// Correct:
if (($foo AND $bar) OR ($b AND $c))

// Incorrect:
if (($foo == $bar) || ($b == $c))
```

Please use elseif, not else if:

```php
// Correct:
elseif ($bar)

// Incorrect:
else if($bar)
```

#### Switch Structures ####
Each case, break and default should be on a separate line. The block inside a case or default must be indented by 1 tab.

```php
switch ($var)
{
    case 'bar':
    case 'foo':
        echo 'hello';
    break;
    case 1:
        echo 'one';
    break;
    default:
        echo 'bye';
    break;
}
```

### Parentheses ###
There should be one space after statement name, followed by a parenthesis. The ! (bang) character must have a space on either side to ensure maximum readability. Except in the case of a bang or type casting, there should be no whitespace after an opening parenthesis or before a closing parenthesis.

```php
// Correct:
if ($foo == $bar)
if ( ! $foo)

// Incorrect:
if($foo == $bar)
if(!$foo)
if ((int) $foo)
if ( $foo == $bar )
if (! $foo)
```

### Ternaries ###
All ternary operations should follow a standard format. Use parentheses around expressions only, not around just variables.

```php
$foo = ($bar == $foo) ? $foo : $bar;
$foo = $bar ? $foo : $bar;
```

All comparisons and operations must be done inside of a parentheses group:

```php
$foo = ($bar > 5) ? ($bar + $foo) : strlen($bar);
```

When separating complex ternaries (ternaries where the first part goes beyond ~80 chars) into multiple lines, spaces should be used to line up operators, which should be at the front of the successive lines:

```php
$foo = ($bar == $foo)
     ? $foo
     : $bar;
```

### Type Casting ###
Type casting should be done with spaces on each side of the cast:

```php
// Correct:
$foo = (string) $bar;
if ( (string) $bar)

// Incorrect:
$foo = (string)$bar;
```

When possible, please use type casting instead of ternary operations:

```php
// Correct:
$foo = (bool) $bar;

// Incorrect:
$foo = ($bar == TRUE) ? TRUE : FALSE;
```

When casting type to integer or boolean, use the short format:

```php
// Correct:
$foo = (int) $bar;
$foo = (bool) $bar;

// Incorrect:
$foo = (integer) $bar;
$foo = (boolean) $bar;
```

### Constants ###
Always use uppercase for constants:

```php
// Correct:
define('MY_CONSTANT', 'my_value');
$a = TRUE;
$b = NULL;

// Incorrect:
define('MyConstant', 'my_value');
$a = True;
$b = null;
```

Place constant comparisons at the end of tests:

```php
// Correct:
if ($foo !== FALSE)

// Incorrect:
if (FALSE !== $foo)
```

This is a slightly controversial choice, so I will explain the reasoning. If we were to write the previous example in plain English, the correct example would read:
if variable <b>$foo</b> is not exactly <b>FALSE</b>

And the incorrect example would read:
if <b>FALSE</b> is not exactly variable <b>$foo</b>

Since we are reading left to right, it simply doesn't make sense to put the constant first.

### Comments ###
#### One-line Comments ####
Use //, preferably above the line of code you're commenting on. Leave a space after it and start with a capital. Never use #.

```php
// Correct

//Incorrect
// incorrect
# Incorrect
```

### Regular Expressions ###
When coding regular expressions please use PCRE rather than the POSIX flavor. PCRE is considered more powerful and faster.

```php
// Correct:
if (preg_match('/abc/i', $str))

// Incorrect:
if (eregi('abc', $str))
```

Use single quotes around your regular expressions rather than double quotes. Single-quoted strings are more convenient because of their simplicity. Unlike double-quoted strings they don't support variable interpolation nor integrated backslash sequences like \n or \t, etc.

```php
// Correct:
preg_match('/abc/', $str);

// Incorrect:
preg_match("/abc/", $str);
```

When performing a regular expression search and replace, please use the $n notation for backreferences. This is preferred over \n.

```php
// Correct:
preg_replace('/(\d+) dollar/', '$1 euro', $str);

// Incorrect:
preg_replace('/(\d+) dollar/', '\\1 euro', $str);
```

Finally, please note that the $ character for matching the position at the end of the line allows for a following newline character. Use the D modifier to fix this if needed. More info.

```php
$str = "email@example.com<script type="text/javascript">
/* <![CDATA[ */
    (function(){try{var s,a,i,j,r,c,l,b=document.getElementsByTagName("script");l=b[b.length-1].previousSibling;a=l.getAttribute('data-cfemail');if(a){s='';r=parseInt(a.substr(0,2),16);for(j=2;a.length-j;j+=2){c=parseInt(a.substr(j,2),16)^r;s+=String.fromCharCode(c);}s=document.createTextNode(s);l.parentNode.replaceChild(s,l);}}catch(e){}})();
/* ]]> */
</script>\n";

preg_match('/^.+@.+$/', $str);  // TRUE
preg_match('/^.+@.+$/D', $str); // FALSE
```

### Whitespaces ###
Operators if, switch, for, foreach, while, etc. are followed by one whitespace and expression wrapped in parentheses

```php
// Correct:
if ($variable == 'one') {...}
foreach ($users as $user) {...}

// Incorrect:
if($variable == 'one') {...}
foreach($users as $user) {...}
```

Don't put whitespace inside parentheses

```php
// Correct:
if ($variable == 'one') {...}
switch ($variable) {...}

// Incorrect:
if ( $variable == 'one' ) {...}
switch ( $variable ) {...}
```

Whitespaces in for

```php
// Correct:
for ($i = 1; $i < 10; $i++)
{
    // code...
}

// Incorrect:
for ($i=1; $i<10; $i++)
{
    // code...
}
```

Whitespaces in function parameters

```php
// Correct:
function my_awesome_function($type, $date, $default = NULL)
{
    // code...
}

// Incorrect:
function my_awesome_function($type,$date,$default=NULL)
{
    // code...
}
```

## PHP in HTML ##

In Kohana View files always use short tags for PHP

```php
// Correct:
<? if ($expression): ?>
    <p>Awseome</p>
<? endif ?>

// Incorrect:
<?php if ($expression): ?>
    <p>Awseome</p>
<?php endif ?>
```

Single lines of PHP don't need ``` ; ``` at end of line

```php
// Correct:
<? endif ?>
<? endforeach ?>
<? endfor ?>
<? $var = 100 ?>

// Incorrect:
<? endif; ?>
<? endforeach; ?>
<? endfor; ?>
<? $var = 100; ?>
```

### Indentation ###

Treat PHP tags as HTML tags

```php
// Correct:
<ul class="users">
    <? foreach ($users as $user): ?>
        <li>
            <?= HTML::anchor($user->profile_url(), $user->name()) ?>
        </li>
    <? endforeach ?>
</ul>

// Incorrect:
<ul class="users">
<? foreach ($users as $user): ?>
    <li>
    <?= HTML::anchor($user->profile_url(), $user->name()) ?>
    </li>
<? endforeach ?>
</ul>

// Incorrect:
<ul class="users">
    <? foreach ($users as $user): ?>
    <li>
        <?= HTML::anchor($user->profile_url(), $user->name()) ?>
    </li>
    <? endforeach ?>
</ul>
```

```php
// Correct:
<ul class="users">
    <? foreach ($users as $user): ?>
        <? if ($user->is_admin()): ?>
            <li>
                <?= HTML::anchor($user->profile_url(), $user->name()) ?>
            </li>
        <? endif ?>
    <? endforeach ?>
</ul>

// Incorrect:
<ul class="users">
    <? foreach ($users as $user):
    if ($user->is_admin()): ?>
        <li>
            <?= HTML::anchor($user->profile_url(), $user->name()) ?>
        </li>
    <? endif;
endforeach ?>
</ul>
```

Switch Structures

```php
// Correct:
<div class="subrow">
    <? switch ($prize->type): ?>
        <? case 'meal': ?>
            <span class="discount-name"><?= $prize->name($item->quantity) ?></span>
        <? break ?>
        <? case 'free_text': ?>
            <span class="discount-name"><?= $prize->name($item->quantity) ?></span>
        <? break ?>
        <? default: ?>
            <span class="discount-name"><?= $prize->name() ?></span>
            <span class="discount-sum"><?= Num::price($item->price, TRUE, 'b', FALSE) ?></span>
        <? break ?>
    <? endswitch ?>
</div>

// Incorrect:
<div class="subrow">
    <? switch ($prize->type):
        case 'meal': ?>
            <span class="discount-name"><?= $prize->name($item->quantity) ?></span>
        <? break;
        case 'free_text': ?>
            <span class="discount-name"><?= $prize->name($item->quantity) ?></span>
        <? break;
        default: ?>
            <span class="discount-name"><?= $prize->name() ?></span>
            <span class="discount-sum"><?= Num::price($item->price, TRUE, 'b', FALSE) ?></span>
        <? break; ?>
    <? endswitch; ?>
</div>
```

Don't indentate PHP code outside of block

```php
// Correct:
<?
$j = $i + 5 / abs($total_pages);
$variable = 4 + $j;
?>

// Incorrect:
<?
    $j = $i + 5 / abs($total_pages);
    $variable = 4 + $j;
?>
```

Form helpers

```php
// Correct:
$measure_form->row('select', 'name', array(
    'label' => __('lbl_measure'),
    'choices' => $measures,
    'include_blank' => TRUE,
    'custom' => TRUE,
),
array(
    'id' => NULL,
    'class' => 'measure_type',
));

// Incorrect:
$measure_form->row(
    'select',
    'name',
    array(
        'label' => __('lbl_measure'),
        'choices' => $measures,
        'include_blank' => TRUE,
        'custom' => TRUE,
        ),
    array(
        'id' => NULL,
        'class' => 'measure_type',
        )
    );
```

## Other good practices ##

##### Avoid defining variables in expressions #####

```php
// Correct:
$logged = get_logged_user();
if ($logged === TRUE)
{
    // code...
}


// Incorrect:
if (($logged = get_logged_user()) === TRUE)
{
    // code...
}
```

##### Keep expressions as simple as possible #####

```php
// Correct:
$orders = Jam::all('orders')->order_by('created_at', 'desc');
foreach ($orders as $key => $value)
{
    # code...
}

// Incorrect:
foreach (Jam::all('orders')->order_by('asd', 'desc') as $key => $value)
{
    # code...
}

```

##### Use blank lines to make your code more readable #####
The "rule" is: put new line when change the logic.

```php
// Good:
public function is_it_open()
{
    $self = get_self();
    $self_for_weekday = get_self_weekday();

    $working_now = $self
        ->and_where('start_hour', '<=', date('H:i:s'))
        ->and_where('end_hour', '>=', date('H:i:s'))
        ->and_where('date', '=', date('Y-m-d'))
        ->and_where('is_closed', '=', '0')
        ->first();

    $working_now_weekday = $self_for_weekday
        ->and_where('start_hour', '<=', date('H:i:s'))
        ->and_where('end_hour', '>=', date('H:i:s'))
        ->and_where('is_closed', '=', '0')
        ->and_where('week_day', '=', date('N'))
        ->first();

    if ($working_now OR $working_now_weekday)
    {
        return TRUE;
    }

    return FALSE;
}

// Bad:
public function is_it_open()
{
    $self = get_self();
    $self_for_weekday = get_self_weekday();
    $working_now = $self
        ->and_where('start_hour', '<=', date('H:i:s'))
        ->and_where('end_hour', '>=', date('H:i:s'))
        ->and_where('date', '=', date('Y-m-d'))
        ->and_where('is_closed', '=', '0')
        ->first();
    $working_now_weekday = $self_for_weekday
        ->and_where('start_hour', '<=', date('H:i:s'))
        ->and_where('end_hour', '>=', date('H:i:s'))
        ->and_where('is_closed', '=', '0')
        ->and_where('week_day', '=', date('N'))
        ->first();
    if($working_now || $working_now_weekday)
    {
        return TRUE;
    }
    return FALSE;
}
```

##### Use Date Constants for minutes, hours, days, etc. instead of 60, 3600, 24*3600 #####

```php
// Correct:
return date('H.i', strtotime($working_tommorow->start_hour)) * Date::HOUR + (Date::DAY - $current_time_in_seconds);

// Incorrect:
return date('H.i', strtotime($working_tommorow->start_hour)) * 3600 + (24*3600 - $current_time_in_seconds);
```
