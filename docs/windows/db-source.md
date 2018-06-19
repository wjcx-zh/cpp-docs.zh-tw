---
title: db_source |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.db_source
dev_langs:
- C++
helpviewer_keywords:
- db_source attribute
ms.assetid: 0ec8bbf7-ade2-4899-bf4c-8608b92779bc
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: b826e5d630b52062892001c26efda01b5c7293f4
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/08/2018
ms.locfileid: "33873715"
---
# <a name="dbsource"></a>db_source
建立資料來源的連接。  
  
## <a name="syntax"></a>語法  
  
```  
  
      [ db_source(   
   db_source,   
   name,   
   hresult   
) ]  
```  
  
#### <a name="parameters"></a>參數  
 *db_source*  
 用來連接到資料來源連接字串。 如需連接字串的格式，請參閱[連接字串] 和 [資料連結](https://msdn.microsoft.com/en-us/library/ms718376.aspx)在 Microsoft Data Access Components (MDAC) SDK。  
  
 *name* (選擇性)  
 當您使用`db_source`對類別、*名稱*具有的資料來源物件的執行個體`db_source`（請參閱範例 1） 它所套用的屬性。 當您使用`db_source`在方法實作中，內嵌*名稱*是變數 （本機方法），可以用來存取資料來源 （請參閱範例 2）。 將此變數傳遞*名稱*至`source_name`參數**db_command**與命令相關的資料來源。  
  
 `hresult` (選擇性)  
 識別將接收此資料庫命令之 `HRESULT` 的變數。 如果變數不存在，則屬性會自動予以插入。  
  
## <a name="remarks"></a>備註  
 `db_source` 建立[CDataSource](../data/oledb/cdatasource-class.md)和[CSession](../data/oledb/csession-class.md)物件共同代表的 OLE DB 取用者資料來源的連接。  
  
 當您使用`db_source`對類別、`CSession`物件變成類別的成員。  
  
 當您使用`db_source`在方法中，將插入的程式碼執行方法在範圍內，而`CSession`物件建立成本機變數。  
  
 `db_source` 將資料來源屬性加入至類別或方法內。 它用於搭配**db_command** (這個方法會接受`db_source`*名稱*參數做為其`source_name`參數)。  
  
 當取用者屬性提供者會將此屬性套用至類別中時，編譯器會重新命名的類別\_ *YourClassName*存取子，其中*YourClassName*是為您提供的名稱類別，而編譯器也會建立一種類別稱為*YourClassName*，其衍生自\_ *YourClassName*存取子。  在 [類別] 檢視中，您會看到這兩個類別。  
  
 如需應用程式中使用這個屬性的範例，請參閱 「 範例[AtlAgent](http://msdn.microsoft.com/en-us/52bef5da-c1a0-4223-b4e6-9e464b6db409)和[MultiRead](http://msdn.microsoft.com/en-us/5a2a915a-77dc-492f-94b2-1b809995dd5e)。  
  
## <a name="example"></a>範例  
 這個範例會呼叫`db_source`類別來建立資料來源的連接上`ds`使用 Northwind 資料庫。 `ds` 可用在內部的資料來源中的控制代碼`CMyCommand`類別。  
  
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
  
## <a name="requirements"></a>需求  
  
### <a name="attribute-context"></a>屬性內容  
  
|||  
|-|-|  
|**適用於**|**class**、 `struct`、member、method、local|  
|**可重複**|否|  
|**必要屬性**|無|  
|**無效屬性**|無|  
  
 如需有關屬性內容的詳細資訊，請參閱 [屬性內容](../windows/attribute-contexts.md)。  
  
## <a name="see-also"></a>另請參閱  
 [OLE DB 消費者屬性](../windows/ole-db-consumer-attributes.md)   
