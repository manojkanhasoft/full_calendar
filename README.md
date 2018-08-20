# Full Calendar with Extra Functionality

### This Demo using php `slim framwork` for backend.This code also contain the dump file of database in dump folder.
#### Note:In this Demo there is a three types of user 1)Executive, 2)Manager, 3)Basic User. And i am considering executive user with `user_id=1` as a login user.

This functionality is enhanced from **[Jquery Full Calendar](https://fullcalendar.io/)**.

In this calendar , i have added below extra functionality or use below plugins.

  - Display time in WEEK and DAY view with red line.
  - Display Events/Tasks for user.
  - Save last view(Month,Week,Day) of full calendar and display that view when user again visit the page.
  - In full calendar, user can view only one month next/previous , user has to do many clicks for change year , but in this i have put a bootstrap datepicker , when user change date in datepicker fullcalendar date is also change.For this you have to click calendar icon besides to **Today**.
  - Save color for Events/Tasks for specific user. **For color change i have used [Jquery color picker](http://www.eyecon.ro/colorpicker/)**.
  - Use a [Jquery Template](https://github.com/BorisMoore/jquery-tmpl) for bind User List.
  - Completed task display with strike line.
  
  ## Preview
   
   #### Demo Link : [CLICK HERE](http://fullcalendar.kanhasoftdev.com/),(For data check Year 2017)
   
  ## Usage
   
  #### HTML CODE:
  `<div id='calendar-external' class="col-sm-9"></div>`
  
  #### JQUERY Code
  ##### NOTE: This is just initialization, for more options check `demo-calendar.js` file.
  
  `var calendar = $('#calendar-external').fullCalendar();`
  
  ##### For initialize color picker.
  
  `$('.color1').colorPicker({showHexField: false});`
  
  ##### For add calendar icon before `Today` in right panel.
  
  ```
// PREPEND CALENDER ICON BEFORE TODAY,USING THIS CALENDER USER CAN EASILY MOVE TO ANOTHER MONTH , ANOTHER YEAR.
$('.fc-right').prepend('<span class="form-group" id="caldatepicker"><i class="fa fa-calendar"></i></span>');
  ```
  
  ##### For initialize datepicker(for above code) with change date in full calendar.
  
  ```
    // BIND CALENDER. */
  $('#caldatepicker').datepicker({
         closeOnDateSelect: true
  }).on('changeDate', function (ev) {
         // CHANGE FULL CALENDER MONTH AND YEAR WHEN THIS CALENDER DATE SELECT.
         calendar.fullCalendar('gotoDate', ev.date);
  });
  ```
  ##### Code for STRIKE line in task , For that need to put below code in fullcalender.js file.
  > Change in `fgSegHtml: function(seg, disableResizing) {` function.
  
  ```
  var strickout_class = "";
  if (event.status == 3) // status 3 is for completed task.
        strickout_class = "text-decoration:line-through";
                
  return '<a class="' + classes.join(' ') + '"' +
                    (event.url ?
                            ' href="' + htmlEscape(event.url) + '"' :
                            ''
                            ) +
                    (skinCss ?
                            ' style="' + skinCss + '"' :
                            ''
                            ) +
                    '>' +
                    '<div class="fc-content" style="' + strickout_class + '">' +
                    (this.isRTL ?
                            titleHtml + ' ' + timeHtml : // put a natural space in between
                            timeHtml + ' ' + titleHtml   //
                            ) +
                    '</div>' +
                    (isResizableFromStart ?
                            '<div class="fc-resizer fc-start-resizer" />' :
                            ''
                            ) +
                    (isResizableFromEnd ?
                            '<div class="fc-resizer fc-end-resizer" />' :
                            ''
                            ) +
                    '</a>';
                
  ```
  
  
