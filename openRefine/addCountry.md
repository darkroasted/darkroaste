# Add Longitude and Latitude to Dataset In Open Refine

1. Requirements:
- Data in open refine
- Column that contains a ISO2 or ISO 3 country name (ie: 'AF' or 'AFG' for afghanistan)

2. Click on the arrow above the country code column and select "Edit Column" -> "Add Column by fetching URLs..."
    ![Screenshot 2023-06-06 122422](https://github.com/darkroasted/darkroaste/assets/103026732/67372254-5996-4cba-8fe8-b47e4f3a5ad4)

3. Name the New column name: JSONData and add the following line into the expression
```
"https://nominatim.openstreetmap.org/search?q=" + value + "&format=json&limit=1"
```

![Screenshot 2023-06-06 122731](https://github.com/darkroasted/darkroaste/assets/103026732/f0e3015b-c52b-4700-b236-4fee088aaca9)

4. Click on OK, and the data will start to be generated. You need an internet connectio to do this!
    Wait for it to finish
    
    ![Screenshot 2023-06-06 122838](https://github.com/darkroasted/darkroaste/assets/103026732/c59e8747-48ac-4168-9ae6-0c8b0904582a)
  
    When it has finished there will be an extra column called JSONData
    
5. To get the Longitude and Latitude data from this JSONData we will be click on the arrow above json data and select "Edit Column" -> "Add column based on this column"

    ![Screenshot 2023-06-06 123054](https://github.com/darkroasted/darkroaste/assets/103026732/2df59fc5-6bcd-4a6c-8861-12afe8d2825f)

Then add the following expression 
```
value.parseJson()[0].lat
```
and call it lat. 

6. Do the same as in step 5 but then add the expression: 
```
value.parseJson()[0].lon 
```
and call it long.
