# sql-queries-
# UPDATE QUERY:

    update stores_newuser set eligible_sub_forms= eligible_sub_forms || ',1266' where user_id=9325892
--------------------------------------------------------------------------------------------------------------------------------

# How to use CAST or CONVERT:

    SELECT CAST(YourVarcharCol AS INT) FROM Table
    SELECT CONVERT(INT, YourVarcharCol) FROM Table
--------------------------------------------------------------------------------------------------------------------------
# Adding column to existing table:

    ALTER TABLE party_master
    ADD COLUMN partyname_maithili varchar(255) ;
-------------------------------------------------------------------------------------------------------------------------------------
# Update query column1 data to column2 in same table:



    UPDATE party_master 
    SET partyname_telugu =(select partyname_english from party_master );
---------------------------------------------------------------------------------------------------------------------------------- 
# copy column data from table1 to table2:

   Insert into assembly_master_mpstate  
   (city_id,city_name) 
   Select can_no, can_name from `madhyapradesh_2018_positionwise _result`
-----------------------------------------------------------------------------------------------------------------------------------------
# update query column in table1 with column in table2:

    UPDATE const_assembly_statewise_mp AS t1, (SELECT const_name data FROM const_master_statewise_mp ) AS t2 SET t1.const_name=t2.data
-----------------------------------------------------------------------------------------------------------------------------------------------
# insert query
    insert into statewise_party_candidate_mp 
    SELECT pcs 
    as parliamentary_constituency, can_no as assembly_id  ,
     can_name as assembly_name, 
     party4 as party,candidate4 as candidatename FROM `madhyapradesh_2018_positionwise _result`;
--------------------------------------------------------------------------------------------------------------------

# create query:

     create table statewise_party_candidate_mp as
     SELECT pcs as parliamentary_constituency, 
     can_no as assembly_id  ,
    can_name as assembly_name, party1 as party,
    candidate1 as candidatename   
    FROM `madhyapradesh_2018_positionwise _result`;

-----------------------------------------------------------------------------------------------------------------------------------------------------
# Replace:

    UPDATE statewise_party_candidate_mp SET parliamentary_constituency = REPLACE(`parliamentary_constituency`, '3-', '')

    UPDATE statewise_party_candidate_mp SET parliamentary_constituency = TRIM(parliamentary_constituency)
--------------------------------------------------------------------------------------------------------------------------------------------------------
# update col in table1 with col table2 where condition
          UPDATE statewise_party_candidate_mp  t1
           inner join  parliamentary_constituency_master  t2
                      
         on t1.parliamentary_constituency = t2.parliamentary_constituency
                      
         SET t1.constituency_id = t2.parlimentary_const_id 
---------------------------------------------------------------------------------------------------------------------------------------------------------
      create table statewise_party_candidateas
      SELECT Party1 as Party FROM election.position_wise_delhi_2015 ;

    insert into statewise_party_candidateas 
    SELECT Party2 FROM election.position_wise_delhi_2015;

    insert into party_dummy1 
     SELECT Party3 FROM election.position_wise_delhi_2015;

     insert into party_dummy1 
     SELECT Party4 FROM election.position_wise_delhi_2015;



# -------substr---


    update parliamentary_constituency_master_statewise
    set parliamentary_constituency = REPLACE(parliamentary_constituency,parliamentary_constituency,substr(parliamentary_constituency,4,length(parliamentary_constituency)))

------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
# current date and week back date query:

    select * from etvb_newsidea where ebs_dated>(ebs_dated-(60*60*24*7)) ORDER BY ebs_dated DESC

    select * from etvb_newsidea where ebs_dated> DATE_SUB(NOW(), INTERVAL 1 WEEK) ORDER BY ebs_dated DESC

     SELECT * FROM etvb_newsidea WHERE date(ebs_dated) = CURDATE()
-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
#  FIND_IN_SET():     (comma separated values in db field)  
    
    1)codeigniter:  $this->db->join("state_master","FIND_IN_SET(state_id,ebn_statewise)<>0",'inner');

     
    2)php: select *  from etvb_newsidea
       
    inner join state_master on FIND_IN_SET(state_id, ebn_statewise);  
                                         ex;5  , 1,2,5

    3)SELECT ebn_storyidea FROM etvb_newsidea WHERE ebn_statewise REGEXP "[[:<:]](4|14|10)[[:>:]]"


--------------------------------------------------------------------------------------------------------------------------
#  comparing only date with timestamp date:

    1)SELECT * FROM table WHERE DATE(timestamp) = '2012-05-05';
    2)SELECT * FROM table WHERE cast(timestamp as date) = '2012-05-05'
-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
# array to string format like implode:
 
   1) select group_concat('field_name') as names from tablename 
  
   2) select group_concat(field_name) as names from tablename

-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
# user creation like another user form eligibilities


update stores_newuser set eligible_sub_forms= eligible_sub_forms || ',1266' where user_id=9325892 










