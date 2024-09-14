# SnowFlake-Streaming
SnowFlake-Streaming
![image](https://github.com/user-attachments/assets/72ef2e08-a4c3-47d5-a4fb-d9ccac7ceaba)


![image](https://github.com/user-attachments/assets/b81a82ab-bdaf-4f35-b60c-b2f9e7913205)


![image](https://github.com/user-attachments/assets/40172f2a-299a-4aca-a931-b8bf110e1207)


![image](https://github.com/user-attachments/assets/e1342aa5-2c00-4eeb-8234-44bb64d1a59e)


![image](https://github.com/user-attachments/assets/b31bedd0-ba90-4724-a19f-992c22d8c2ce)

![image](https://github.com/user-attachments/assets/e9304b89-51a7-4d22-9c6d-479460c9ebb3)


Still records did not come to final table. We need to consume the stream in to final table

![image](https://github.com/user-attachments/assets/37511d7a-3395-4145-8708-9862eb9a405a)


After consumption, stream is empty

![image](https://github.com/user-attachments/assets/a1cf7491-5072-4ca3-b080-a609dabe1489)

But values added to final table from stream


![image](https://github.com/user-attachments/assets/bae5e77e-e6ec-4cac-9397-4fac61edb8e8)


Updating data and checking changes reflecting in result table




![image](https://github.com/user-attachments/assets/eb98af1c-3d9e-4dae-a349-dbab975ba139)

You will see 2 entries. delete and insert

![image](https://github.com/user-attachments/assets/e3f8a4ea-a60e-4b51-9a65-6216c091c8a0)

To get update entry in final table, use merge statement like below

merge into SALES_FINAL_TABLE F      -- Target table to merge changes from source table
using SALES_STREAM S                -- Stream that has captured the changes
   on  f.id = s.id                 
when matched 
    and S.METADATA$ACTION ='INSERT'
    and S.METADATA$ISUPDATE ='TRUE'        -- Indicates the record has been updated 
    then update 
    set f.product = s.product,
        f.price = s.price,
        f.amount= s.amount,
        f.store_id=s.store_id;
You can see banana is updated with potato in final table using merge

![image](https://github.com/user-attachments/assets/7996396c-747c-4804-83fc-37611905f523)


Handling delete in stream

![image](https://github.com/user-attachments/assets/cb058918-c145-4cf8-877b-61b39ce5101d)

![image](https://github.com/user-attachments/assets/4d7a45d6-2ad1-4057-aad6-58ab0d0497c3)

![image](https://github.com/user-attachments/assets/7ca9b712-d05e-443d-b6f6-b6a84a0fc125)


Multiple operations together

![image](https://github.com/user-attachments/assets/7eca6e18-9988-4802-806e-e7f9af18c630)








        










