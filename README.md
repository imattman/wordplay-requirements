# Wordplay Requirements

Design and build an application that implements a wordplay game solver, as defined below.  
Please show evidence of test-driven development with unit tests, along with example usage and/or runner scripts.  

Create a RESTful web service that handles queries based on a lexicon of valid accepted words.
The lexicon should be loaded from an external resource file, the path to which is configurable and specified at application start up.
You can assume the lexicon file conforms to a regular format such as a plain text file with one word entry per line.

Expose a RESTful interface that allows a client to:

  - GET a valid word and its score if contained in the lexicon
  - POST a valid word along with explicit letter point values that override the default letter scoring
    - Supplying a partial set of letter point overrides is legal.  Omitted letters should fall back to their default point value.
  - GET the top 10 word matches based on score that can be formed using only the supplied letters (full or parital set)
  - POST the top 10 word matches based on score that can be formed using only the supplied letters (full or partial set) and the custom explicit letter point values
    - Supplying a partial set of letter point overrides is legal.  Omitted letters should fall back to their default point value.
  - GET Lexicon and application statistics including
    - Overall size of lexicon, length of longest and shortest entries
    - Number of match queries executed since application start
    - Top N scoring words matched
    - Relevant K<sup>th</sup> percentile slow match times

Design your own data and API structure(s) for the lexicon index.
Include an `X-query-executed` HTTP header with the match execution time in all lookup/match reponses.
Implement at least 2 word matching algorithms, including brute force and something more efficient.

  - Show tests that demonstrate the difference in match speed
  - Allow switching the match algorithms at deploy-time via only configuration.

Consider making your application lenient in the data it accepts (e.g. capital vs. lowercase letters)


## Letter Scoring

Default scoring is to be calculated using Scrabble letter point values.

| Point Value | Letters                      |
|-------------|------------------------------|
| 1           | A, E, I, L, N, O, R, S, T, U |
| 2           | D, G                         |
| 3           | B, C, M, P                   |
| 4           | F, H, V, W, Y                |
| 5           | K                            |
| 8           | J, X                         |
| 10          | Q, Z                         |




