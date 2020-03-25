---
title: db_source （C++ COM 屬性）
ms.date: 10/02/2018
f1_keywords:
- vc-attr.db_source
helpviewer_keywords:
- db_source attribute
ms.assetid: 0ec8bbf7-ade2-4899-bf4c-8608b92779bc
ms.openlocfilehash: 6346a8d6f60313dc17bbcbad062aa888857f0b67
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80167273"
---
# <a name="db_source"></a>db_source

建立與資料來源的連接。

## <a name="syntax"></a>語法

```cpp
[ db_source(db_source, name, hresult) ]
```

### <a name="parameters"></a>參數

*db_source*<br/>
用來連接到資料來源的連接字串。 如需連接字串的格式，請參閱 Microsoft Data Access Components （MDAC） SDK 中的[連接字串和資料連結](/previous-versions/windows/desktop/ms718376(v=vs.85))。

*name*<br/>
選擇性當您在類別上使用**db_source**時， *name*是已套用**db_source**屬性（請參閱範例1）之資料來源物件的實例。 當您在方法實中使用**db_source**內嵌時， *name*就是可用來存取資料來源的變數（在方法的本機）（請參閱範例2）。 您會將此*名稱*傳遞給 `db_command` 的*source_name*參數，以將資料來源與命令建立關聯。

*hresult*<br/>
選擇性識別將接收此資料庫命令之 HRESULT 的變數。 如果變數不存在，則屬性會自動予以插入。

## <a name="remarks"></a>備註

**db_source**會建立[CDataSource](../../data/oledb/cdatasource-class.md)和[CSession](../../data/oledb/csession-class.md)物件，這兩者會一起代表與 OLE DB 取用者資料來源的連接。

當您在類別上使用**db_source**時，`CSession` 物件會成為類別的成員。

當您在方法中使用**db_source**時，插入的程式碼會在方法範圍內執行，而 `CSession` 物件則會建立為本機變數。

**db_source**會將資料來源屬性加入至類別或方法內。 它會與 `db_command` （採用*db_source* *name*參數作為其*source_name*參數）一起使用。

當取用者屬性提供者將此屬性套用至類別時，編譯器會將類別重新命名為 \_*YourClassName*存取子，其中*YourClassName*是您提供給類別的名稱，而編譯器也會建立名為*YourClassName*的類別，其衍生自 \_*YourClassName*存取子。  在 [類別] 檢視中，您會看到這兩個類別。

如需應用程式中使用此屬性的範例，請參閱[MultiRead](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/ATL/OLEDB/Consumer)。

## <a name="example"></a>範例

這個範例會在類別上呼叫**db_source** ，以使用 Northwind 資料庫建立與資料來源 `ds` 的連接。 `ds` 是資料來源的控制碼，可以在內部用於 `CMyCommand` 類別。

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

## <a name="requirements"></a>需求

### <a name="attribute-context"></a>屬性內容

|||
|-|-|
|**適用於**|**class**、 **struct**、member、method、local|
|**可重複**|否|
|**必要屬性**|None|
|**無效屬性**|None|

如需有關屬性內容的詳細資訊，請參閱 [屬性內容](cpp-attributes-com-net.md#contexts)。

## <a name="see-also"></a>另請參閱

[OLE DB 消費者屬性](ole-db-consumer-attributes.md)
