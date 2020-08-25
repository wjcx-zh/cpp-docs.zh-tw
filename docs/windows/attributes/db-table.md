---
title: 'db_table (c + + COM 屬性) '
ms.date: 10/02/2018
f1_keywords:
- vc-attr.db_table
helpviewer_keywords:
- db_table attribute
ms.assetid: ff9eb957-4e6d-4175-afcc-fd8ea916cec0
ms.openlocfilehash: dfdf012550359d0658d53b3f67c0619a124b6309
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/25/2020
ms.locfileid: "88834189"
---
# <a name="db_table"></a>db_table

開啟 OLE DB 資料表。

## <a name="syntax"></a>語法

```cpp
[ db_table(db_table, name, source_name, hresult) ]
```

### <a name="parameters"></a>參數

*db_table*<br/>
字串，指定資料庫資料表的名稱 (例如「產品」 ) 。

*name*<br/>
 (選擇性) 用來處理資料表的控制碼名稱。 如果您想要傳回一列以上的結果，則必須指定這個參數。 **db_table** 會產生具有指定之 *名稱* 的變數，可用來進行資料列集或執行多個動作查詢。

*source_name*<br/>
 (選擇性的) `CSession` 變數或類別的實例，而該類別的屬性會套用 `db_source` 到命令執行所在的屬性。 請參閱 [db_source](db-source.md)。

*hresult*<br/>
 (選擇性) 識別將接收此資料庫命令之 HRESULT 的變數。 如果變數不存在，則屬性會自動予以插入。

## <a name="remarks"></a>備註

**db_table** 會建立 [CTable](../../data/oledb/ctable-class.md) 物件，供 OLE DB 取用者用來開啟資料表。 您只能在類別層級使用此屬性。您無法使用內嵌。 用 `db_column` 來將資料表資料行系結至變數; 使用 `db_param` 來分隔 (設定參數類型，以及) 參數。

當取用者屬性提供者將此屬性套用至類別時，編譯器會將類別重新命名為 \_ *YourClassName*存取子，其中*YourClassName*是您賦予類別的名稱，而編譯器也會建立名為*YourClassName*的類別，該類別衍生自 \_ *YourClassName*存取子。  在 [類別] 檢視中，您會看到這兩個類別。

## <a name="example"></a>範例

下列範例會開啟 Products 資料表以供使用 `CProducts` 。

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

如需在應用程式中使用這個屬性的範例，請參閱 [MultiRead](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/ATL/OLEDB/Consumer)。

## <a name="requirements"></a>規格需求

| 屬性內容 | 值 |
|-|-|
|**適用於**|**`class`**, **`struct`**|
|**重複**|否|
|**必要的屬性**|無|
|**無效屬性**|無|

如需有關屬性內容的詳細資訊，請參閱 [屬性內容](cpp-attributes-com-net.md#contexts)。

## <a name="see-also"></a>另請參閱

[OLE DB 取用者屬性](ole-db-consumer-attributes.md)
