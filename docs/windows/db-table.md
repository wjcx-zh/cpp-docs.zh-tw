---
title: db_table |Microsoft Docs
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
ms.openlocfilehash: 6e084a0f876d0b2598a5317e15057162c602474a
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/17/2018
ms.locfileid: "45717115"
---
# <a name="dbtable"></a>db_table

開啟 OLE DB 資料表。

## <a name="syntax"></a>語法

```cpp
[ db_table(
   db_table,
   name,
   source_name,
   hresult
) ]
```

#### <a name="parameters"></a>參數

*db_table*  
字串，指定資料庫資料表 （例如 「 產品 」） 的名稱。

*name*  
（選擇性）您用來處理與資料表的控制代碼的名稱。 如果您想要傳回一個以上的資料列的結果，您必須指定此參數。 **db_table**會產生具有指定的變數*名稱*，可用來周遊資料列集或執行多個動作查詢。

*source_name*  
（選擇性）`CSession`變數或具有類別的執行個體`db_source`屬性套用至它在其上執行命令。 請參閱 [db_source](../windows/db-source.md)。

*hresult*  
（選擇性）識別將會收到此資料庫命令的 HRESULT 的變數。 如果變數不存在，則屬性會自動予以插入。

## <a name="remarks"></a>備註

**db_table**會建立[CTable](../data/oledb/ctable-class.md) OLE DB 消費者用來開啟資料表的物件。 您可以使用這個屬性只能在類別層級;您無法使用它內嵌。 使用 `db_column`繫結至變數; 的資料表資料行使用`db_param`來分隔 （設定的參數類型，因此上） 的參數。

當取用者的屬性提供者會將此屬性套用至類別時，編譯器會重新命名的類別\_ *YourClassName*存取子，其中*YourClassName*是您所指定的名稱類別，而編譯器也會建立一個叫做類別*YourClassName*，其衍生自\_ *YourClassName*存取子。  在 [類別] 檢視中，您會看到這兩個類別。

## <a name="example"></a>範例

下列範例會開啟 [產品] 資料表，以供`CProducts`。

```cpp
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

如需在應用程式中使用這個屬性的範例，請參閱範例[AtlAgent](https://github.com/Microsoft/VCSamples)並[MultiRead](https://github.com/Microsoft/VCSamples)。

## <a name="requirements"></a>需求

### <a name="attribute-context"></a>屬性內容

|||
|-|-|
|**適用於**|**類別**，**結構**|
|**可重複**|否|
|**必要屬性**|無|
|**無效屬性**|無|

如需有關屬性內容的詳細資訊，請參閱 [屬性內容](../windows/attribute-contexts.md)。

## <a name="see-also"></a>另請參閱

[OLE DB 消費者屬性](../windows/ole-db-consumer-attributes.md)  
