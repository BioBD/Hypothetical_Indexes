### Hypothetical Indexes in PostgreSQL
Hypothetical indexes are simulated index structures created solely in the database catalog. This type of index has no physical extension and, therefore, cannot be used to answer queries. The main benefit is to provide a means for simulating how query execution plans would change if the hypothetical indexes were actually created in the database. Thus this feature is useful for database tuners and DBAs.
Index selection tools, such as Microsoft’s SQL Server Index Tuning Wizard, make use of hypothetical indexes in the database server to evaluate candidate index configurations.
We have made some server extensions to PostgreSQL 9.3.6 to include the notion of hypothetical indexes in the system. We have introduced three new commands:

create hypothetical index <br />
drop hypothetical index <br />
explain hypothetical <br />

### Installing our solution
Our implementation of hypothetical indexes in PostgreSQL is intrusive. The installation of this version does not lead to additional steps. So you can follow the set of steps reported in the INSTALL file from the root folder of the PostgreSQL source code.

./configure <br />
gmake <br />
su <br />
gmake install <br />
adduser postgres <br />
mkdir /usr/local/pgsql/data <br />
chown postgres /usr/local/pgsql/data <br />
su - postgres <br />
/usr/local/pgsql/bin/initdb -D /usr/local/pgsql/data <br />
/usr/local/pgsql/bin/postgres -D /usr/local/pgsql/data >logfile 2>&1 & <br />
/usr/local/pgsql/bin/createdb test <br />
/usr/local/pgsql/bin/psql test <br />

### How to use
Our implementation of hypothetical indexes extend the commands create index, drop index and explain, so that we get new commands create hypothetical index, drop hypothetical index and explain hypothetical.
In general these commands specified were as follows:

CREATE HYPOTHETICAL index_name ON table_name (<cols>) <br />
DROP HYPOTHETICAL index_name <br />
EXPLAIN HYPOTHETICAL query_to_explain <br />

To view some examples of using see the wiki home page. 

