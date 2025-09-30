#include <stdio.h>
#include <string.h>
#include <ctype.h>

int main() {
    char text[1000];
    int i, words = 0, lines = 0, characters = 0;

    printf("Enter text (end input with '~'):\n");

    // Read input until '~'
    i = 0;
    char ch;
    while ((ch = getchar()) != '~' && i < 999) {
        text[i++] = ch;
    }
    text[i] = '\0';

    // Count characters, words, and lines
    characters = strlen(text);

    for (i = 0; text[i] != '\0'; i++) {
        if (text[i] == '\n')
            lines++;
        if ((isspace(text[i]) || text[i+1] == '\0') && 
            (i > 0 && !isspace(text[i-1]))) {
            words++;
        }
    }

    // If text contains at least one line
    if (characters > 0)
        lines++;

    printf("\n--- Count Result ---\n");
    printf("Characters: %d\n", characters);
    printf("Words     : %d\n", words);
    printf("Lines     : %d\n", lines);

    return 0;
}