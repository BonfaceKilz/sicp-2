# Hierarchical Data and Closure property

Main point of data abstraction is to separate
* the way how something is used from
* the way something is defined

In LISP we could have seen this on example of `cons` which is used as
container for pairs of arbitrary data, but is in fact defined as
procedure, and it could be defined in different ways which would not
change the way something is used.

LISP provides `pairs` as a mean of data abstraction. This data
abstraction provides `closure property` which means that you can make
more complex data by combining already combined data. For example, we
can make pair of pairs by using the same mean of combination (making `pairs`).
This way, we can build very complex data abstractions with simple mean
of combination provided by the language.

This is one of the essential questions about the means of combination in
some programming language. We should always ask

> Is this mean of combination closed over the set of primitive elements
of the langauge.

For example if you can not create array of arrays as in FORTRAN, then we
can not say that this language has `closure property` of this mean of
combination.

## Sequences

First, and most simple way to combine data is in the sequence. As the
ordered collection of data objects. Such ordered collection is called a
`list`.

One technique to walk through the list is `cdr-ing down` the list.
Other technique is to `cons up` the resulting list while `cdr-ing down`
given input list.

### Mapping over lists

One of basic operations is to apply certain transformation to all
elements of the list.

Introducing `map` abstraction is very good example of how adding layers
of abstraction moves our thining into different directions. If we take
example of scaling list of items as 

  (define (scale-elements items factor)
    (if (null? items)
      nil
      (cons (* (car items) factor) (scale-elements (cdr items) factor))))

and with map abstraction with

  (define (scale-elements items factor)
    (map (lambda (x) (* x factor))
         items))

we can see that in second case we don't have to think about the details
of impemenatation of scale-elements procedure since map is well
understood abstaraction which stands in front of all the details of
implementation.


