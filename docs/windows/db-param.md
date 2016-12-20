---
title: "db_param | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "vc-attr.db_param"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "db_param attribute"
ms.assetid: a28315f5-4722-459e-92ef-32e83c0b205a
caps.latest.revision: 11
caps.handback.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# db_param
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

將指定的成員變數以輸入或輸出參數相關聯，用來分隔的變數。  
  
## 語法  
  
```  
  
      [ db_param(   
   ordinal,   
   paramtype="DBPARAMIO_INPUT",   
   dbtype,   
   precision,   
   scale,   
   status,   
   length  
) ]  
```  
  
#### 參數  
 `ordinal`  
 資料行編號 \(**DBCOLUMNINFO** 序數\) 對應到要將資料繫結至資料列集的欄位。  
  
 *paramtype*  \(可省略\)  
 若要設定的參數型別。  提供者都會支援僅 I\/O 的參數型別所支援的基礎資料來源。  型別是組合的一或多 **DBPARAMIOENUM** 的值：  
  
-   **DBPARAMIO\_INPUT** 的輸入的參數。  
  
-   **DBPARAMIO\_OUTPUT** 輸出參數。  
  
-   **DBPARAMIO\_NOTPARAM** 的存取子擁有無參數。  設定 **eParamIO** 這個資料列中的值來存取子提醒使用者參數會被忽略。  
  
 *dbtype*  \(可省略\)  
 OLE DB [型別指示器](https://msdn.microsoft.com/en-us/library/ms711251.aspx)的資料行的項目。  
  
 *精確度* \(可省略\)  
 資料行的項目所使用的整數位數。  如需詳細資訊，請參閱說明 **bPrecision** 中的項目 [DBBINDING 結構](https://msdn.microsoft.com/en-us/library/ms716845.aspx)  
  
 *小數位數* \(可省略\)  
 要用於資料行的項目小數位數。  如需詳細資訊，請參閱說明 **bScale** 中的項目 [DBBINDING 結構](https://msdn.microsoft.com/en-us/library/ms716845.aspx)  
  
 *狀態* \(可省略\)  
 成員變數，用來存放本篇文章中的狀態。  狀態表示資料行的值是否為資料值或某些其他值，例如 **NULL**。  可能的值，請參閱[狀態](https://msdn.microsoft.com/en-us/library/ms722617.aspx) 在  *OLE DB 程式設計人員參考*。  
  
 *長度* \(可省略\)  
 成員變數，用來存放資料行的大小，以位元組為單位。  
  
## 備註  
 **db\_param** 會定義您所使用的參數中命令的方式。 因此您使用與 **db\_command**。  例如，您可以使用 **db\_param** SQL 的查詢或預存程序中的參數的繫結。  問號 \(?\)、 標示出來的預存程序中的參數，您應該參數的顯示的順序中繫結的資料成員。  
  
 **db\_param** 用來分隔成員資料是以 OLE DB 可參與`ICommandWithParameters`\-根據繫結。  它會將參數型別 \(輸入或輸出\)、 OLE DB 型別、 整數位數、 小數位數、 狀態和長度為指定的參數。  這個屬性會插入 OLE DB 消費者巨集 BEGIN\_PARAM\_MAP...  END\_PARAM\_MAP。  您將標記與每個成員 **db\_param** 屬性將佔用的 COLUMN\_ENTRY 形式對應中的一個項目。  
  
 **db\_param** 為一起使用，  [db\_table](../windows/db-table.md) 或 [db\_command](../windows/db-command.md) 屬性。  
  
 當消費者屬性提供者會將這個屬性套用至類別時，編譯器將類別重新指定成 \_*YourClassName*存取子，其中  *YourClassName* 是類別的名稱，而且編譯器也會建立一個名為 *YourClassName，* 衍生 \_*YourClassName*存取子。  在 \[類別檢視\] 中，您會看到這兩個類別。  
  
## 範例  
 下列範例會建立根據 SalesbyYear 預存程序，在 Northwind 資料庫的指令類別。  它將相關聯的預存程序的第一個參數`m_RETURN_VALUE`變數，並定義它為輸出參數。  它將相關聯的 \(輸入\) 的最後兩個參數，與`m_Beginning_Date`和`m_Ending_Date`。  
  
 下列範例將`nOutput`變數使用輸出參數。  
  
```  
// db_param.cpp  
// compile with: /LD  
#include <atlbase.h>  
#include <atlplus.h>  
#include <atldbcli.h>  
  
[ db_source(L"my_connection_string"),   
  db_command(L"{ ? = CALL dbo.\"Sales by Year\"(?,?) }")   
]  
struct CSalesbyYear {  
   DBSTATUS m_dwShippedDateStatus;  
   DBSTATUS m_dwOrderIDStatus;  
   DBSTATUS m_dwSubtotalStatus;  
   DBSTATUS m_dwYearStatus;  
  
   DBLENGTH m_dwShippedDateLength;  
   DBLENGTH m_dwOrderIDLength;  
   DBLENGTH m_dwSubtotalLength;  
   DBLENGTH m_dwYearLength;  
  
   // Bind columns  
   [ db_column("1", status="m_dwShippedDateStatus", length="m_dwShippedDateLength") ] DBTIMESTAMP m_ShippedDate;  
   [ db_column("2", status="m_dwOrderIDStatus", length="m_dwOrderIDLength") ] LONG m_OrderID;  
   [ db_column("3", status="m_dwSubtotalStatus", length="m_dwSubtotalLength") ] CURRENCY m_Subtotal;  
   [ db_column("4", status="m_dwYearStatus", length="m_dwYearLength") ] TCHAR m_Year[31];  
  
   // Bind parameters  
   [ db_param("1", paramtype="DBPARAMIO_OUTPUT") ] LONG m_RETURN_VALUE;  
   [ db_param("2", paramtype="DBPARAMIO_INPUT") ] DBTIMESTAMP m_Beginning_Date;  
   [ db_param("3", paramtype="DBPARAMIO_INPUT") ] DBTIMESTAMP m_Ending_Date;  
};  
```  
  
## 需求  
  
### 屬性內容  
  
|||  
|-|-|  
|**適用於**|**類別**， `struct`，成員、 方法、 本機|  
|**可重複**|否|  
|**必要的屬性**|None|  
|**無效的屬性**|None|  
  
 如需有關屬性內容的詳細資訊，請參閱[屬性內容](../windows/attribute-contexts.md)。  
  
## 請參閱  
 [OLE DB Consumer Attributes](../windows/ole-db-consumer-attributes.md)   
 [Attributes Samples](http://msdn.microsoft.com/zh-tw/558ebdb2-082f-44dc-b442-d8d33bf7bdb8)