# phone-keyboard-lader
#include <iostream>
#include <cstring>
using namespace std;
//-----------------------------------------------------------------------
// phone-keyboard[i] a 2d array that carry numbers of phone and its alphabet
const char Phonekeyboard[10][5] = {"", "", "ABC", "DEF", "GHI", "JKL","MNO", "PQRS", "TUV", "WXYZ"};
//------------------------------------------------------------------------
//unique word is a func that combine a first letter of the first num choice with the other nums
void  uniqueword(int number[], int worddigit, char output[], int s)
{
    //to see if the function collect the word and prepared
    int i;
    if (worddigit == s)
    {
        cout << output << "||" ;
        return ;
    }

    // Try all 3 possible combinations with recursive properties
    for (i=0; i<strlen(Phonekeyboard[number[worddigit]]); i++)
    {
        output[worddigit] = Phonekeyboard[number[worddigit]][i];
        uniqueword(number, worddigit+1, output, s);
        if (number[worddigit] == 0 || number[worddigit] == 1)
            return;
    }
}

//this function collect words in an array of chars to make a beautiful shape for print
void print_all_words(int number[], int s)
{
    char result[s+1];
    result[s] ='\0';
    uniqueword(number, 0, result, s);
}

int main()
{
    //numbers that user press
    int number[] = {7,2,3};
    //to calculate array size
    int s = sizeof(number)/sizeof(number[0]);
    print_all_words(number, s);
    return 0;
}
