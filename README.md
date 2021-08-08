# Thank you for your response

## 1. Anagram Tester

```php
function anagram($first_word, $second_word) {
  return count_chars($first_word, 1) == count_chars($second_word, 1);
}
```

## 2. Rewrite Pow

```php
function my_pow($base, $exponent) {
  if (!is_int($exponent)) {
    return null;
  }

  if ($exponent == 0) {
    return 1;
  }

  $isNegative = $exponent < 0;
  if ($isNegative) {
    $exponent *= -1;
  }

  $res = $base;
  for ($i = 1; $i < $exponent; $i++) {
    $res *= $base;
  }
  return $isNegative ? (1 / $res) : $res;
}
```

## 3. Knowledge base

### 3.1 SQL Injections

SQL injection is a code injection technique that can change your database.
SQL injection attacks data-driven applications, in which malicious SQL statements are inserted into an entry field for execution.
**Prevent SQL injection:**

- Validate input
- Use prepared statements
- Stored procedures
- Use escaping
- Hide exception, error message
- Set permissions in the database
- Use ORM layer
- Use Web application firewall
- Backup database
- Validate your application

**PHP best practices for preventing SQL injection are to apply as many of them as possible**

### 3.2 N+1 Query

N+1 query occurs when we get a query, each result of the previous query entails N other queries. Thus, 1 is the original query, N is the number of queries called for each original query result.

**Example in Laravel:**

```php
class Post extends Model
{
    /**
     * Get the user that creates the post.
     */
    public function user()
    {
        return $this->belongsTo('App\User’);
    }
}
```

**When we get:**

```php
$posts = App\Models\Post::all();

foreach ($posts as $post) {
    echo $post->user->name;
}
```

**With 5 posts:**

```sql
SELECT * FROM posts;
SELECT * FROM users WHERE id=1;
SELECT * FROM users WHERE id=2;
SELECT * FROM users WHERE id=3;
SELECT * FROM users WHERE id=4;
SELECT * FROM users WHERE id=5;
```

**Use Eager Loading for improve:**

```php
$posts = App\Models\Post::with(‘user’)->all();

foreach ($posts as $post) {
    echo $post->user->name;
}
```

**With 5 posts:**

```sql
SELECT * FROM posts;
SELECT * FROM users WHERE id IN (1, 2, 3, 4, 5);
```

### 3.3 `===` vs `==`

**Different:**

Equal Operator (==) accepts two inputs to compare and returns true value if both of the values are same (It compares only value of variable, not data types) and returns a false value if both of the values are not same.
Identical Operator (===) allows for a much stricter comparison between the given variables or values. This operator returns true if both variables contain the same information and same data types otherwise return false.

**Use ===:**

Checks to see if the left and right values are equal, and also checks to see if they are of the same variable type

**Use ==:**

Checks to see if the left and right values are equal

### 3.4 Server Variable

$stringVariable ?? ‘’; $intVariable ?? 0;

### 3.5 Test Unit / Unit Testing

Unit Testing is a software testing method by which individual units of source code—sets of one or more computer program modules together with associated control data, usage procedures, and operating procedures—are tested to determine whether they are fit for use. Unit tests are typically automated tests written and run by software developers to ensure that a section of an application (known as the "unit") meets its design and behaves as intended. By writing tests first for the smallest testable units, then the compound behaviors between those, one can build up comprehensive tests for complex applications.

I use Laravel testing to write Unit or Feature Test for many tasks I get.

I think we need to use Unit Testing for every task to detect error and detect slow and inefficient functions through Unit Test runtime.

## 4. Bug Fixing

- Backup database.
- Log both input and output data for comparison.
- Reproduce.
- Debug and fix code.
- Reproduce with new code.
- Try again with the same case (Debug and fix code).
- Refactor and clean code.

## 5. Taking over an old project

- Restructure each part of the project. Break down modules for processing.
- Cover as many cases as possible.
- If we have time, refactor code and upgrade the newest system for the future

I have maintained a lot of systems like that.
