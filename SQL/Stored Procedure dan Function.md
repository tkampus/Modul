# Bagian 14: Stored Procedure dan Function

## Yang Akan Dibahas

Materi ini membahas stored procedure dan function sebagai logika SQL yang disimpan di database. Peserta akan melihat contoh function di PostgreSQL dan stored procedure di MySQL.

## Tujuan Pembelajaran

Setelah mempelajari materi ini, peserta diharapkan mampu:

1. Menjelaskan perbedaan umum function dan stored procedure.
2. Membuat function sederhana di PostgreSQL.
3. Membuat stored procedure sederhana di MySQL.
4. Memahami kapan logika SQL perlu disimpan di database.

Stored procedure dan function adalah logika SQL yang disimpan di database. Fitur ini berguna untuk proses yang sering diulang.

## 14.1 Contoh Function PostgreSQL

```sql
CREATE FUNCTION calculate_subtotal(quantity INT, unit_price DECIMAL)
RETURNS DECIMAL AS $$
BEGIN
    RETURN quantity * unit_price;
END;
$$ LANGUAGE plpgsql;
```

Menggunakan function:

```sql
SELECT calculate_subtotal(3, 50000);
```

## 14.2 Contoh Stored Procedure MySQL

```sql
DELIMITER //

CREATE PROCEDURE get_customers_by_city(IN city_name VARCHAR(50))
BEGIN
    SELECT *
    FROM customers
    WHERE city = city_name;
END //

DELIMITER ;
```

Menggunakan procedure:

```sql
CALL get_customers_by_city('Jakarta');
```

---
