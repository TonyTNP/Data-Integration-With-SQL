# Data-Integration-With-SQL

-- Task 1: Combine customer and invoice data.
-- #Records = 384  / #NULL = no
SELECT
    Customer.CustomerId,
    Customer.LastName,
    Invoice.InvoiceId
FROM Customer
JOIN Invoice ON Customer.PostalCode = Invoice.BillingPostalCode;

-- Task 2: Explore LEFT JOIN
-- #Records = 388  / #NULL = yes (InvoiceId)
SELECT
    Customer.CustomerId,
    Customer.LastName,
    Invoice.InvoiceId
FROM Customer
LEFT JOIN Invoice ON Customer.PostalCode = Invoice.BillingPostalCode;

-- Task 3: Explore RIGHT JOIN
-- #Records = 412  / #NULL = yes (CustomerId, LastName)
SELECT
    Customer.CustomerId,
    Customer.LastName,
    Invoice.InvoiceId
FROM Customer
RIGHT JOIN Invoice ON Customer.PostalCode = Invoice.BillingPostalCode;

-- Task 4: Explore FULL OUTER JOIN
-- #Records = 416  / #NULL = yes (any column containing NULL)
SELECT
    Customer.CustomerId,
    Customer.LastName,
    Invoice.InvoiceId
FROM Customer
FULL OUTER JOIN Invoice ON Customer.PostalCode = Invoice.BillingPostalCode;
