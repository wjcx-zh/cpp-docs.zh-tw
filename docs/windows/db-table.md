---
title: "db_table | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "vc-attr.db_table"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "db_table attribute"
ms.assetid: ff9eb957-4e6d-4175-afcc-fd8ea916cec0
caps.latest.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 10
---
# db_table
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

OLE DB 表格會跚  
  
## 語法  
  
```  
  
      [ db_table(   
   db_table,   
   name,   
   source_name,   
   hresult   
) ]  
```  
  
#### 參數  
 *db\_table*  
 字串，指定資料庫資料表的名稱 \(例如，\[產品\]\)。  
  
 *名稱* \(可省略\)  
 您用來處理與資料表的控制代碼的名稱。  如果您想要傳回的結果的多個資料列，您必須指定此參數。  **db\_table** 會產生具有指定變數*名稱* ，可以用來周遊資料列集或執行多個動作查詢。  
  
 *source\_name*  \(可省略\)  
 `CSession`變數或具有類別的執行個體`db_source`屬性套用至它執行的命令。  請參閱 [db\_source](../windows/db-source.md)。  
  
 `hresult` \(選擇項\)  
 識別要接收之變數`HRESULT`的這個資料庫\] 指令。  如果變數不存在，它會自動插入屬性。  
  
## 備註  
 **db\_table** 會建立 [CTable](../data/oledb/ctable-class.md) 物件，它由 OLE DB 消費者開啟資料表。  您可以使用這個屬性只能在類別層級。 您不能使用內嵌。  使用 **db\_column** 若要將資料表資料行繫結至變數。 使用 **db\_param** 來分隔 \(設定的參數型別，因此在上\) 的參數。  
  
 當消費者屬性提供者會將這個屬性套用至類別時，編譯器將類別重新指定成 \_*YourClassName*存取子，其中  *YourClassName* 是類別的名稱，而且編譯器也會建立一個名為 *YourClassName，* 衍生 \_*YourClassName*存取子。  在 \[類別檢視\] 中，您會看到這兩個類別。  
  
## 範例  
 下列範例會開啟 \[產品\] 資料表，供使用的`CProducts`。  
  
```  
// db_table.cpp  
// compile with: /LD  
#include <atlbase.h>  
#include <atlplus.h>  
#include <atldbcli.h>  
  
[ db_table(L"dbo.Products") ]  
class CProducts {  
   [ db_column("1") ] LONG m_ProductID;  
};  
```  
  
 如需在應用程式中使用這個屬性的範例，請參閱範例 [AtlAgent](http://msdn.microsoft.com/zh-tw/52bef5da-c1a0-4223-b4e6-9e464b6db409) 和 [MultiRead](http://msdn.microsoft.com/zh-tw/5a2a915a-77dc-492f-94b2-1b809995dd5e)。  
  
## 需求  
  
### 屬性內容  
  
|||  
|-|-|  
|**適用於**|**類別**，`struct`|  
|**可重複**|否|  
|**必要的屬性**|None|  
|**無效的屬性**|None|  
  
 如需有關屬性內容的詳細資訊，請參閱[屬性內容](../windows/attribute-contexts.md)。  
  
## 請參閱  
 [OLE DB Consumer Attributes](../windows/ole-db-consumer-attributes.md)   
 [Attributes Samples](http://msdn.microsoft.com/zh-tw/558ebdb2-082f-44dc-b442-d8d33bf7bdb8)