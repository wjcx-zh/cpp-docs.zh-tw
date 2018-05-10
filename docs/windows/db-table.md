---
title: db_table |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.db_table
dev_langs:
- C++
helpviewer_keywords:
- db_table attribute
ms.assetid: ff9eb957-4e6d-4175-afcc-fd8ea916cec0
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: f482e93f124d73d48d1de66f3feb1779146025d0
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/08/2018
---
# <a name="dbtable"></a>db_table
開啟 OLE DB 資料表。  
  
## <a name="syntax"></a>語法  
  
```  
  
      [ db_table(   
   db_table,   
   name,   
   source_name,   
   hresult   
) ]  
```  
  
#### <a name="parameters"></a>參數  
 *db_table*  
 字串，指定資料庫資料表 （例如，"Products") 的名稱。  
  
 *name* (選擇性)  
 您用來處理與資料表的控制代碼的名稱。 如果您想要傳回的結果的多個資料列，您必須指定這個參數。 **db_table**會產生具有指定的變數*名稱*，可以用來周遊資料列集或執行多個動作的查詢。  
  
 *source_name* (選擇性)  
 命令所執行的 `CSession` 變數或已套用 `db_source` 屬性的類別執行個體。 請參閱 [db_source](../windows/db-source.md)。  
  
 `hresult` (選擇性)  
 識別將接收此資料庫命令之 `HRESULT` 的變數。 如果變數不存在，則屬性會自動予以插入。  
  
## <a name="remarks"></a>備註  
 **db_table**建立[CTable](../data/oledb/ctable-class.md)物件，來開啟資料表供 OLE DB 取用者。 您可以使用這個屬性只能在類別層級;您無法使用內嵌。 使用**db_column**若要將資料表資料行繫結至變數; 使用**db_param**來分隔 （設定參數類型，因此上） 的參數。  
  
 當取用者屬性提供者會將此屬性套用至類別中時，編譯器會重新命名的類別\_ *YourClassName*存取子，其中*YourClassName*是為您提供的名稱類別，而編譯器也會建立一種類別稱為*YourClassName*，其衍生自\_ *YourClassName*存取子。  在 [類別] 檢視中，您會看到這兩個類別。  
  
## <a name="example"></a>範例  
 下列範例會開啟 [產品] 資料表，以供`CProducts`。  
  
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
  
 如需應用程式中使用這個屬性的範例，請參閱 「 範例[AtlAgent](http://msdn.microsoft.com/en-us/52bef5da-c1a0-4223-b4e6-9e464b6db409)和[MultiRead](http://msdn.microsoft.com/en-us/5a2a915a-77dc-492f-94b2-1b809995dd5e)。  
  
## <a name="requirements"></a>需求  
  
### <a name="attribute-context"></a>屬性內容  
  
|||  
|-|-|  
|**適用於**|**class**、 `struct`|  
|**可重複**|否|  
|**必要屬性**|無|  
|**無效屬性**|無|  
  
 如需有關屬性內容的詳細資訊，請參閱 [屬性內容](../windows/attribute-contexts.md)。  
  
## <a name="see-also"></a>另請參閱  
 [OLE DB 消費者屬性](../windows/ole-db-consumer-attributes.md)   
