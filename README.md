# Data-Integration-With-SQL

-- Task 1: Combine customer and invoice data.
-- #Records = 384  / #NULL = no
<!--
The Customer table contains NULL values in the PostalCode column. These records are excluded when using an INNER JOIN, resulting in 384 retrieved records (rows).
-->

SELECT
    Customer.CustomerId,
    Customer.LastName,
    Invoice.InvoiceId
FROM Customer
JOIN Invoice ON Customer.PostalCode = Invoice.BillingPostalCode;

-- Task 2: Explore LEFT JOIN
-- #Records = 388  / #NULL = yes (InvoiceId)

<!-- The LEFT JOIN will produce 388 records, including four customers without a PostalCode. This is because the LEFT JOIN retrieves all Customer table data and any matching InvoiceId's from the Invoice table. For those four customers without a matching BillingPostalCode, the InvoiceId value is NULL. -->

SELECT
    Customer.CustomerId,
    Customer.LastName,
    Invoice.InvoiceId
FROM Customer
LEFT JOIN Invoice ON Customer.PostalCode = Invoice.BillingPostalCode;

-- Task 3: Explore RIGHT JOIN
-- #Records = 412  / #NULL = yes (CustomerId, LastName)

<!-- The RIGHT JOIN retrieves all records from the Invoice table and any matching records from the Customer table. It will also include NULL values for CustomerIds and LastNames where there is no match in the Customer table. This is why the RIGHT JOIN returns 412 records, which includes records where the PostalCode from the Customer table is NULL. -->

SELECT
    Customer.CustomerId,
    Customer.LastName,
    Invoice.InvoiceId
FROM Customer
RIGHT JOIN Invoice ON Customer.PostalCode = Invoice.BillingPostalCode;

-- Task 4: Explore FULL OUTER JOIN
-- #Records = 416  / #NULL = yes (any column containing NULL)

<!--  The FULL OUTER JOIN returns all records from both tables, including matching and non-matching ones. In this instance, the FULL OUTER JOIN produced 416 records. -->

SELECT
    Customer.CustomerId,
    Customer.LastName,
    Invoice.InvoiceId
FROM Customer
FULL OUTER JOIN Invoice ON Customer.PostalCode = Invoice.BillingPostalCode;
