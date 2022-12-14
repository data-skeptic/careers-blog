Nearly all aspiring data scientists end up dealing with CSV files as a source of data.  Thanksfully, many resources exist in most languages to load and write CSV files, saving you the annoyances of re-implementing logic for handling quote encapsulated data and other of the complexities of loading a CSV file.

There's something truly wonderful about comma separated value files.  Any computer user should be able to open the file and understand it's contents.  Tools like Excel and Google Sheets can easily import them.  When you need to write a custom script to process a CSV, that's straightforward to.  CSV is a truly robust, accessible format.  Yet its not without drawbacks.

CSV files lack any way to store metadata, such as the data type of a column (e.g. integer or dates).  They have no built in compression, so the files are often unnecessarily large.  CSV processing tools need to load the entire file before you can use the data, unless you build something custom.  If you only need the first row of a file, that's a huge waste.

For these and many other reasons, most data scientists taking on newer and bigger challenges will eventually encounter Parquet files.

Parquet is a columnar storage format for storing data in a tabular format. It is often used in the context of data analytics and is well-suited for use cases that involve large datasets. There are several reasons why a data scientist might choose to use parquet, including:

It is a columnar storage format, which means that data is stored in a way that is optimized for reading and writing columns of data, rather than rows. This can make queries that access only a subset of the columns in a table much faster, since only the needed columns need to be read from disk.  Software can intelligently "skip over" reading the parts of the file that aren't required.

In almost all cases, Parquet files will be much smaller than CSV files. Because parquet is a columnar storage format, it can store data more densely than row-based formats like CSV. This means that it can often compress data to a smaller size on disk, which can save on storage costs and improve performance when working with large datasets.  The compression of the data applies to how it is stored, not to privacy.  There is no cost to un-compress the data.  The compression simply reduces storage of redudant data in a way which lookups can be fast and still have the correct result.

Parquet is self-describing. This means that the schema for a parquet file is stored within the file itself, so it can be read and understood without any external metadata. This can make it easier to share parquet files with others, since the schema is embedded within the file.  When loading the data, the library you use can leverage this metadata to provide you appropriately typed fields, rather than storing everything initially as strings.

It is supported by a wide range of tools and technologies. Because parquet is a popular format for storing data in the context of data analytics, it is supported by many different tools and technologies, including Apache Spark, Apache Drill, and Apache Impala. This means that data scientists can use parquet with a variety of different tools and technologies to analyze their data.

While Parquet was developed with tabular data in mind, it has efficient support for nested data. Parquet is designed to support nested data structures, which are common in many big data use cases. This means that data scientists can use parquet to store and analyze data that has a complex, hierarchical structure without losing any of the performance benefits of a columnar storage format.

If your organization's datasets fit cleanly into the memory of your computer, most would agree you work on small data.  There's nothing wrong with that.  However, as you take on problems of scale and big data, you'll need better solutions than CSV files.  Parquet is a tool you should become familiarly with to help you manage data as you advance your career.

