---
title: "db_accessor | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "vc-attr.db_accessor"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "db_accessor attribute"
ms.assetid: ec407a9f-24d7-4822-96d4-7cc6a0301815
caps.latest.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 11
---
# db_accessor
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

群組 **db\_column** 參與屬性`IAccessor`為基礎的繫結。  
  
## 語法  
  
```  
  
      [ db_accessor(   
   num,   
   auto   
) ]  
```  
  
#### 參數  
 *num*  
 指定存取子 \(以零起始的整數索引\)。  您必須指定存取子以遞增的數字排序，請使用整數或定義的值。  
  
 *自動*  
 布林值，指出是否自動擷取存取子 \(**，則為 TRUE**\) 或未擷取 \(**，則為 FALSE**\)。  
  
## 備註  
 **db\_accessor** 為基礎的 OLE DB 存取子會定義後續 **db\_column** 和 **db\_param** 在相同的類別或函式中的屬性。  **db\_accessor** 是使用在成員層級，用來群組 **db\_column** 參與 OLE DB 屬性`IAccessor`\-基礎繫結。  請搭配使用 **db\_table** 或 **db\_command** 屬性。  呼叫這個屬性是類似於撥號 [BEGIN\_ACCESSOR](../data/oledb/begin-accessor.md) 和 [END\_ACCESSOR](../data/oledb/end-accessor.md) 巨集。  
  
 **db\_accessor** 會產生一個資料列集，並將它連結到相對應的存取子對應。  如果您不會呼叫 **db\_accessor**、 存取子 0 會自動產生，以及所有的資料行繫結會對應到這個存取子區塊。  
  
 **db\_accessor** 群組的資料庫資料行繫結至一或多個存取子。  您要使用多重存取子案例探討，請參閱[在資料列集上使用多重存取子](../data/oledb/using-multiple-accessors-on-a-rowset.md)。  在 \[請參閱 「 使用者資料錄支援的多重存取子" [使用者資料錄](../data/oledb/user-records.md)。  
  
 當消費者屬性提供者會將這個屬性套用至類別時，編譯器將類別重新指定成 \_*YourClassName*存取子，其中  *YourClassName* 是類別的名稱，而且編譯器也會建立一個名為 *YourClassName，* 衍生 \_*YourClassName*存取子。  在 \[類別檢視\] 中，您會看到這兩個類別。  
  
## 範例  
 下列範例會使用 **db\_accessor** 「 訂單 」 資料表中從 Northwind 資料庫成兩個存取子的群組資料行。  存取子 0 為自動存取子和存取子 1 並非。  
  
```  
// cpp_attr_ref_db_accessor.cpp  
// compile with: /LD /link /OPT:NOREF  
#define _ATL_ATTRIBUTES  
#include <atlbase.h>  
#include <atldbcli.h>  
  
[ db_command(L"SELECT LastName, FirstName FROM Orders") ]  
class CEmployees {  
public:  
   [ db_accessor(0, TRUE) ];  
   [ db_column("1") ] LONG m_OrderID;  
   [ db_column("2") ] TCHAR m_CustomerID[6];  
   [ db_column("4") ] DBTIMESTAMP m_OrderDate;   
  
   [ db_accessor(1, FALSE) ];  
   [ db_column("8") ] CURRENCY m_Freight;  
};  
```  
  
## 需求  
  
### 屬性內容  
  
|||  
|-|-|  
|**適用於**|屬性區塊|  
|**可重複**|否|  
|**必要的屬性**|None|  
|**無效的屬性**|None|  
  
 如需有關屬性內容的詳細資訊，請參閱[屬性內容](../windows/attribute-contexts.md)。  
  
## 請參閱  
 [OLE DB Consumer Attributes](../windows/ole-db-consumer-attributes.md)   
 [Attributes Samples](http://msdn.microsoft.com/zh-tw/558ebdb2-082f-44dc-b442-d8d33bf7bdb8)