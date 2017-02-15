##Creating a theatre application with the following specifications: 

A client of LaunchPad Lab is opening a movie theater. We need you to build a Rails app so they can start selling tickets online.

Customers should be able to come to the site and see all movies playing with their showtimes. Seating is limited for each theater so a particular showtime should only have a limited number of seats. Once a show sells out, a customer should no longer be able to buy tickets. Customers should only be able to buy one ticket at a time so don't worry about a shopping cart for this version.

When customers decide to buy their ticket, they should be able to checkout by entering their name, email, credit card, and expiration date. We want to make sure we don't get any bogus orders, so please keep an eye out for any validations and make sure the user knows if there's a problem with the order. We'll add a credit card processor later on, so you DON’T need to integrate with a credit card processor. Once the customer purchases their tickets, they should receive an email receipt.

The theater owner needs a way to manage the movies playing and seating capacities . She should be able to add auditoriums and seating capacities. In addition, the movies change all the time so our client should be able to set which movie is showing in which auditorium.

The theater owner also wants to keep track of her sales, so the order information should be saved to the database. She wants to see a list of all orders and a list of orders for each movie. We don't need any authentication on the app for now.

We're not worried about custom visual design, so feel free to use any CSS framework, or roll your own. However, we need the site to work on mobile, so keep that in mind.

##My thought process:
I initially broke everything down into pieces, and started formatting the database. I didn't need users, only 1 owner for the site so I think making a login for that person is the only user model needed. 

A theatre can have many auditoriums, but the auditoriums belong to that specific theatre so I set up a one to many relationship on that. Additionally, added a max seats to the auditorum for checking if any seats available. 

The next thing I had to deal with was movies. Auditoriums can have many movies, and a movie can be show in different auditoriums. I set up a many to many with a join table called showings. I believe this is effective because then the showtime can be put on the showings table, and the movie itself will just need its name and runtime. 

Tickets was next on the list. Since I'm not using users, i think it would be best to associate each created ticket with the purchaser, so I gave it the properties of customer name and their email. The price of the ticket as well, and finally linking the ticket itself to a particular showing. So now the ticket has access to its show time and which auditorium it is in. So when checking the seat count, I can count the number of tickets for a showing, and compare that to the auditoriums max seat attribute.