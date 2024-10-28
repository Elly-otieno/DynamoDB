# **Introduction to Amazon DynamoDB**
<br>

Amazon DynamoDB is a fast and flexible NoSQL database service for all applications that need consistent, single-digit millisecond latency at any scale. It is a fully managed database and supports both document and key-value data models. Its flexible data model and reliable performance make it a great fit for mobile, web, gaming, ad-tech, Internet of Things (IoT), and many other applications.

In this demo, we will create a table in DynamoDB to store information about a music library. We will query the music library and then delete the DynamoDB table.

## **Objectives**
<br>

In this demo we will:
- Create an Amazon DynamoDB table
- Enter data into an Amazon DynamoDB table
- Query an Amazon DynamoDB table
- Delete an Amazon DynamoDB table


## **Create a new table**
<br>

Here, we create a new table named **Music** in DynamoDB. Each table requires a partition key (or a primary key) that is used to partition data across DynamoDB servers. A table can also have a sort key. The combination of a partition key and sort key uniquely identifies each item in a DynamoDB table.

1. In the AWS Management Console, choose the  **Services** menu. Under **Database**, choose **DynamoDB**.

2. Choose **Create table**.

3. For the **Table name**, enter *Music*

4. For the **Partition key**, enter *Artist* and leave **String** selected in the dropdown list.

5. For **Sort key - optional**, enter Song and leave **String** selected.

    Our table will use the default settings for indexes and provisioned capacity.

6. Scroll down, and choose **Create table**.

    The table will be created in less than 1 minute. Wait for the **Music** table to be **Active** before moving on to the next task.

 

## **Add data**
<br>

Here, we will add data to the **Music** table. A table is a collection of data on a particular topic.

Each table contains multiple *items*. An item is a group of attributes that is uniquely identifiable among all of the other items. Items in DynamoDB are similar in many ways to rows in other database systems. In DynamoDB, there is no limit to the number of items we can store in a table.

Each item consists of one or more *attributes*. An attribute is a fundamental data element, something that does not need to be broken down any further. For example, an item in a **Music** table contains attributes such as song and artist. Attributes in DynamoDB are similar columns in other database systems, but each item (row) can have different attributes (columns).

When we write an item to a DynamoDB table, only the partition key and sort key (if used) are required. Other than these fields, the table does not require a schema. This means that we can add attributes to one item that may be different than the attributes for other items.

7. Choose the **Music** table.

8. Choose **Actions**, and then choose **Create item**.

9. For the **Artist** value, enter `Pink Floyd`

10. For the **Song** value, enter `Money`

    These are the only required attributes, but we now add additional attributes.

11. To create an additional attribute, choose **Add new attribute**.

12. In the dropdown list, select **String**.

    A new attribute row will be added.

13. For the new attribute, enter the following:

    - **FIELD**: `Album`
    - **VALUE**: `The Dark Side of the Moon`

14. To add another new attribute, choose **Add new attribute**.

15. In the dropdown list, choose **Number**.

    A new number attribute will be added.

16. For the new attribute, enter the following:

    - **FIELD**: `Year`
    - **VALUE**: `1973`

17. Choose **Create item**.

    The item has now been added to the Music table.

18. Similarly, to create a second item, use the following attributes:

    | Attribute Name | Attribute Type | Attribute Value |
    |----------------|----------------|-----------------|
    | Artist |	String | John Lennon |
    | Song |	String | Imagine |
    | Album |	String | Imagine |
    | Year |	Number | 1971 |
    | Genre |	String | Soft rock |

    This item has an additional attribute called **Genre**. This is an example of each item being capable of having different attributes without having to pre-define a table schema.

19. To create a third item, use the following attributes:

    | Attribute Name | Attribute Type | Attribute Value |
    |----------------|----------------|-----------------|
    | Artist | String | Psy |
    | Song | String | Gangnam Style |
    | Album | String | Psy 6 (Six Rules), Part 1 |
    | Year | Number | 2011 |
    | LengthSeconds | Number | 219 |

    Once again, this item has a new **LengthSeconds** attribute identifying the length of the song. This demonstrates the flexibility of a NoSQL database.

    There are also faster ways to load data into DynamoDB, such as using AWS Command Line Interface, programmatically loading data, or using one of the free tools available on the internet.

 

## **Modify an existing item**
<br>

Here, we will modify an existing item.

20. In the DynamoDB dashboard, under **Tables**, choose **Explore Items**.

21. Choose the  **Music** button.

22. Choose **Psy**.

    **Note**: Incase you can not see the **Music** table items that we added refresh the page.

23. Change the Year from 2011 to 2012.

24. Choose Save changes.

    The item is now updated. You can see that on the table items.

 

## **Query the table**
<br>

There are two ways to query a DynamoDB table: *query* and *scan*.

A query operation finds items based on the primary key and optionally the sort key. It is fully indexed, so it runs very fast.

25. Expand *Scan/Query items*, and choose *Query*.

    Fields for the Artist (Partition key) and Song (Sort key) are now displayed.

26. Enter the following details:

    - **Artist (Partition key)**: `Psy`
    - **Song (Sort key)**: `Gangnam Style`

27. Choose **Run**. 

The song quickly appears in the list. We might need to scroll down to see this result.

A query is the most efficient way to retrieve data from a DynamoDB table. 

Alternatively, we can scan for an item. This option involves looking through every item in a table, so it is less efficient and can take significant time for larger tables.

28. Scroll up on the page, and choose **Scan**.

29. Expand **Filters**, and enter the following values:

    - For **Attribute name**, enter `Year`
    - For **Type**, choose `Number`.
    - For **Value**, enter `1971`

30. Choose **Run**

Only the song released in 1971 is displayed.

 

## **Delete the table**
<br>

Here, we will delete the **Music** table, which will also delete all the data in the table.

31. In the DynamoDB dashboard, under **Tables**.

32. Choose the **Music** table if it is not already selected.

33. Choose **Actions**, and then choose **Update settings**.

34. Choose **Actions**, and then choose **Delete table**. 

35. On the confirmation panel, enter `confirm` and choose **Delete**.

The table will be deleted permanently. Remember this action cannot be undone.

 

## **Conclusion**
<br>

We now have successfully:

- Created an Amazon DynamoDB table
- Entered data into an Amazon DynamoDB table
- Queried an Amazon DynamoDB table
- Deleted an Amazon DynamoDB table

For more information about DynamoDB, see the [DynamoDB documentation](http://aws.amazon.com/documentation/dynamodb).


