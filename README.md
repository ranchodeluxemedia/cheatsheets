cheatsheets
===========

Various bits of info and text.



    Field -> Data Type
    -----    ---------
    Id       int
    Phone #  varchar
    Email    varchar
    Desc     varchar
    Name     varchar
    Ssn      varchar
    Price    decimal, money, smallmoney
    ShipDate datetime
    Sex      bit
    Discont  bit
    Quantity int
    ZipCode  varchar
    
---------------------

    def quid(price)
        number_to_currency(price, :unit => "£")
    end
    
Then call it in views:

    quid(line_item.price)
