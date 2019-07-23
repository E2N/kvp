# Key Value Pairs (KVP) Specification

A key value pair consists of an identifier KEY, followed by a SEPARATOR, a VALUE and a prefix and suffix termed the KVDELIMITER

KVDELIMITER KEY {whitespace} SEPARATOR {whitespace} VALUE{UNIT} KVDELIMITER

## Term Definitions

- An alphanumeric characters is any character in the character set a-zA-Z and 0-9.
- A character sequence is numeric if it contains only characters from the set 0-9. 

### KVDELIMITER

- at least one characters from " " "," ";" "\t" "\r" and "\n"
  - space " "
  - comma " "
  - semicolon ";"
  - tab "\t"
  - carriage return "\r"
  - newline "\n"

### KEY

- must have at least one character
- the allowed list of characters is any alphanumeric plus "_" "." "$" and "@"
- the first character must be non numeric character
- can be enclosed in double quotes to escape non allowed characters

### {whitespace} 

- an optional space " " 

### VALUE

- consists of any alphanumeric plus "_" "." "$" "@"
- can be enclosed in double quotes to escape non allowed characters

#### UNIT

- an optional suffix for a numerical VALUE
- can be percent character "%" or up to two alphabetical characters

### SEPARATOR

- is the character "="
- can be preceded and followed by a space " "

## Character Escaping

- Used to allow a KEY or VALUE to contain a character that would not otherwise be allowed, e.g. a space or quote or comma or bracket is not allowed in a KEY or VALUE unless escaped.
- Is supported in both KEY and VALUE by adding a backslash "\" in front of the character to be escaped or by including the entire KEY or VALUE in double quotes

## Examples

- latency=100ms, cpu.load = 2%
- timestamp=1563880736, url="https://example.com?id=1", user="Jane Doe"
- "timestamp"=1563880736, url="https://example.com?id=1", user=Jane\ Doe
- "timestamp[0]"=1563880736 url="https://example.com?id=1" user=Jane\ Doe

## Additional Notes

- UTF-8 should be the default encoding
- Unless escaped the characters "-", "+" should not be used in KEY or VALUE 
- Character escaping should be done with doubles quotes instead of a backslash
- Pick a consistent SEPARATOR for all key value pairs and do not mix different separators in one record