---
title: 預存程式屬性範例（JScript） |Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
dev_langs:
- JScript
helpviewer_keywords:
- ActiveConnection property [ADO], JScript example
- CommandText property [ADO], JScript example
- Size property [ADO], JScript example
- Direction property [ADO], JScript example
- CommandTimeout property [ADO], JScript example
ms.assetid: ea74e2a3-c965-43aa-9076-26a084b48ad8
author: rothja
ms.author: jroth
ms.openlocfilehash: 0fb389dd9761ff4e310d5047f85085b7f9ff6a43
ms.sourcegitcommit: 6037fb1f1a5ddd933017029eda5f5c281939100c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2020
ms.locfileid: "82763559"
---
# <a name="activeconnection-commandtext-commandtimeout-commandtype-size-and-direction-properties-example-jscript"></a>ActiveConnection、CommandText、CommandTimeout、CommandType、Size 和 Direction 屬性範例（JScript）
這個範例會使用[ActiveConnection](../../../ado/reference/ado-api/activeconnection-property-ado.md)、 [CommandText](../../../ado/reference/ado-api/commandtext-property-ado.md)、 [CommandTimeout](../../../ado/reference/ado-api/commandtimeout-property-ado.md)、 [CommandType](../../../ado/reference/ado-api/commandtype-property-ado.md)、 [Size](../../../ado/reference/ado-api/size-property-ado-parameter.md)和[Direction](../../../ado/reference/ado-api/direction-property.md)屬性來執行預存程式。 將下列程式碼剪下並貼到 [記事本] 或其他文字編輯器，然後將它儲存為**ActiveConnectionJS。**  
  
```  
<!-- BeginActiveConnectionJS -->  
<%@LANGUAGE="JScript"%>  
<%// use this meta tag instead of adojavas.inc%>  
<!--METADATA TYPE="typelib" uuid="00000205-0000-0010-8000-00AA006D2EA4" -->  
  
<html>  
<head>  
    <title>ActiveConnection, CommandText, CommandTimeout, CommandType, Size, and Direction Properties</title>  
<style>  
<!--  
BODY {  
   font-family: 'Verdana','Arial','Helvetica',sans-serif;  
   BACKGROUND-COLOR:white;  
   COLOR:black;  
    }  
.thead {  
   background-color: #008080;   
   font-family: 'Verdana','Arial','Helvetica',sans-serif;   
   font-size: x-small;  
   color: white;  
   }  
.thead2 {  
   background-color: #800000;   
   font-family: 'Verdana','Arial','Helvetica',sans-serif;   
   font-size: x-small;  
   color: white;  
   }  
.tbody {   
   text-align: center;  
   background-color: #f7efde;  
   font-family: 'Verdana','Arial','Helvetica',sans-serif;   
   font-size: x-small;  
    }  
-->  
</style>  
</head>  
  
<body bgcolor="White">  
  
<%  
    var iRoyalty = parseInt(Request.Form("RoyaltyValue"));  
    // check user input  
  
    if (iRoyalty > -1)  
    {  
            // connection and recordset variables  
        var Cnxn = Server.CreateObject("ADODB.Connection")  
        var strCnxn = "Provider='sqloledb';Data Source=" + Request.ServerVariables("SERVER_NAME") + ";" +  
            "Initial Catalog='pubs';Integrated Security='SSPI';";  
        var cmdByRoyalty = Server.CreateObject("ADODB.Command");  
        var rsByRoyalty = Server.CreateObject("ADODB.Recordset");  
        var rsAuthor = Server.CreateObject("ADODB.Recordset");  
        // display variables  
        var filter, strMessage;          
  
        try  
        {  
            // open connection  
            Cnxn.Open(strCnxn);  
  
            cmdByRoyalty.CommandText = "byroyalty";  
            cmdByRoyalty.CommandType = adCmdStoredProc;  
            cmdByRoyalty.CommandTimeOut = 15;  
  
            // The stored procedure called above is as follows:  
                //    CREATE PROCEDURE byroyalty  
                //  @percentage int  
                //    AS  
                //  SELECT au_id from titleauthor  
                //  WHERE titleauthor.royaltyper = @percentage  
                //  GO  
  
            prmByRoyalty = Server.CreateObject("ADODB.Parameter");  
            prmByRoyalty.Type = adInteger;  
            prmByRoyalty.Size = 3;  
            prmByRoyalty.Direction = adParamInput;  
            prmByRoyalty.Value = iRoyalty;  
            cmdByRoyalty.Parameters.Append(prmByRoyalty);  
  
            cmdByRoyalty.ActiveConnection = Cnxn;  
  
            // recordset by Command - Execute  
            rsByRoyalty = cmdByRoyalty.Execute();  
  
            // recordset by Recordset - Open  
            rsAuthor.Open("Authors", Cnxn);  
  
            while (!rsByRoyalty.EOF)  
            {  
                // set filter  
                filter = "au_id='" + rsByRoyalty("au_id")  
                rsAuthor.Filter = filter + "'";  
  
                // start new line  
                strMessage = "<P>";  
  
                // get data  
                strMessage += rsAuthor("au_fname") + " ";   
                strMessage += rsAuthor("au_lname") + " ";  
  
                // end line  
                strMessage += "</P>";  
  
                // show data  
                Response.Write(strMessage);  
  
                // get next record  
                rsByRoyalty.MoveNext;  
            }  
        }  
        catch (e)  
        {  
            Response.Write(e.message);  
        }  
        finally  
        {  
            // clean up  
            if (rsByRoyalty.State == adStateOpen)  
                rsByRoyalty.Close;  
            if (rsAuthor.State == adStateOpen)  
                rsAuthor.Close;  
            if (Cnxn.State == adStateOpen)  
                Cnxn.Close;  
            rsByRoyalty = null;  
            rsAuthor = null;  
            Cnxn = null;  
        }  
    }  
%>  
  
<hr>  
  
<form method="POST" action="ActiveConnectionJS.asp">  
  <p align="left">Enter royalty percentage to find (e.g., 40): <input type="text" name="RoyaltyValue" size="5"></p>  
  <p align="left"><input type="submit" value="Submit" name="B1"><input type="reset" value="Reset" name="B2"></p>  
</form>  
  
</body>  
  
</html>  
<!-- EndActiveConnectionJS -->  
```  
  
## <a name="see-also"></a>另請參閱  
 [ActiveCommand 屬性（ADO）](../../../ado/reference/ado-api/activecommand-property-ado.md)   
 [Command 物件（ADO）](../../../ado/reference/ado-api/command-object-ado.md)   
 [CommandText 屬性（ADO）](../../../ado/reference/ado-api/commandtext-property-ado.md)   
 [CommandTimeout 屬性（ADO）](../../../ado/reference/ado-api/commandtimeout-property-ado.md)   
 [CommandType 屬性（ADO）](../../../ado/reference/ado-api/commandtype-property-ado.md)   
 [Connection 物件（ADO）](../../../ado/reference/ado-api/connection-object-ado.md)   
 [Direction 屬性](../../../ado/reference/ado-api/direction-property.md)   
 [Parameter 物件](../../../ado/reference/ado-api/parameter-object.md)   
 [Record 物件（ADO）](../../../ado/reference/ado-api/record-object-ado.md)   
 [Recordset 物件（ADO）](../../../ado/reference/ado-api/recordset-object-ado.md)   
 [Size 屬性 (ADO 參數)](../../../ado/reference/ado-api/size-property-ado-parameter.md)
