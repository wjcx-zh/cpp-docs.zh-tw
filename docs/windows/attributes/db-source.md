---
title: 'db_source (c + + COM 屬性) '
ms.date: 10/02/2018
f1_keywords:
- vc-attr.db_source
helpviewer_keywords:
- db_source attribute
ms.assetid: 0ec8bbf7-ade2-4899-bf4c-8608b92779bc
ms.openlocfilehash: f17a4ea183a24f7bf4e88137f4536ca082efdf85
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/25/2020
ms.locfileid: "88831381"
---
# <a name="db_source"></a>db_source

建立與資料來源的連接。

## <a name="syntax"></a>語法

```cpp
[ db_source(db_source, name, hresult) ]
```

### <a name="parameters"></a>參數

*db_source*<br/>
用來連接到資料來源的連接字串。 如需連接字串的格式，請參閱 Microsoft Data Access Components 中的 [連接字串和資料連結](/previous-versions/windows/desktop/ms718376(v=vs.85)) (MDAC) SDK。

*name*<br/>
 (選擇性) 當您在類別上使用 **Db_source** 時， *name* 會是已套用 **db_source** 屬性之資料來源物件的實例 (請參閱範例 1) 。 當您在方法執行中使用 **db_source** 內嵌時， *name* 是方法的變數 (區域) 可以用來存取資料來源 (請參閱範例 2) 。 您可以將此 *名稱* 傳遞給的 *source_name* 參數 `db_command` ，將資料來源與命令建立關聯。

*hresult*<br/>
 (選擇性) 識別將接收此資料庫命令之 HRESULT 的變數。 如果變數不存在，則屬性會自動予以插入。

## <a name="remarks"></a>備註

**db_source** 會建立 [CDataSource](../../data/oledb/cdatasource-class.md) 和 [CSession](../../data/oledb/csession-class.md) 物件，這些物件會一起代表與 OLE DB 取用者資料來源的連接。

當您在類別上使用 **db_source** 時， `CSession` 物件會成為類別的成員。

當您在方法中使用 **db_source** 時，會在方法範圍內執行插入的程式碼，並將 `CSession` 物件建立為本機變數。

**db_source** 會將資料來源屬性加入至類別或方法內。 它會搭配使用 `db_command` *db_source* *name* 參數做為 *source_name* 參數) 的 (一起使用。

當取用者屬性提供者將此屬性套用至類別時，編譯器會將類別重新命名為 \_ *YourClassName*存取子，其中*YourClassName*是您賦予類別的名稱，而編譯器也會建立名為*YourClassName*的類別，該類別衍生自 \_ *YourClassName*存取子。  在 [類別] 檢視中，您會看到這兩個類別。

如需在應用程式中使用這個屬性的範例，請參閱 [MultiRead](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/ATL/OLEDB/Consumer)。

## <a name="example"></a>範例

這個範例會呼叫類別上的 **db_source** ，以使用 Northwind 資料庫建立資料來源的連接 `ds` 。 `ds` 這是資料來源的控制碼，可以在內部用於 `CMyCommand` 類別。

```cpp
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

## <a name="requirements"></a>規格需求

| 屬性內容 | 值 |
|-|-|
|**適用於**|**`class`**、 **`struct`** 、member、method、local|
|**重複**|否|
|**必要的屬性**|無|
|**無效屬性**|無|

如需有關屬性內容的詳細資訊，請參閱 [屬性內容](cpp-attributes-com-net.md#contexts)。

## <a name="see-also"></a>另請參閱

[OLE DB 取用者屬性](ole-db-consumer-attributes.md)
