
/* In any language program, most syntax errors occur due to unbalanced delimiters such as
(), {}, []. Write a C++ program using a stack to check whether a given expression is well
parenthesized or not.
*/

#include <iostream>
using namespace std;
#define SIZE 10

class StackExp {
    int top;
    char stk[SIZE];

public:
    StackExp() {
        top = -1;
    }

    void push(char);
    char pop();
    int isFull();
    int isEmpty();
};

void StackExp::push(char x) {
    top = top + 1;
    stk[top] = x;
}

char StackExp::pop() {
    char s = stk[top];
    top = top - 1;
    return s;
}

int StackExp::isFull() {
    if (top == SIZE - 1)
        return 1;
    else
        return 0;
}

int StackExp::isEmpty() {
    if (top == -1)
        return 1;
    else
        return 0;
}

int main() {
    StackExp s1;
    char exp[20], ch;
    int i = 0;

    cout << "\n\t!! Parenthesis Checker..!!!!" << endl;
    cout << "\nEnter the expression to check whether it is in well-formed or not: ";
    cin >> exp;

    if ((exp[0] == ')') || (exp[0] == ']') || (exp[0] == '}')) {
        cout << "\nInvalid Expression.....\n";
        return 0;
    } else {
        while (exp[i] != '\0') {
            ch = exp[i];
            switch (ch) {
                case '(':
                case '[':
                case '{':
                    s1.push(ch);
                    break;
                case ')':
                case ']':
                case '}':
                    s1.pop();
                    break;
            }
            i = i + 1;
        }
    }

    if (s1.isEmpty()) {
        cout << "\nExpression is well parenthesized...\n";
    } else {
        cout << "\nSorry!!! Invalid Expression or not well parenthesized....\n";
    }

    return 0;
}
