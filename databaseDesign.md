# Database Design

## Database Planning
     - TicketsTable
      * ID
      * ConcertID           // references the concerts table
      * TicketHolderID      // don't keep everything in one table

     - TicketHolderTable
      * ID
      * firstName
      * lastName
      * email

     - ConcertsTable
      * ID
      * Date
      * city
      * state
      * venue

> create seperate tables for related data.
> removing repeated data; moving data to different tables and replacing the data in the original table  with an ID, is called **Normalization**
