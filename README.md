# Wordline-and-character-counter
Making word line and character counter using file handling
#include <stdio.h>
#include <stdlib.h>
#include <ctype.h>

int main() {
    FILE *fp;
    char filename[100];
    char ch;
    int lines = 0, words = 0, characters = 0;
    int inWord = 0;

    // Ask user for file name
    printf("Enter filename: ");
    scanf("%s", filename);

    // Open file
    fp = fopen(filename, "r");
    if (fp == NULL) {
        printf("Error: Cannot open file %s\n", filename);
        exit(1);
    }

    // Read file character by character
    while ((ch = fgetc(fp)) != EOF) {
        characters++;

        if (ch == '\n')
            lines++;

        if (isspace(ch)) {
            inWord = 0;
        } else if (!inWord) {
            inWord = 1;
            words++;
        }
    }

    fclose(fp);

    // If file not empty, add last line
    if (characters > 0 && ch == EOF)
        lines++;

    printf("Lines      : %d\n", lines);
    printf("Words      : %d\n", words);
    printf("Characters : %d\n", characters);

    return 0;
}
