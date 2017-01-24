---
title: "&#39;&lt;Null 常數&gt;&#39; 項目未宣告 | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bc30822"
  - "vbc30822"
helpviewer_keywords: 
  - "BC30822"
ms.assetid: dda0e2c1-46a3-4cc4-b36c-0858a5259bac
caps.latest.revision: 13
caps.handback.revision: 13
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;&lt;Null 常數&gt;&#39; 項目未宣告
'\<Null 常數\>' 項目未宣告。 不再支援 Null 常數。請使用 System.DBNull 代替。  
  
 陳述式使用 Visual Basic 不再支援的 `Null` 關鍵字。  
  
 **錯誤 ID︰**BC30822  
  
### 更正這個錯誤  
  
1.  使用 <xref:System.DBNull> 取代 `Null`。 下列範例為其示範。  
  
    ```  
    Sub TestDBNull() Dim t As DataTable ' Assume the DataGrid is bound to a DataTable. t = CType(DataGrid1.DataSource, DataTable) Dim r As DataRow r = t.Rows(datagrid1.CurrentCell.RowNumber) r.BeginEdit r(1) = System.DBNull.Value ' Assign DBNull to the record. r.EndEdit r.AcceptChanges If r.IsNull(1) Then MsgBox("") End If End Sub  
    ```  
  
2.  當您使用物件變數時，請使用 [Nothing](../Topic/Nothing%20\(Visual%20Basic\).md) 關鍵字進行指派和比較。 下列範例為其示範。  
  
    ```  
    Sub TestNothing() Dim cls As Object ' cls is Nothing if it has not been assigned using the New keyword. If (cls Is Nothing) Then MsgBox("cls is Nothing") End If cls = Nothing ' Assign Nothing to the class variable cls. End Sub  
    ```  
  
## 請參閱  
 <xref:System.DBNull>   
 [Nothing](../Topic/Nothing%20\(Visual%20Basic\).md)   
 [Programming Element Support Changes Summary](http://msdn.microsoft.com/zh-tw/0483590a-6309-449c-a2fa-effa26a03b95)