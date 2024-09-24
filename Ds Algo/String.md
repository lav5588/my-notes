
## Knuth Moris Patt (KMP) Algorithm
**Intution:-**

The Knuth-Morris-Pratt (KMP) algorithm is an efficient string matching algorithm that avoids redundant comparisons by preprocessing the pattern to create an LPS (Longest Prefix Suffix) array. The LPS array stores the length of the longest proper prefix of the pattern which is also a suffix for each prefix of the pattern. During the search phase, when a mismatch occurs after matching some characters, the algorithm uses the LPS array to skip unnecessary comparisons in the pattern, allowing it to continue searching without backtracking in the text. This results in a linear time complexity for both the preprocessing and searching phases.

```cpp
class KMPAlgorithm {
public:
    // Function to compute the LPS (Longest Prefix Suffix) array
    void computeLPSArray(const string& pattern, vector<int>& lpsArray) {
        int patternLength = pattern.length();
        int longestPrefixLength = 0; // Length of the previous longest prefix & suffix

        lpsArray[0] = 0; // No proper prefix and suffix for the first character

        int currentIndex = 1;
        while (currentIndex < patternLength) {
            if (pattern[currentIndex] == pattern[longestPrefixLength]) {
                longestPrefixLength++;
                lpsArray[currentIndex] = longestPrefixLength;
                currentIndex++;
            } else {
                if (longestPrefixLength != 0) {
                    longestPrefixLength = lpsArray[longestPrefixLength - 1]; // Use the previously computed LPS
                } else {
                    lpsArray[currentIndex] = 0;
                    currentIndex++;
                }
            }
        }
    }

    vector<int> searchPattern(const string& pattern, const string& text) {
        int textLength = text.length();
        int patternLength = pattern.length();
        vector<int> matchPositions;

        // Create an LPS array to store the longest proper prefix which is also a suffix
        vector<int> lpsArray(patternLength, 0);
        computeLPSArray(pattern, lpsArray);

        int textIndex = 0; // Index for text
        int patternIndex = 0; // Index for pattern

        while (textIndex < textLength) {
            if (pattern[patternIndex] == text[textIndex]) {
                textIndex++;
                patternIndex++;
            }

            if (patternIndex == patternLength) {
                matchPositions.push_back(textIndex - patternIndex + 1); // Store match position (1-based index)
                patternIndex = lpsArray[patternIndex - 1];
            } else if (textIndex < textLength && pattern[patternIndex] != text[textIndex]) {
                if (patternIndex != 0) {
                    patternIndex = lpsArray[patternIndex - 1];
                } else {
                    textIndex++;
                }
            }
        }

        return matchPositions;
    }
};

```