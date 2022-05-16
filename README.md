User can create an order.
Firstly the mysql query select all the items from the database and display in the console if the item quantity is more than zero.
It also store the items in an array.
Now the user can type the ID of the song.
The user can type same id of the song.
It also checks the id validity.
Now the program shows the list of the items
After that the program can edit the list item by removing items from the list or buy the items.
When the program goes to buy function then two loops are execute.
There is a ‘If’ statement, that check is the given value is matching with the id of songs.
Then a mysql query is get the current quantity of the item in the database.
totalprice add the price of the items which are bought by the user.
Then the quantity calculation, in every purchase the quantity reduce of the respective item.
The update mysql query update the last calculated item quantity in the database.
Finally the result message and the total price pops up in the console.
Then the Exit Code executes.
