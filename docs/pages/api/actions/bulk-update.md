---
permalink: bulk-update
---

## Definition

The Dapper Plus BulkUpdate method allow to UPDATE entities in a database table or a view.

## Bulk Update Entity

The Dapper Plus BulkUpdate method allow updating a single or multiple entities of the same type.

{% include template-example.html %} 
{% highlight csharp %}

//Update a single order.
connection.BulkUpdate(order);

//Update multiple orders.
connection.BulkUpdate(order1, order2, order3);
{% endhighlight %}

## Bulk Update IEnumerable<TEntity>

The Dapper Plus BulkUpdate method allow updating a single enumerable or multiple enumerable of entities of the same type.

{% include template-example.html %} 
{% highlight csharp %}

//Update a list of orders.
connection.BulkUpdate(orders);

//Update multiple list of orders.
connection.BulkUpdate(orders1, orders2, orders3);
{% endhighlight %}

## Bulk Update with "One to One" Relation

The Dapper Plus BulkUpdate method allow updating a related item with a "One to One" relation.

{% include template-example.html %} 
{% highlight csharp %}

//Update an order and the related invoice.
connection.BulkUpdate(order, order => order.Invoice);

//Update a list of orders and the related invoice to every order.
connection.BulkUpdate(orders, order => order.Invoice);
{% endhighlight %}

## Bulk Update with "One to Many" Relation

The Dapper Plus BulkUpdate method allow updating related items with a "One to Many" relation.

{% include template-example.html %} 
{% highlight csharp %}

//Update an order and all related items.
connection.BulkUpdate(order, order => order.Items);

//Update a list of orders and all related items to every order.
connection.BulkUpdate(orders, order => order.Items);
{% endhighlight %}

## Bulk Update with "Mixed" Relation

The Dapper Plus BulkUpdate method allow updating related item(s) with any relation.

{% include template-example.html %} 
{% highlight csharp %}

//Update an order, all related items, and the related invoice.
connection.BulkUpdate(order, order => order.Items, order => order.Invoice);

//Update a list of orders, all related items to every order, and the related invoice to every order.
connection.BulkUpdate(orders, order => order.Items, order => order.Invoice);
{% endhighlight %}

## Bulk Update Chain Action

The Dapper Plus BulkUpdate method allow chaining multiple bulk action methods.

{% include template-example.html %} 
{% highlight csharp %}

//Update an order and all related items. Update an invoice and all related invoice items.
connection.BulkUpdate(order, order => order.Items)
          .BulkUpdate(invoice, invoice => invoice.Items);

//Update a list of orders and all related items to every order. Update a list of invoices and 
//all related items to every invoice.
connection.BulkUpdate(orders, order => order.Items)
          .BulkUpdate(invoices, invoice => invoice.Items);

{% endhighlight %}

