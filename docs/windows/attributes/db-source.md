---
title: db_source (C++ COM 屬性)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.db_source
helpviewer_keywords:
- db_source attribute
ms.assetid: 0ec8bbf7-ade2-4899-bf4c-8608b92779bc
ms.openlocfilehash: 884cab78d64c20bef00958f0cc0319281fd69921
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59026327"
---
# <a name="dbsource"></a>db_source

建立資料來源的連接。

## <a name="syntax"></a>語法

```cpp
[ db_source(db_source, name, hresult) ]
```

### <a name="parameters"></a>參數

*db_source*<br/>
用來連接到資料來源連接字串。 如需連接字串的格式，請參閱[連接字串和資料連結](/previous-versions/windows/desktop/ms718376(v=vs.85))在 Microsoft Data Access Components (MDAC) SDK。

*name*<br/>
（選擇性）當您使用**db_source**類別中上,*名稱*是具有資料來源物件的執行個體**db_source**套用屬性 （請參閱範例 1）。 當您使用**db_source**在方法實作中，內嵌*名稱*是一個變數 （本機方法），可用來存取資料來源 （請參閱範例 2）。 您傳遞這*名稱*要*source_name*參數`db_command`命令相關聯的資料來源。

*hresult*<br/>
（選擇性）識別將會收到此資料庫命令的 HRESULT 的變數。 如果變數不存在，則屬性會自動予以插入。

## <a name="remarks"></a>備註

**db_source**會建立[CDataSource](../../data/oledb/cdatasource-class.md)並[CSession](../../data/oledb/csession-class.md)物件都代表與 OLE DB 取用者資料來源的連線。

當您使用**db_source**對類別、`CSession`物件會變成類別的成員。

當您使用**db_source**在方法中，插入的程式碼會執行方法範圍內，`CSession`物件建立成本機變數。

**db_source**類別或方法中新增資料來源屬性。 它用於搭配`db_command`(這個方法會接受*db_source* *名稱*參數做為其*source_name*參數)。

當取用者的屬性提供者會將此屬性套用至類別時，編譯器會重新命名的類別\_ *YourClassName*存取子，其中*YourClassName*是您所指定的名稱類別，而編譯器也會建立一個叫做類別*YourClassName*，其衍生自\_ *YourClassName*存取子。  在 [類別] 檢視中，您會看到這兩個類別。

如需在應用程式中使用這個屬性的範例，請參閱範例[AtlAgent](https://github.com/Microsoft/VCSamples)並[MultiRead](https://github.com/Microsoft/VCSamples)。

## <a name="example"></a>範例

此範例會呼叫**db_source**類別來建立資料來源的連接上`ds`使用 Northwind 資料庫。 `ds` 資料來源，可用於在內部的控制代碼`CMyCommand`類別。

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
|**適用於**|**類別**， **struct**、 member、 method、 local|
|**可重複**|否|
|**必要屬性**|None|
|**無效屬性**|None|

如需有關屬性內容的詳細資訊，請參閱 [屬性內容](cpp-attributes-com-net.md#contexts)。

## <a name="see-also"></a>另請參閱

[OLE DB 消費者屬性](ole-db-consumer-attributes.md)
