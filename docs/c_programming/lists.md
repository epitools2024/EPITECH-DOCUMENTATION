**Simply linked lists**

We therefore call ``chained list`` or more simply ``list``,
a data structure made of elements
each containing :

* payload data or a reference (address or pointer) to
* useful data ;
a reference (address or pointer) to the next element.

A linked list is a data structure representing an ordered
representing an ordered collection of elements of arbitrary size.
arbitrary size of elements.
The access to the elements of a list is done in a
sequentially
An element contains an access to a data.

***Guidelines***

The principle of the chained list is that each element
has, in addition to the data, pointers to the
elements which are logically adjacent to it in the
list.

(Image)

* first(L) designates the first element of the list
* null designates the absence of element, thus an empty list
* simply chained list
* data(elt) designates the data associated with the elt element
* next(elt) is the element following the elt element

***List initialization***

It is enough to assign the value ``NULL`` to the variable representing
the head of the list.
The head of the list is represented by a pointer to the
first element of the list.

***List operations***

* Browse the list
* Adding an item
* Deleting an item
* search for a data item
* replacing, concatenating a
list
* merging lists, etc.


***Definitions***

```C
struct list_entier {
    int val;
    struct list_entier *next;
};
...
struct list_entier *head=NULL;
```

***Creation of element***

This operation can, a priori, be divided into two steps:
* obtaining a memory zone for the representation of the
the element;
* inserting this element into a particular list, at the desired
the desired location.

```C
struct list_entier *elem_new (int val)
{
    struct list_entier *new;
    new = (struct list_entier *)malloc (sizeof(struct list_entier));

    if (new == NULL)
        exit (0);
    else {
        new->val = val;
        new->next = NULL;
        return new;
    }
}
```

***Free the space occupied by an element***

```C
void elem_free (struct list_entier *elem)
{
    free(elem);
}
```

***Access to an element***

* The first element of a list is directly accessible through the pointer that
the pointer that represents the list;
* The second element is only accessible from the pointer that is in the
The second element is accessible only from the pointer that is in the first element;
* The access to the element of rank n requires to browse the first n - 1
The second element is accessible only from the pointer in the first element;
* This behavior is quite different from that of
arrays.

***Inserted at the top of the list***

It is relatively simple to insert an element at the top of a
list. It is sufficient that the old "head" of the list becomes the
next to the inserted element, and that this element becomes the
new list head.

***Insert an element at the top***

```C
struct list_entier * list_push (struct
list_entier * L, struct
list_entier *elt)
{
    elt->next = L;
    return elt;
}
...
head = list_push(tete,elem_new(12));
```

***Insert an element after a P element***

```C
void list_insert (struct list_entier *p, struct list_entier *elt);
```

***Insert in "tail" of list***

```C
struct list_entier * list_append(struct list_entier *L, struct list_entier * elt);
```

***List length***

```C
int taille_list (struct list_entier *L)
{
    int len = 0;
    struct list_entier *cur = L;

    while (cur != NULL) {
        cur = cur->next;
        len++;
    }
    return len;
}
```
***Displaying the contents of a list***

```C
void list_print(struct list_entier *L);
```

**Double-chained list**

(Image)

***List operations***

* Browse the list
* Adding an item
* Deleting an item
* search for a data item
* replacing, concatenating a
list
* merging lists, etc.

***Definitions***

```C
struct node
{
    int data; //data associated with the element
    struct node *p_next; //designate the next element
    struct node *p_prev; //designates the previous element
};
 ```
 This first structure will allow us to
represent an element of the chained list.

To represent our double-chained list properly, we will use a second
structure as follows:

```C
typedef struct dlist
{
    int length;
    struct node *p_tail;
    struct node *p_head;
} Dlist;
```

p_head will point to the first element of our list
while p_tail will point to the last element. Thus,
we will keep permanently a pointer to the beginning and a pointer to the end of the
and a pointer to the end of the list.

***Creation of an empty double
chained list***

```C
Dlist * dlist_new()
{
    Dlist * p_new;
    p_new = malloc(sizeof (*p_new));// p_new = malloc(sizeof (Dlist));

    if (p_new != NULL) {
        p_new->length = 0;
        p_new->p_head = NULL;
        p_new->p_tail = NULL;
    }
    return p_new;
}
```

***Add an item at the end of the list***

```C
Dlist * dlist_append(Dlist *p_list, int data);
```

***Add an item at the beginning of the
list***

```C
Dlist * dlist_append(Dlist *p_list, int data);
```
***Deletion of an element from the list according to its
value***

```C
Dlist * dlist_remove(Dlist *p_list, int data);
```

***Free a list***

After using our list, we have to free all the elements allocated by our functions
allocated by our functions, otherwise we will get what is called a memory leak.
memory leaks.

```C
void dlist_delete(Dlist **p_list)
{
    if (*p_list != NULL) {
        struct node *p_temp = (*p_list)->p_head, *p_del;
        while (p_temp != NULL) {
            p_del = p_temp;
            p_temp = p_temp->p_next;
            free(p_del);
        }
        free(*p_list);
    }
}
```