#QlikView CookBook 
**Current Page : 34**

##Charts
* 'Pop-up Labels' option (in Presentation Tab) is just like 'ToolTip' in SSRS. If we want to display a customized Pop-up, we can create a new expression and uncheck the 'BAR' option so that only popup will be shown. In this case, if we dont disble the 'pop-up' for other Expressions, both the defined popup for the existing expression and the Customized popup that we created, will be displayed.
* When we open the Qlikview Script Editor, we see a set of Variables being assigned values. These are standard Qlikview Variables and can be used in the script or expressions.
* chr(10) is a line feed that moves the text onto the next line. We can use it in expression when we want the text to go to the next line.
* BoxPlot doesnt work for all types of charts. For example, it works for Combo Chart while it is not enabled for Bar Chart.
* We can combine two charts by setting the Transparency of background of one chart to 100% and matching the 'Static Max' option in both the charts. In this case we need to ensure that the 'layer' setting of the top most chart should be 'Top' and the below one to be 'Normal'. We can also try Custom layer options.
* 
