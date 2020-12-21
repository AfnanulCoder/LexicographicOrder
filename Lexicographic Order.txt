#include<stdio.h>

struct Student {
    char name[100];
    int id;
    float cgpa;
};


mergeSort(struct Student a[],int p,int r)
{
    int q;

    if(p<r)
    {
        q = (int)((p+r)/2);
        mergeSort(a, p, q);
        mergeSort(a, q+1, r);
        merge(a, p, q, r);
    }
}


merge(struct Student a[], int p, int q, int r)
{
    int n1 = q-p+1, n2 = r-q, i = 0, j = 0, k = p, c = 0;
    struct Student l[n1+1], ri[n2+1];

    for(i=0;i<n1;i++)
    {
        strcpy(l[i].name, a[p+i].name);
        l[i].id = a[p+i].id;
        l[i].cgpa = a[p+i].cgpa;
    }
    
    for(j=0; j<n2; j++)
    {
        strcpy(ri[j].name, a[q+j+1].name);
        ri[j].id = a[q+j+1].id;
        ri[j].cgpa = a[q+j+1].cgpa;
    }
        

    l[n1].name[0] = 'z'+1;
    ri[n2].name[0] = 'z'+1;
    
    
    // for(i=0; i<n1+1; i++)
    // {
    //     printf("%d. %s\n", i,  l[i].name);
        
    // }
    
    // for(i=0; i<n2+1; i++)
    // {
    //     printf("%d. %s\n", i, ri[i].name);
        
    // }
    
    
    

    i=0;
    j=0;
    

    for(k=p; k<=r; k++)
    {
        c=0;
        while(l[i].name[c] == ri[j].name[c])
        {
            c++;
        }
        
        
        
        if(l[i].name[c] <= ri[j].name[c])
        {
            strcpy(a[k].name, l[i].name);
            a[k].id = l[i].id;
            a[k].cgpa = l[i].cgpa;
            i++;

        }
        else
        {
            strcpy(a[k].name, ri[j].name);
            a[k].id = ri[j].id;
            a[k].cgpa = ri[j].cgpa; 
            j++;

        }

    }
        
}



main()
{
    
    
    
    int size, i;
    printf("Number of Students:  ");
    scanf("%d", &size);

    int a[size];
    struct Student std[size];

    printf("\nEnter You array:  \n");

    for(i=0; i<size; i++)
    {
        printf("Name:  ");
        scanf("%s", &std[i].name);
        printf("ID:  ");
        scanf("%d", &std[i].id);
        printf("CGPA:  ");
        scanf("%f", &std[i].cgpa);
    }
        
    printf("\n\nYour array:  \n\n");
    for(i=0; i<size; i++)\
    {
        printf("Name:  %s\n", std[i].name);
        printf("ID:  %d\n", std[i].id);
        printf("CGPA:  %f\n\n\n", std[i].cgpa);
    }
        // printf("%d    ", a[i]);


    mergeSort(std, 0, size-1);

    printf("\n\nYour Sorted Array:  \n\n");
    for(i=0; i<size; i++)
    {
        printf("Name:  %s\n", std[i].name);
        printf("ID:  %d\n", std[i].id);
        printf("CGPA:  %f\n\n\n", std[i].cgpa);
    }     

     printf("\n");
}
