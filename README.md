# cascatingdropbox

A common problem is to relate different html elements and add the data to that elements using a json datasource.

The most common style of this is to have to select elements / dropdown elements, and have the content of one of them based on other select box.

This is a problem i had seen and evaluate the solution for th elast 10 years, so i had decided to share to the community the solution i had use for that 

The example will consider we have a select box that allow us to select the brand of a vehicle and the second one the model.

First of all we should define the data domain or source for or selectbox's.

The easiest way is to consider the following object model

  var models = {
        'Nissan': ['cla', 'Qdatsun'],
        'Opel': ['BarcelINSIGNIA SPORTS','COMBO VAN 1.6'],
        'Seat': ['ARONA 1.6 TDI','IBIZA','Porto'],}
    
  For the first sample i had decide to consider the correlation between brand and possible models, reperesenting as JSON you have and array of Objects.
  
  So the easiest way to popolate the dependent select box is to get the value of the first select box and with that index the models array to get the valid values for that index and populate the second select box.
  
  In Jquery we would have something like:
  
   $('#sel_brand').change(function () {
        var sel_brand = $(this).val(), lcns = models[sel_brand] || [];
        
        var html = $.map(lcns, function(lcn){
            return '<option value="' + lcn + '">' + lcn + '</option>'
        }).join('');
        $sel_model.html(html)
    });
    
