---
title: 'Creating a BRE Lookup'
--- 
# Table of Contents

- [Table of Contents](#table-of-contents)
  - [Before You Begin](#before-you-begin)
  - [Fill in the form with the necessary details and click "Update Directions"](#fill-in-the-form-with-the-necessary-details-and-click-update-directions)
  - [Preparing the tenant to use the BRE:](#preparing-the-tenant-to-use-the-bre)
    - [In the Attributes section:](#in-the-attributes-section)
      - [Found rule](#found-rule)
      - [NotFound rule](#notfound-rule)
  - [Accessing the BRE data from your flow](#accessing-the-bre-data-from-your-flow)

---

## Before You Begin
Ask your CSM to create a BRE Table for you

You can access the BRE data here: https://rules.wxcc-us1.cisco.com/datasync

---

## Fill in the form with the necessary details and click "Update Directions" 
<form>
  
  <label for="context">Table Name Created by CSM:</label><br>
  <input type="text" id="context" name="context"><br>
  
  <label for="label">Label Name (keep default unless you have a reason):</label><br>
  <input type="text" id="label" name="label" value="routeInfo"><br>
  
  <label for="key">Key to be used in flows:</label><br>
  <input type="text" id="key" name="key"><br>
<br>

  <button onclick="update()">Update Directions</button>
</form>

---

## Preparing the tenant to use the BRE:

 ⚠️ **Important note:** All BRE are settings, rules, attributes, and labels are case sensitive!

> Click BRE 
Click Attributes and add a new attribute called context (case sensitive) and type text
>
> Click Labels and add <w class="label_out">routeInfo</w> (case sensitive)
>
> Click Context and Add Context with the name of the <w class = "context_out">table/Context that your CSM created for you</w> (case sensitive) then select <w class = "context_out">context</w> under Attribute

### In the Attributes section:

#### Found rule

> Click on Add Rule (Editor)
> 
> Name your rule <w class="context_out">something ending in </w>Found
> 
> Click to make the rule active
> 
> Select the label <w class = "label_out"> </w> from the drop down 
>
>Set the priority to 100
>
>Copy the rule into the editor



>> when<br>
    c: Contact()<br>
    eval(c.getGlobalValuesManager().getAsString( c.getTenantId(), c.getAttribute("context")+"." + c.getAttribute("<w class = "key_out">ani</w>")) != null)<br>
 then<br>
    c.putAttribute("<w class = "label_out">routeInfo</w>", c.getGlobalValuesManager().getAsString(c.getTenantId(), c.getAttribute("context")+"." + c.getAttribute("<w class = "key_out">ani</w>")));<br>
 end<br>

#### NotFound rule

> Click on Add Rule (Editor)
> 
> Name your rule <w class="context_out">something ending in </w>Notfound
> 
> Click to make the rule active
> 
> Select the label <w class = "label_out"> </w> from the drop down 
>
>Set the priority to 99
>
>Copy the rule into the editor




>> when<br>
    c: Contact()<br>
    eval(c.getGlobalValuesManager().getAsString( c.getTenantId(), c.getAttribute("context")+"." + c.getAttribute("<w class = "key_out">ani</w>")) == null)<br>
 then<br>
   c.putAttribute("<w class = "label_out">routeInfo</w>", "NotFound");<br>
 end<br>


## Accessing the BRE data from your flow






<script>
    function update(){them = Array.from(document.querySelectorAll("input")).reduce((acc, input) => ({...acc, [input.id + "_out"] : input.value}),{});
	Object.entries(them).forEach((entry) => {
    Array.from(document.getElementsByClassName(entry[0])).forEach((element,index) => 
    {
      console.log(document.getElementsByClassName(entry[0])[index].innerHTML); 
      document.getElementsByClassName(entry[0])[index].innerHTML = entry[1];
    })})

  event.preventDefault()}
</script> 