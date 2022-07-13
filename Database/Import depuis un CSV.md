#mysql #database #csv

LOAD DATA LOCAL INFILE 'geonames-postal-code@public.csv'  
    INTO TABLE akki_city  
    FIELDS TERMINATED BY ';'  
    ENCLOSED BY '"'  
    LINES TERMINATED BY '\n'  
    IGNORE 1 LINES  
    (@country_code, @postal_code, @place_name, @col4)  
    SET country_code = @country_code, postal_code = @postal_code, name = @place_name;