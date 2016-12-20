---
title: "db_column | Microsoft Docs"
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
  - "vc-attr.db_column"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "db_column attribute"
ms.assetid: 58da4afc-f69c-4ae6-af9a-3f9515f56081
caps.latest.revision: 12
caps.handback.revision: 12
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# db_column
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

將指定的資料行繫結至資料列集的變數。  
  
## 語法  
  
```  
  
      [ db_column(   
   ordinal,   
   dbtype,   
   precision,   
   scale,   
   status,   
   length   
) ]  
```  
  
#### 參數  
 `ordinal`  
 序數的資料行編號 \(**DBCOLUMNINFO** 序數\) 或要將資料繫結至資料列集的欄位相對應的資料行名稱 \(ANSI 或 Unicode 字串\)。  如果您使用數字，則可以略過連續的序數 \(例如： 1、 2、 3、 5\)。  如果您使用的 OLE DB 提供者支援的話，名稱可以包含空格。  例如，您可以使用下列格式之一：  
  
```  
[db_column("2")] TCHAR szCity[30];  
[db_column(L"city_name")] TCHAR szCity[30];  
```  
  
 *dbtype*  \(可省略\)  
 OLE DB [型別指示器](https://msdn.microsoft.com/en-us/library/ms711251.aspx)的資料行的項目。  
  
 *精確度* \(可省略\)  
 資料行的項目所使用的整數位數。  如需詳細資訊，請參閱說明`bPrecision`中的項目 [DBBINDING 結構](https://msdn.microsoft.com/en-us/library/ms716845.aspx)  
  
 *小數位數* \(可省略\)  
 要用於資料行的項目小數位數。  如需詳細資訊，請參閱說明`bScale`中的項目 [DBBINDING 結構](https://msdn.microsoft.com/en-us/library/ms716845.aspx)  
  
 *狀態* \(可省略\)  
 成員變數，用來存放本篇文章中的狀態。  狀態表示資料行的值是否為資料值或某些其他值，例如 **NULL**。  可能的值，請參閱[狀態](https://msdn.microsoft.com/en-us/library/ms722617.aspx) 在  *OLE DB 程式設計人員參考*。  
  
 *長度* \(可省略\)  
 成員變數，用來存放資料行的大小，以位元組為單位。  
  
## 備註  
 **db\_column** 會指定的資料表的資料行繫結至資料列集的變數。  它用來分隔成員資料是以 OLE DB 可參與`IAccessor`為基礎的繫結。  這個屬性會設定通常使用 OLE DB 消費者巨集來定義資料行對應 [BEGIN\_COLUMN\_MAP](../data/oledb/begin-column-map.md)，  [END\_COLUMN\_MAP](../data/oledb/end-column-map.md)，以及  [COLUMN\_ENTRY](../data/oledb/column-entry.md)。  這些操作 OLE DB  [DBBINDING 結構](https://msdn.microsoft.com/en-us/library/ms716845.aspx)要繫結指定的資料行。  您將標記與每個成員 **db\_column** 屬性將佔用資料行對應中的資料行的項目表單中的一個項目。  因此，您可以呼叫這個屬性會放置的資料行對應，也就是在命令或資料表類別。  
  
 使用 **db\_column** 是配合 [db\_table](../windows/db-table.md) 或 [db\_command](../windows/db-command.md) 屬性。  
  
 當消費者屬性提供者會將這個屬性套用至類別時，編譯器將類別重新指定成 \_*YourClassName*存取子，其中  *YourClassName* 是類別的名稱，而且編譯器也會建立一個名為 *YourClassName，* 衍生 \_*YourClassName*存取子。  在 \[類別檢視\] 中，您會看到這兩個類別。  
  
 有關使用應用程式中，這個屬性的範例，請參閱 「 範例 [AtlAgent](http://msdn.microsoft.com/zh-tw/52bef5da-c1a0-4223-b4e6-9e464b6db409)，以及  [MultiRead](http://msdn.microsoft.com/zh-tw/5a2a915a-77dc-492f-94b2-1b809995dd5e)。  
  
## 範例  
 本範例將資料行繫結至資料表中**長**資料成員，並指定狀態和長度的欄位。  
  
```  
// db_column_1.cpp  
// compile with: /LD  
#include <atlbase.h>  
#include <atlplus.h>  
#include <atldbcli.h>  
  
[ db_command(L"Select * from Products") ]  
class CProducts {  
   DBSTATUS m_dwProductIDStatus;  
   DBLENGTH m_dwProductIDLength;  
  
   [ db_column("1", status="m_dwProductIDStatus", length="m_dwProductIDLength") ] LONG m_ProductID;  
};  
```  
  
## 範例  
 這個範例會繫結至的四個資料行**長**，為字元字串、 時間戳記，以及  **DB\_NUMERIC** 依此順序的整數。  
  
```  
// db_column_2.cpp  
// compile with: /LD  
#include <atlbase.h>  
#include <atlplus.h>  
#include <atldbcli.h>  
  
[ db_command(L"Select * from Products") ]  
class CProducts {  
   [db_column("1")] LONG m_OrderID;  
   [db_column("2")] TCHAR m_CustomerID[6];  
   [db_column("4")] DB_NUMERIC m_OrderDate;     
   [db_column("7", dbtype="DBTYPE_NUMERIC")] DB_NUMERIC m_ShipVia;  
};  
```  
  
## 需求  
  
### 屬性內容  
  
|||  
|-|-|  
|**適用於**|**類別**， `struct`，成員、 方法|  
|**可重複**|否|  
|**必要的屬性**|None|  
|**無效的屬性**|None|  
  
 如需有關屬性內容的詳細資訊，請參閱[屬性內容](../windows/attribute-contexts.md)。  
  
## 請參閱  
 [OLE DB Consumer Attributes](../windows/ole-db-consumer-attributes.md)   
 [Class Attributes](../windows/class-attributes.md)   
 [Attributes Samples](http://msdn.microsoft.com/zh-tw/558ebdb2-082f-44dc-b442-d8d33bf7bdb8)