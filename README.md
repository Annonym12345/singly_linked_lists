# Git Intro Project

// #ifndef LISTS_H
// #define LISTS_H

/*
 ** File: lists.h
 ** Auth: Brennan D Baraban
 ** Desc: Header file containing prototypes and definitions for all functions
 **       and types written in the 0x11-singly_linked_lists directory.
 */

// #include <stdlib.h>

/**
 ** struct list_s - singly linked list
 ** @str: string - (malloc'ed string)
 ** @len: length of the string
 ** @next: points to the next node
 *
 ** Description: singly linked list node structure
 *              for Holberton project
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
// #include <stdio.h>

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


#include "lists.h"

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
