# Git Intro Project

// #ifndef LISTS_H
// #define LISTS_H

/*
 ** File: lists.h
 ** Auth: Brennan D Baraban
 ** Desc: Header file containing prototypes and definitions for all functions
 **       and types written in the 0x11-singly_linked_lists directory.
 */

// #include <.....h>

/**
 ** struct list_s - singly linked list
 ** @str: string - (malloc'ed string)
 ** @len: length of the string
 ** @next: points to the next node
 *
 ** Description: singly linked list node structure
 **              for Holberton project
 */
typedef struct list_s
{
        char *str;
        unsigned int len;
        struct list_s *next;
} list_t;

size_t print_list(const list_t *h);
size_t list_len(const list_t *h);
list_t *add_node(list_t **head, const char *str);
list_t *add_node_end(list_t **head, const char *str);
void free_list(list_t *head);

#endif



// #include "lists.h"
// #include <......h>

/**
 ** print_list - Prints all the elements of a list_t list.
 **@h: The list_t list.
 **
 ** Return: The number of nodes in h.
 */

size_t print_list(const list_t *h)
{
        size_t n = 0;

        while (h)
        {
                if (h->str == NULL)
                        printf("[0] (nil)\n");

                else
                        printf("[%d] %s\n", h->len, h->str);

                n++;
                h = h->next;
        }
        return (n);
}


// #include "lists.h"

/**
 ** list_len - Finds the number of elements in
 **            a linked list_t list.
 ** @h: The linked list_t list.
 *
 ** Return: The number of elements in h.
 */
size_t list_len(const list_t *h)
{
        size_t e = 0;

        while (h)
        {
                e++;
                h = h->next;
        }
        return (e);
}



// #include "lists.h"
// #include <.....h>

/**
 ** add_node - Adds a new node at the beginning
 **            of a list_t list.
 ** @head: A pointer to the head of the list_t list.
 ** @str: The string to be added to the list_t list.
 *
 ** Return: If the function fails - NULL.
 **         Otherwise - the address of the new element.
 */
list_t *add_node(list_t **head, const char *str)
{
        char *dup;
        int len;
        list_t *new;

        new = malloc(sizeof(list_t));
        if (new == NULL)
                return (NULL);

        dup = strdup(str);
        if (dup == NULL)
        {
                free(new);
                return (NULL);
        }

        for (len = 0; str[len];)
                len++;

        new->str = dup;
        new->len = len;
        new->next = *head;

        *head = new;

        return (new);
}




// #include "lists.h"
// #include <.....h>

/**
 ** add_node_end - Adds a new node at the end
 **                of a list_t list.
 ** @head: A pointer the head of the list_t list.
 ** @str: The string to be added to the list_t list.
 *
 ** Return: If the function fails - NULL.
 **         Otherwise - the address of the new element.
 */
list_t *add_node_end(list_t **head, const char *str)
{
        char *dup;
        int len;
        list_t *new, *last;

        new = malloc(sizeof(list_t));
        if (new == NULL)
                return (NULL);

        dup = strdup(str);
        if (str == NULL)
        {
                free(new);
                return (NULL);
        }

        for (len = 0; str[len];)
                len++;

        new->str = dup;
        new->len = len;
        new->next = NULL;

        if (*head == NULL)
                *head = new;

        else
        {
                last = *head;
                while (last->next != NULL)
                        last = last->next;
                last->next = new;
        }

        return (*head);
}




// #include "lists.h"
// #include <......h>

/**
 ** free_list - Frees a list_t list.
 ** @head: A pointer to the list_t list.
 */
void free_list(list_t *head)
{
        list_t *tmp;

        while (head)
        {
                tmp = head->next;
                free(head->str);
                free(head);
                head = tmp;
        }
}
