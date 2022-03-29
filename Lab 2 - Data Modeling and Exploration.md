![Microsoft Power Platform.](Images/powerbi-welcome.png 'Microsoft Power Platform')

# Lab 2 - Data Modeling and Exploration

**Contents** 

<!-- TOC -->

- [Introduction](#introduction)
- [Power BI Desktop - Data Modeling and Exploration](#power-bi-desktop-data-modeling-and-exploration)
  - [Power BI Desktop – Layout](#power-bi-desktop-layout)
  - [Power BI Desktop – Data Exploration](#power-bi-desktop-data-exploration)
  - [Power BI Desktop – Data Exploration Continued](#power-bi-desktop-data-exploration-continued)
- [References](#references)

## Introduction

This is lab two out of five labs in total. Please continue to use your file after completing Lab 1, if you are joining the DIAD at this point or were unable to complete Lab 1, please start this lab with the “Lab 1 solution.pbix” file you can find in the **Reports** folder. 

In this lab you will learn how to:
 - create a range of different charts.
 - highlight and cross-filter.
 - create new groups and hierarchies.
 - add new measures to the model to do additional analysis.

The lab includes steps for the user to follow along with associated screenshots that provide a visual aid. In the screenshots, sections are highlighted with red or orange boxes to indicate the area the user needs to focus on.

>**Note**: This lab uses real, anonymized data provided by ObviEnce, LLC. Visit their site to learn about their services: www.obvience.com. This data is the property of ObviEnce, LLC and has been shared to demonstrate Power BI functionality with industry sample data. Any use of this data must include this attribution to ObviEnce, LLC.

# Power BI Desktop – Data Modeling and Exploration

In this section, we will learn about the [key parts of the Power BI desktop](https://powerbi.microsoft.com/en-us/documentation/powerbi-desktop-query-overview/). We will model and explore the data and build visuals.

## Power BI Desktop - Layout 

Let’s start with the main Power BI Desktop window and become familiar with the distinct sections available.

   ![](Images/powerbi-02-01.png)
   
1. On the top of the window, you see the **Home** tab where the most common operations you perform are available.

2. The **Insert** tab in the ribbon allows you to insert shapes, a text box or new visuals

3. The **Modeling** tab in the ribbon enables additional data modelling capabilities like adding custom columns and calculating measures. 

4. The **View** tab has options to format the page layout. 

5. The **Help** tab provides self-help options like guided learning, training videos and links to online communities, partner showcase and consulting services.

6. On the left side of the window, you have three icons, **Report**, **Data** and **Model**. If you hover over the icons, you can see the tooltips. Switching between these allows you to see the data and the relationships between the tables.

7. The center **white space** is the canvas where you will be creating visuals.

   ![](Images/powerbi-02-02.png)

8. The **Visualizations** panel on the right allows you to select visualizations, add values to the visuals,and add columns to the axis or filters.

9. The **Fields** window on the right panel is where you see the list of tables which were generated from the queries. Click the :arrow_down_small: icon (downward facing triangle) next to a table name to expand the field list for that table.

    ![](Images/powerbi-02-03.png)
    
10. Click on the **Data** icon on the left side. Expand the **Sales** table in the **Fields** pane as shown in the figure above. Scroll up and down to notice how fast you can navigate through over three million rows.

    ![](Images/powerbi-02-04.png)
    
11. Click on the **Model** icon on the left panel of Power BI Desktop. You see the tables you have imported along with Relationships. The Power BI Desktop automatically infers relationships between the tables. 
  - A relationship is created between the Sales and Product tables using the **ProductID** column.
  - A relationship is created between the Product and Manufacturer tables using the **ManufacturerID** column.

Power BI supports multiple types of relationships:
  - 1 to many 
  - 1 to 1 
  - Many to many 

In this lab, we will be using the 1 to many type of relationship, the most common type of relationship. This means one of the tables involved in the relationship should have a unique set of values. We will create additional relationships later in this lab. 

>**Note**: Tables may not appear as shown in the figure. You can zoom in and out of the **Relationships** page by dragging the zoom slider in the bottom right corner of the window. Also, if you want to ensure you are seeing all the tables, use the fit to screen icon: ![](Images/powerbi-02-05.png) . Drag and move the tables to appear as shown in the figure:

   ![](Images/powerbi-02-06.png)
   
12. Click on the Search box and notice the options available. The options change based on what you are clicked on in canvas

    ![](Images/powerbi-02-07.png)
    
## Power BI Desktop – Data Exploration 

Now that we have loaded data, let’s start with analyzing sales by country.

13. Click on the **Report** icon on the left panel to navigate to the Report view.

14. Click the **Clustered column chart** visual in **Visualizations** as shown in the screenshot.

    ![](Images/powerbi-02-08.png)
    
15. From the **Fields** section, expand the **Geography** table and then click the checkbox next to the **Country** field.

16. From the **Fields** section, expand the **Sales** table and then click the checkbox next to the **Revenue** field.

17. **Resize** the visual as needed by dragging the edges.

    ![](Images/powerbi-02-09.png)
    
 Notice that the revenue of each country is the same. Now we need to create a relationship between the Sales and Geography tables.

18. Click on the **Model** icon on the left panel to navigate to the Relationship view.

19. Our sales data is by **Zip** code, so we need to connect the Zip column from the **Sales** table with **Zip** column in the **Geography** table. You can do this by dragging the **Zip** field in the **Sales** table to connect the line with the **Zip** field in the **Geography** table.

    ![](Images/powerbi-02-10.png)
    
    You will notice the **Create relationship** dialog opens with a warning message at the bottom stating the relationship has a many-many cardinality. The reason for the warning is that we don’t have unique Zip values in the **Geography** table. This is because multiple countries could have the same Zip code. Let’s 
concatenate the **Zip** and **Country** columns to create a unique value field.

20. Click **Cancel** in the **Create relationship** dialog box.

    We need to create a new column in both the Geography table and the Sales table that combines the **Zip** and **Country** columns. Let’s start by creating a new column in the Sales table. 

21. Click on the **Report** icon on the left panel to navigate to the **Report** view.

22. In the **Fields** section, click on the ellipse next to the **Sales** table. Click the **New Column** as shown in the figure. You will see a formula bar appear, as shown in the screenshot, to help create this new column.

    ![](Images/powerbi-02-11.png)
    
23. Now we are ready to combine the Zip and Country columns into a new column called **ZipCountry**, separated by a comma. To create this column called ZipCountry, type the following calculation in the editor.

         `ZipCountry = Sales[Zip] & "," & Sales[Country]`

    ![](Images/powerbi-02-12.png)

24. Once you are done entering the formula press **Enter** or click the checkmark on the left side of the formula bar. 

    You will notice that IntelliSense appears guiding you to choose the correct column. The language you used to create this new column is called Data Analysis Expression (DAX). We are connecting columns (Zip and Country) in each row by using the “&” symbol. The icon with an (fx), near the new column ZipCountry, indicates that you have a column containing an expression, also referred to as a calculated column.

**IMPORTANT:heavy_exclamation_mark:**: If you get an error creating a new column, make sure your Zip column is the Text Data Type.

>**Note**: An alternative way to add a new column is by selecting the table, click **Table Tools**, click **New Column** or **Modeling**, and then click **New Column** from the ribbon.

   ![](Images/powerbi-02-13.png)
   
   Let us use this method to create a **ZipCountry** column in the **Geography** table. 

25. From the Fields section, click the **Geography** table, from the ribbon click **Modeling**, and then click **New Column** as shown in the figure.

    ![](Images/powerbi-02-14.png)

26. A formula bar now appears. Enter the following DAX expression in the formula bar: 

          `ZipCountry = Geography[Zip] & "," & Geography[Country]` 
          
    ![](Images/powerbi-02-15.png)

You will see a new column, **ZipCountry**, in the **Geography** table. The final step is to set up the relationship between the two tables using the newly created **ZipCountry** columns in each of these tables.

27. Click on the **Model** icon on the left panel to navigate to the **Relationship** view.

28. Drag the **ZipCountry** field from the **Sales** table and connect it to the **ZipCountry** field in the **Geography** table.

    ![](Images/powerbi-02-16.png)
    
Now we have successfully created a relationship. The number “1” next to Geography indicates it is on the one side of the relationship and the “*” next to Sales indicates it is on the many side of the relationship.

29. Click on the **Report** icon on the left panel to navigate to the **Report** view.

Notice the clustered column chart that we created earlier. It shows different sales for each country or region. USA has the most sales, followed by Australia and Japan. By default, the chart is sorted by **Revenue**.

30. Click on the **ellipse** on the top right corner of the visual (alternatively, the ellipse may be at the bottom of the chart). Notice there is an option to Sort by **Country** as well.

    ![](Images/powerbi-02-17.png)

31. Notice that we have some blanks in our data. We want to clean up our data and get rid of the blanks

32. Drag the **Country** field from the **Geography** table to the Filters pane and drop it in **Filters on all pages**

33. Change filter type to **Advanced filtering** and select **is not blank**, click on **Apply Filter**
 
 >**NOTE**: Additional filter options are available: is blank, is empty, is not empty

   ![](Images/powerbi-02-18.png)

34. From the **Fields** section, expand the **Manufacturer** table, and then drag the **Manufacturer** column to the **Legend** section under Visualizations.

35. While you have your chart selected, click the **Clustered column chart** from the **Visualizations** section, and then click the **Stacked column chart** visual.

36. **Resize** the visual as needed.

    ![](Images/powerbi-02-19.png)

Now we can see the top manufacturers by country. 

Now let’s try different visuals to see which chart represents the data the best.

37. Begin with the **Stacked column chart** selected.

    ![](Images/powerbi-02-20.png)

38. Sort the legend in descending order

    ![](Images/powerbi-02-21.png)
    
39. In the **Filters** pane, expand **Manufacturer**.

40. From the **Filter Type** dropdown menu, click **Top N**.

41. Enter **5** in the text box next to **Top**.

42. From the **Sales** table, drag and drop the **Revenue** field into the **By value** section.

43. Click on **Apply filter**.

    ![](Images/powerbi-02-22.png)

Notice that the visual is filtered to display the top five manufacturers by Revenue. We see that the manufacturer VanArsdel has a higher percentage of sales in Australia compared to other countries or regions.

We can now add total labels to the stacked visuals

44. Lets explore font formatting options

45. Click on the **paint roller icon** and click on **X axis**

46. Turn on **Bold** and **Italic** – feel free to try different formatting option on different areas. For the purpsoe of the lab we will turn off Bold and Italic

    ![](Images/powerbi-02-23.png)

47. Navigate to the **Total labels** heading and click to **On**

    ![](Images/powerbi-02-24.png)
    
Let’s remove the total labels

48. Click Total labels to the **Off** position

We are interested in the top five competitors by revenue. Let’s group them so we don’t have to add a filter to every visual. Before we do that, we’ll remove the **Top 5** visual level filter.

49. Begin with **Stacked column chart** selected.

50. Hover over and click the **Clear filter** icon (erase) next to **Manufacturer** field in the **Filters** Pane.

    ![](Images/powerbi-02-25.png)

51. From the **Fields** section, right-click on the **Manufacturer** field name from **Manufacturer** table.

>**Note**: do not check the checkbox.

52. Click **New Group**.

53. In the **Ungrouped values** section, using **Ctrl** key, click **Aliqui**, **Currus**, **Natura**, and **Pirum**.

54. Click the **Group** button. Notice a new group is added in the **Groups and members** section.

55. Double-click the newly created group and rename it **Top Competitors**.

56. Click **VanArsdel** from the **Ungrouped values** section and click the **Group** button to create the **VanArsdel** group.

57. Click the checkbox **Include Other group**. This will create another **Other** group that includes all the other manufacturers.

58. Click **OK** to close the **Groups** dialog.

    ![](Images/powerbi-02-26.png)
    
59. With the **Stacked column chart** selected, click on the **X** next to **Manufacturer** in the **Legend** section. This will remove the Manufacturer.

60. From the **Fields** section, drag the newly created **Manufacturer (groups)** to the **Legend** section.Now we can see that VanArsdel has nearly 50% share in Australia.

    ![](Images/powerbi-02-27.png)

61. Hover over one of the columns and right-click.

62. Click **Show as a table**. You will now be in **Focus** mode with the chart displayed on top and the data displayed below. Notice that VanArsdel has a large percent of the Australian market.

63. Use the icon in the top right corner to switch to the vertical layout. In this layout, you view the chart on the left panel and the data on the right panel.

64. Click **Back to Report** to go back to the **Report** canvas.

    ![](Images/powerbi-02-28.png)

 >**Note**: You can use similar steps to Show data point as a table to see records for a specific data point.

Now let’s create a Revenue by Manufacturer visual.

65. Click on the white space in the canvas. From the **Fields** section, click the checkbox next to the **Revenue** field in the **Sales** table.

66. From the **Fields** section, click the checkbox next to the **Manufacturer** field in the **Manufacturer** table.

67. From the **Visualizations** section, click the **Treemap** visual.

    ![](Images/powerbi-02-29.png)
    
We now have Revenue by Manufacturer. Now let’s turn our attention to the interaction between the Stacked column chart and the Treemap visuals.

68. In the **Treemap**, click **VanArsdel** and notice that the Stacked column chart is filtered. This confirms that VanArsdel has a large percentage of the Australian market.

    ![](Images/powerbi-02-30.png)
    
69. To remove the filter, click **VanArsdel** again.

This interaction between visuals is called cross-filtering.

Previously, we added a Top 5 Visual level filter. Now let’s add a filter to the Page level, so we are working with the Top Competitors and VanArsdel and filter out the other manufacturers.

Page-level filters apply to all visuals on the page. Visual-level filters apply only to a visual. Ensure the Filters pane is expanded/open.

70. From the **Fields** section, drag **Manufacturer (groups)** from the **Manufacturer** table to the **Filters on this page** box in the **Filters Pane**.

71. Click **Top Competitors** and **VanArsdel**.

    ![](Images/powerbi-02-31.png)

Now, let’s add a visual that provides sales information over time

72. Begin by clicking on the white space in the canvas.

73. Click the checkbox next to the **Date** field in the **Sales** table. Notice that a Date Hierarchy is created. 

74. Click the checkbox next to the **Revenue** in the **Sales** table field. Notice that a Clustered column chart is created. Also notice in the **Axis** section, a date hierarchy is created. There are arrows on the top bar of the chart which are used to navigate through the hierarchy.

    ![](Images/powerbi-02-32.png)

75. Click on the **Australia** column in the **Revenue by Country** visual.

76. With the **Revenue by Country** visual selected, from the ribbon click on **Format**, and then click **Edit Interactions**. Notice on the top right of the other two visuals new icons with the highlight icon selected.

77. Click the **filter icon** for both visuals.

    ![](Images/powerbi-02-33.png)
    
Notice now in both Revenue by Year and Revenue by Manufacturer, data is filtered for Australia

78. Now click the **Revenue by Year** visual.

79. Next, click the **filter** icon on the other two visuals.

    ![](Images/powerbi-02-34.png)

80. Similarly, click on the **Revenue by Manufacturer** visual and click the **filter icon** on the other **two visuals**. Once you are done, all the visuals should be in filter mode.

81. With the **Revenue by Manufacturer** visual selected, from the ribbon click **Format** then **Edit Interactions** to remove the icons.

82. Click on VanArsdel in the Revenue by Manufaturer visual

>**Note**: If your screen doesn’t look like the one below please edit your interactions.

   ![](Images/powerbi-02-35.png)

We have already noticed that VanArsdel has a large share of the market in Australia. Let’s see how VanArsdel has done over time in Australia.

83. Click on the **Revenue by Country and Manufacturer (groups)** chart and remove **Manufacturer (groups)** from the legend.

84. Click on **VanArsdel** in the **Revenue by Manufacturer** visual.

85. **Ctrl+Click** the **Australia column** in the **Revenue by Country** visual. 

Now we have filtered the charts by both VanArsdel and Australia. Looking at the results, we can see a spike in 2021 sales for VanArsdel in Australia. This spike in sales is intriguing, so let’s investigate further.

86. Click the down arrow on the top of the **Revenue by Year** visual. This enables drill-down capability.

    ![](Images/powerbi-02-36.png)
    
87. Click the **2021** column in the **Revenue by Year** visual.

Notice that you have drilled down to the quarter level of 2021. There was a big spike in the fourth quarter. Let’s dig further.

88. Click on the double arrow icon on the top of the **Revenue by Year** visual. This drills down to the next level of the hierarchy, which is the month.

    ![](Images/powerbi-02-37.png)

89. Click on the up-arrow icon on the top of the **Revenue by Year** visual to drill up to the **Quarter** level.

90. Click on the drill up icon again to go up to the **Year** level

91. Click on the split arrow icon on the top right of the **Revenue by Year** visual. This expands down to the next level of the hierarchy, which is quarters for all the years.

Notice that the fourth-quarter sales have always been high, but in 2021 there was a larger sales spike in the fourth quarter than usual.

92. Now let’s expand down to the month level. Click on the split arrow icon on the top right of the **Revenue by Year** visual. This expands down to the next level of the hierarchy, which is months for all the years.

    ![](Images/powerbi-02-38.png)

There is a lot of information in the visual and we must scroll left and right to compare.

## Power BI Desktop – Data Exploration Continued

Now that we’ve explored the data, let’s add a slicer so we can filter by the manufacturers.

93. Click on the white space in the canvas. From the **Fields** section, click the checkbox next to the **Manufacturer** field in the **Manufacturer** table.

94. From the **Visualizations** section, click on the **Slicer** visual.

95. Here you will see a list of Manufacturers. Click **VanArsdel** and notice that all the visuals are filtered based on your selection.

96. Hover over the top right corner of the visual and click on the down arrow. Notice you have the option to change the slicer from a list to a dropdown.

97. Click **Dropdown**.

98. Click **VanArsdel** from the dropdown.

    ![](Images/powerbi-02-39.png)
    
99. Confirm **Top Competitors** and **VanArsdel** are selected in the **Manufacturer (groups)** filter in the **Filters** pane.

    ![](Images/powerbi-02-40.png)
    
Note that there is a box for **Filters on all pages** in the **Filters** pane. If you have duplicate pages, this is how you sync a filter for the whole file.

Now let’s use the **Manufacturer** slicer to analyze one manufacturer at a time.

100. Begin by clicking on the **Revenue by Manufacturer Treemap** visual.

101. From the **Visualizations** section, click on the **Card** visual.
    
     ![](Images/powerbi-02-41.png)
     
The card visual gives us the Revenue as we filter and cross-filter the visuals.

Notice that all key dimensions are in their table with related attributes, except the date. For example, **Product** attributes are in the **Product** table. Now let’s create a **Date** table.

102. Navigate to the **Data** view by clicking on the **Data** icon in the left panel.

103. From the ribbon, click on **Table Tools**, then click on **New Table**.

Notice that a new table is created in the **Fields** section on the right and that the formula bar opens.

104. Enter `Date =CALENDAR (DATE(2014,1,1), DATE(2021,12,31))` in the formula bar and click on the checkmark. A Date table with a Date column is created.

We are using two DAX functions: the **CALENDAR** function, which takes the start and end data, and the **DATE** function, which takes the **year**, **month**, and **date** Fields. 

For this lab, we will create Dates from 2014 to 2021, since we have data for those years. We can also add more Fields, like **Year**, **Month**, **Week**, etc., to this table by using DAX functions. 

Notice that the **Date** field is of the type **Date/Time**. Let’s change it to the **Date** data type.

105. Click on the **Date** field in the **Date** table.

106. From the ribbon, click **Column Tools**, click **Data type**, and then click **Date**.

     ![](Images/powerbi-02-42.png)

Next, we need to create a relationship between the newly created **Date** table and the **Sales** table. 

107. From the ribbon, click **Column Tools**, and then click **Manage Relationships**.

108. A **Manage Relationships** dialog box opens. Click the **New** button.

109. A **Create Relationship** dialog box opens. Click **Date** from the top dropdown menu.

110. Click **Sales** from the second dropdown menu.

111. Highlight the **Date** Field in both tables.

112. Click **OK** to close the **Create relationship** dialog box.

     ![](Images/powerbi-02-43.png)

113. Click **Close** to close the **Manage relationships** dialog box.

114. Navigate to the Report view by clicking on the **Report** icon in the left panel.

Notice that the Revenue by Date chart looks different. Let’s fix it

115. Click the **Revenue by Date** visual.

116. From the **Axis**, click on the “**X**” to remove the **Date** field.

     ![](Images/powerbi-02-44.png)

117. From the **Fields** section, expand the **Date** table.

118. Now drag the **Date** field to the **Axis** section.

     ![](Images/powerbi-02-45.png)

Notice that the new **Date** field behavior is like it was previously.

Since there are now two Date Fields, it may be confusing to know which one to use. To accommodate this, let’s hide the **Date** field in the **Sales** table.

119. From the **Fields** section, click on the **three dots** next to the **Date** field in the **Sales** table and select **Hide**

     ![](Images/powerbi-02-46.png)

120. In the same way, hide **Country**, **ProductID**, **Zip**, and **ZipCountry** in the **Sales** table as well.

121. Now hide **ZipCountry** from the **Geography** table.

122. Hide **ManufacturerID** from **Manufacturer** table.

123. Hide **ProductID** and **ManufacturerID** from **Product** table.

**Tip**: It is a best practice to hide unused Fields in reports.

Now let’s get back to our data story, Australia, VanArsdel and 2021. Let’s check if the spike occurred in a specific region in Australia.

124. Click the **Revenue by Country** visual.

125. From the **Fields** section, drag the **State** field from the **Geography** table below the **Country** field in the **Axis** section.

126. Drag the **District** field below the **State** field in the **Axis** section.

We have just created a hierarchy.

   ![](Images/powerbi-02-47.png)

127. Make sure that **VanArsdel** is selected in the **Manufacturer** slicer.

128. Enable **Drill mode** by clicking the down arrow of the **Revenue by Country** visual.

     ![](Images/powerbi-02-48.png)

129. Click **Australia** to drill down to the **State** level.

130. From the **Revenue by Year** visual click **2021** and notice what happens to the **Revenue by Country** and the **State** visual.

131. Now, **Drill up** to the **country** level.

132. Disable drill mode by clicking the down arrow again.

Now let’s analyze the data by product. We’ll start by creating a product hierarchy.

133. From the **Fields** section, click on the **ellipse** next to the **Category** field in the **Product** table.

134. Click **Create Hierarchy**.

     ![](Images/powerbi-02-49.png)

Notice that a new field called **Category Hierarchy** is created in the Product table.

135. Double-click **Category Hierarchy** and rename it to **Product Hierarchy**.

     ![](Images/powerbi-02-50.png)  

136. Click the **ellipse** next to **Segment**.

137. Click **Add to Hierarchy**, and then click **Product Hierarchy**.

     ![](Images/powerbi-02-51.png)

138. Click the **ellipse** next to **Product**.

139. Click **Add to Hierarchy**, and then click **Product Hierarchy**.

We have now created a Product Hierarchy with the priority of Category, Segment, and then Product. 

140. Click on the white space in the canvas. From the **Visualizations** section, click **Clustered bar chart**.

141. From the **Fields** section, expand the **Product** table.

142. Click the checkbox next to the **Product Hierarchy**. Notice the complete hierarchy is selected.

143. From the **Fields** section, expand the **Sales** table.

144. Click the checkbox next to the **Revenue** field.

145. Let’s edit interactions for the new chart.

146. Click the Format tab and click edit interations

147. Click on the **Revenue by Country** visual and change the **Revenue by Category** visual to **filter**

     ![](Images/powerbi-02-52.png)

148. Do the same thing with the **Revenue by Year** visual, change the interaction of the **Revenue by Category** to **filter**

149. We also need to change the interactions of the other charts. Click on the Revenue by **Category** visual and change the **Revenue by Year** visual to a **filter** action.

150. Click the **filter** interaction on the **Revenue by Country** visual as well

151. Click the **format** tab and click **Edit interactions** to turn it off

152. Ensure **Australia** and **2021** are selected.

153. Let’s get back to the **Revenue by Category** visual

     ![](Images/powerbi-02-53.png)

154. Enable drill-down mode in the **Revenue by Category** chart by clicking on the down arrow.

     ![](Images/powerbi-02-54.png)

155. Click on **Urban**.

156. In the **Revenue by Country** visual, if you are not at the Country level drill up to Country level anddisable drill down

     ![](Images/powerbi-02-55.png)


