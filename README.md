# Valid-Parentheses
Valid Parentheses

Given a string s containing just the characters '(', ')', '{', '}', '[' and ']', determine if the input string is valid.

An input string is valid if:

Open brackets must be closed by the same type of brackets.
Open brackets must be closed in the correct order.
Every close bracket has a corresponding open bracket of the same type.
 

Example 1:

Input: s = "()"
Output: true
Example 2:

Input: s = "()[]{}"
Output: true
Example 3:

Input: s = "(]"
Output: false



//Code C# Prgramming.........................

class Solution {
    public bool IsValid(string s) {
        // Create a stack to keep track of open brackets.
        Stack<char> stack = new Stack<char>();

        // Define a mapping of open and close brackets.
        Dictionary<char, char> bracketMapping = new Dictionary<char, char> {
            { '(', ')' },
            { '[', ']' },
            { '{', '}' }
        };

        // Iterate through each character in the string.
        foreach (char c in s) {
            // If the character is an open bracket, push it onto the stack.
            if (bracketMapping.ContainsKey(c)) {
                stack.Push(c);
            }
            // If the character is a close bracket.
            else {
                // If the stack is empty or the top of the stack does not match the current character, return false.
                if (stack.Count == 0 || bracketMapping[stack.Pop()] != c) {
                    return false;
                }
            }
        }

        // After processing the string, the stack should be empty if it's valid.
        return stack.Count == 0;
    }
}














 

Constraints:

1 <= s.length <= 104
s consists of parentheses only '()[]{}'.
