# cs50
School Asignmennt

/***************************************
 * Caesar,c
 * Emily Donato
 * 4/17/18
 * This program takes a key and rotates
   all letters in plain text by this
   number
***************************************/

#include <stdio.h>
#include <cs50.h>
#include <string.h>
#include <stdlib.h>
#include <ctype.h>

int main (int argc, string argv[2])
{
    // Checks to see if the key was entered
    if (argc != 2)
    {
        return 1;
    }

    //converts key to integer
    int key = atoi(argv[1]);

    //get plain text
    string plainText = get_string("Please enter plain text and press enter: ");

    //prints final strings
    printf (" Plain Text: %s\n", plainText);
    printf ("Cipher Text: ");

    //variables for loop
    int ascii = 0;
    char hold = 'a';

    //for loop that gets all charcters plus the key and converts to ascii
    for (int i = 0, n = strlen(plainText); i < n; i++)
    {
        //gets char seperate from rest of word
        ascii = (plainText[i]);

        //determines if figure is alphabet
        if ( isalpha(plainText[i]) )
        {
            //determines if alphabet is uppercase
            if ( isupper(plainText[i]) )
            {
                //adds key to ascii
                ascii += key;

                //determines if it exceeds the uppercase range
                while (ascii > 90 )
                {
                    //puts it back in range
                    ascii -= 90;
                    ascii += 64;
                }

                //puts it back in to character
                hold = ascii;

                //print cipher
                printf("%c", hold);

            }else if ( islower(plainText[i]) ){        //checks to see if it is lower case
                //adds key to ascii
                ascii += key;

                //determines if it exceeds the uppercase range
                while (ascii > 122)
                {
                    //puts it back in range
                    ascii -= 122;
                    ascii += 96;
                }

                //puts it back in to character
                hold = ascii;

                //print cipher
                printf("%c", hold);

            }
        }else {
            printf (" ");
        }

    }

    //get new line
    printf("\n");

    return 0;
}
