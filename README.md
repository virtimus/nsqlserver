nSQLServer
==========



nSQLServer project is a result of some research on possibilities to access different databases in unique form using kind of "Database Hub" or "Proxy"

It's compilation of two projects: - a MongoDB fork (slightly extended MongoDB version by some "nSQL" commands) - a fork of SQLRelay project (relational DB proxy handling many SQL backends)


Currently it is in a pre-prototype stage. 
I'm now working on making MongoDB understand something which would be "close" to SQL - I've named it "nSQL" - it's json based dialect of SQL operating on hierachical collections

https://github.com/virtimus/nsqlserver

It's a work in progress - nothing yet there committed - however I have already offline w protype version which processes simple nSQL queries of the form:

  db.runCommand(
    {nsQL:
        {
           sel:['id','emailUse','emailType','emailSubject'],    // properties/colums to return
           flt:{emailUse:0,emailType:'test'},           // filter (where phrase equivalent)
           ctb:'wp_eshop_emails'                // table equivalent (can be agregated in collection as path)
        },
        cid:ci,                         //connection id
        sid:si                          //session id
    })

It can work on both MySQL, MongoDB or almost any other Relational/non relational backend 

Above component would be the main part of work. There is a lot of development to make it fully functional (handling of aggregations, sorting, subdocument filters, inserts/updates/deletes, maybe also joins etc) End effect seems to be very promissing in general. 

Imagine for instance SQL to NoSQL migration using several simple "INSERT FROM INTO" commands ...

The rest of work would be to connect it with client applications - neither through native API or some sort of SQL2NSQL translator.

Is there someone interested in speeding up the project? Help in analysis/development ? Financial donating ?
