# ceaser-cipher-
#include <stdio.h>
#include <string.h>
#include <stdbool.h>

int ENCR()
{
    char plain[100], ch;
    int key, i;

    printf("\nEnter PLAIN text: ");
    getchar();
    fgets(plain, sizeof(plain), stdin);
    plain[strcspn(plain, "\n")] = '\0';

    printf("\nEnter KEY value: ");
    scanf("%d", &key);

    for (i = 0; i < strlen(plain); i++)
    {
        ch = plain[i];

        if (ch >= 'A' && ch <= 'Z')
        {
            plain[i] = ((ch - 'A' + key) % 26) + 'A';
        }
        else if (ch >= 'a' && ch <= 'z')
        {
            plain[i] = ((ch - 'a' + key) % 26) + 'a';
        }
    }

    printf("ENCRYPTED text: %s\n", plain);
    return 0;
}

int DECR()
{
    char plain[100], ch;
    int key, i, m;

    printf("Enter ENCRYPTED text: ");
    getchar();
    fgets(plain, sizeof(plain), stdin);
    plain[strcspn(plain, "\n")] = '\0';

    printf("Enter KEY value: ");
    scanf("%d", &key);

    for (i = 0; i < strlen(plain); i++)
    {
        ch = plain[i];

        if (ch >= 'A' && ch <= 'Z')
        {
            m = ch - 'A';
            if (m < 0)
            {
                m += 26;
            }
            plain[i] = (((m - key) + 26) % 26) + 'A';
        }
        else if (ch >= 'a' && ch <= 'z')
        {
            m = ch - 'a';
            if (m < 0)
            {
                m += 26;
            }
            plain[i] = (((m - key) + 26) % 26) + 'a';
        }
    }

    printf("DECRYPTED text: %s\n", plain);
    return 0;
}

int main()
{
    int a;
    char c[2];

    while (true)
    {
        printf("\nENTER 1:ENCRYPTION 2:DECRYPTION: ");
        scanf("%d", &a);

        if (a == 1)
        {
            ENCR();
        }
        else if (a == 2)
        {
            DECR();
        }
        else
        {
            break;
        }

        printf("\nDo you want to continue? (y/n): ");
        getchar();
        scanf("%c", &c);

        if (c[0] != 'y' && c[0] != 'Y')
        {
            break;
        }
    }

    return 0;
}
