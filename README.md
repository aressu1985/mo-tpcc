# mo-tpcc
how to run TPCC：
1.https://github.com/aressu1985/mo-tpcc

2、create database and tables
  create database tpcc;
  use tpcc;
  execute mo-tpcc/sql/tableCreates_pk.sql
  or
  source /path/to/mo-tpcc/sql/tableCreates_pk.sql; 

3、generate tpcc data
   mkdir data
   ./runLoader.sh props.mo warehouse X filelocation data/
   
   X means the num of warehouse

4、load data
load data infile '/path/to/mo-tpcc/data/config.csv' into table bmsql_config;
load data infile '/path/to/mo-tpcc/data/cust-hist.csv' into table bmsql_history;
load data infile '/path/to/mo-tpcc/data/customer.csv' into table bmsql_customer;
load data infile '/path/to/mo-tpcc/data/district.csv' into table bmsql_district;
load data infile '/path/to/mo-tpcc/data/item.csv' into table bmsql_item;
load data infile '/path/to/mo-tpcc/data/new-order.csv' into table bmsql_new_order;
load data infile '/path/to/mo-tpcc/data/order-line.csv' into table bmsql_order_line;
load data infile '/path/to/mo-tpcc/data/order.csv' into table bmsql_oorder;
load data infile '/path/to/mo-tpcc/data/stock.csv' into table bmsql_stock;
load data infile '/path/to/mo-tpcc/data/warehouse.csv' into table bmsql_warehouse;

5、modify props.mo
  warehouse=X, X is the num of warehouse
  terminals=X, X is the num of terminals that will simultaneously run
  runMins the time that the test will run
6、./runBenchmark.sh props.mo
