# ** reversed **

```
#include <stdio.h>

int main()
{
    char a[20],b[20];
    int i,c;
    printf("enter your Character:");
    gets(a);
    for(i=0;i<a[i]!='\0';i++);
    	c=i-1;
    for(i=0;a[i]!='\0';i++)
    {
        b[c-i]=a[i];
    }
    b[i]='\0';
    for(i=0;b[i]!='\0';i++)
    {
        a[i]=b[i];
    }
    a[i]='\0';
    printf("\n reversed: %s",a);
}
```
