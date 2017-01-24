---
title: "db_source | Microsoft Docs"
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
  - "vc-attr.db_source"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "db_source attribute"
ms.assetid: 0ec8bbf7-ade2-4899-bf4c-8608b92779bc
caps.latest.revision: 10
caps.handback.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# db_source
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

建立資料來源的連接。  
  
## 語法  
  
```  
  
      [ db_source(   
   db_source,   
   name,   
   hresult   
) ]  
```  
  
#### 參數  
 *db\_source*  
 用來連接到資料來源的連接字串。  連接字串的格式，請參閱[的連接字串和資料連結](https://msdn.microsoft.com/en-us/library/ms718376.aspx)在 Microsoft 資料存取元件 \(MDAC\) SDK。  
  
 *名稱* \(可省略\)  
 當您使用`db_source`類別， *名稱*有的資料來源物件的執行個體`db_source` \(請參閱範例 1\) 套用至它的屬性。  當您使用`db_source`內嵌在方法實作中， *名稱*是變數 \(本機方法\)，可以用來存取資料來源 \(請參閱範例 2\)。  您可以傳遞這*名稱*到`source_name`參數的 **db\_command** 與命令關聯的資料來源。  
  
 `hresult` \(選擇項\)  
 識別要接收之變數`HRESULT`的這個資料庫\] 指令。  如果變數不存在，它會自動插入屬性。  
  
## 備註  
 `db_source`會建立 [CDataSource](../data/oledb/cdatasource-class.md) 和 [CSession](../data/oledb/csession-class.md) 物件，同時代表與 OLE DB 消費者的資料來源的連線。  
  
 當您使用`db_source`類別， `CSession`物件將成為類別的成員。  
  
 當您使用`db_source`在方法中，插入的程式碼將會執行在方法範圍內，以及`CSession`為區域變數建立物件。  
  
 `db_source`新增資料來源屬性至類別或方法內。  它用於搭配 **db\_command** \(負責`db_source`*名稱*參數則做為其`source_name`參數\)。  
  
 當消費者屬性提供者會將這個屬性套用至類別時，編譯器將類別重新指定成 \_*YourClassName*存取子，其中  *YourClassName* 是類別的名稱，而且編譯器也會建立一個名為 *YourClassName，* 衍生 \_*YourClassName*存取子。  在 \[類別檢視\] 中，您會看到這兩個類別。  
  
 如需在應用程式中使用這個屬性的範例，請參閱範例 [AtlAgent](http://msdn.microsoft.com/zh-tw/52bef5da-c1a0-4223-b4e6-9e464b6db409) 和 [MultiRead](http://msdn.microsoft.com/zh-tw/5a2a915a-77dc-492f-94b2-1b809995dd5e)。  
  
## 範例  
 這個範例會呼叫`db_source`類別來建立資料來源的連接上`ds`使用北風資料庫。  `ds`為資料來源，可在內部為控制代碼`CMyCommand`類別。  
  
```  
// db_source_1.cpp  
// compile with: /LD  
#include <atlbase.h>  
#include <atlplus.h>  
#include <atldbcli.h>  
  
[  
  db_source(L"my_connection_string", name="ds"),  
  db_command(L"select * from Products")  
]  
class CMyCommand {};  
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