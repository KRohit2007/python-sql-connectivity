# python-sql-connectivity
'''demonstartes python-sql connectivity-fetchall()'''
#select query
#sql connectivity with python
#get all the records in one time
import Mysql.connector as cnMySQL
from mysql.connector import Error,errorcode
myHostName='localhost'
myDatabaseName='dbschool'
myDbUserId='root'
myDbPassword='Rohitk2007'

try:
    # create connection with database
    myconnection= cnMySQL.connect(host=myHostName,
                                  database=myDatabaseName,
                                  user=MyDbUserId,
                                  password=myDbPassword,
                                  use_pure= true)
    if myConnection.is_connected():
        print("Successfully connected to Database")
    #create cursor
    myCursor= myConnection.cursor(buffered=True)
    #Sql query
    mySql_query= """select
                          *
                          from 
                          studentdet;
                 """
    #execute query at server
    mycursor.execute(mySql_query)
    #get result of query,return list of tuples where tuple is created
    Result= mycursor.fetchall()
    #print each record
    for eachrow in Result:
        print(eachrow)
        
    mycursor.close()
except Error as error:
    print("Error:{}".format(error))
finally:
    if(myConnection.is_connecetd()):
        myconncetion.close()
        print("MySql connection is closed")
