---
title: db_column （c + + COM 屬性）
ms.date: 10/02/2018
f1_keywords:
- vc-attr.db_column
helpviewer_keywords:
- db_column attribute
ms.assetid: 58da4afc-f69c-4ae6-af9a-3f9515f56081
ms.openlocfilehash: b78fb081895b7a3e8f0e266810cd19d1b2792240
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87222143"
---
# <a name="db_column"></a>db_column

將指定的資料行系結至資料列集中的變數。

## <a name="syntax"></a>語法

```cpp
[ db_column(ordinal, dbtype, precision, scale, status, length) ]
```

### <a name="parameters"></a>參數

*序數*<br/>
對應至資料列集中之欄位（用來系結資料）的序數資料行編號（ `DBCOLUMNINFO` 序數）或資料行名稱（ANSI 或 Unicode 字串）。 如果您使用數位，可以略過連續的序數（例如：1、2、3、5）。 如果您使用的 OLE DB 提供者支援，名稱可能會包含空格。 例如，您可以使用下列其中一種格式：

```cpp
[db_column("2")] TCHAR szCity[30];
[db_column(L"city_name")] TCHAR szCity[30];
```

*dbtype*<br/>
選擇性資料行專案的 OLE DB[類型指標](/previous-versions/windows/desktop/ms711251(v=vs.85))。

*有效位數*<br/>
選擇性要用於資料行專案的有效位數。 如需詳細資訊，請參閱 `bPrecision` [DBBINDING 結構](/previous-versions/windows/desktop/ms716845(v=vs.85))之元素的描述

*scale*<br/>
選擇性要用於資料行專案的尺規。 如需詳細資訊，請參閱 `bScale` [DBBINDING 結構](/previous-versions/windows/desktop/ms716845(v=vs.85))的元素描述

*status*<br/>
選擇性用來保存此資料行之狀態的成員變數。 狀態會指出資料行值是否為數據值或其他值，例如 Null。 如需可能的值，請參閱*OLE DB 程式設計人員參考*中的[狀態](/previous-versions/windows/desktop/ms722617(v=vs.85))。

*length*<br/>
選擇性用來保存資料行大小的成員變數（以位元組為單位）。

## <a name="remarks"></a>備註

**db_column**將指定的資料表資料行系結至資料列集中的變數。 它會分隔可以參與 OLE DB 型系結的成員資料 `IAccessor` 。 這個屬性會使用 OLE DB 取用者宏[BEGIN_COLUMN_MAP](../../data/oledb/begin-column-map.md)、 [END_COLUMN_MAP](../../data/oledb/end-column-map.md)和[COLUMN_ENTRY](../../data/oledb/column-entry.md)，設定正常定義的資料行對應。 這些會操控 OLE DB 的[DBBINDING 結構](/previous-versions/windows/desktop/ms716845(v=vs.85))，以系結指定的資料行。 您以**db_column**屬性標記的每個成員，都會以資料行專案的形式，在資料行對應中佔用一個專案。 因此，您會呼叫這個屬性，您會在其中放置資料行對應，也就是在命令或資料表類別中。

搭配[db_table](db-table.md)或[db_command](db-command.md)屬性使用**db_column** 。

當取用者屬性提供者將此屬性套用至類別時，編譯器會將類別重新命名為 \_ *YourClassName*存取子，其中*YourClassName*是您為類別提供的名稱，而編譯器也會建立名為*YourClassName*的類別，其衍生自 \_ *YourClassName*存取子。  在 [類別] 檢視中，您會看到這兩個類別。

如需應用程式中使用此屬性的範例，請參閱[MultiRead](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/ATL/OLEDB/Consumer)。

## <a name="example"></a>範例

這個範例會將資料表中的資料行系結至 **`long`** 資料成員，並指定狀態和長度欄位。

```cpp
// db_column_1.cpp
// compile with: /LD
#include <atlbase.h>
#include <atlplus.h>
#include <atldbcli.h>

[ db_command(L"Select * from Products") ]
class CProducts {
   DBSTATUS m_dwProductIDStatus;
   DBLENGTH m_dwProductIDLength;

   [ db_column("1", status="m_dwProductIDStatus", length="m_dwProductIDLength") ] LONG m_ProductID;
};
```

## <a name="example"></a>範例

這個範例會依序將四個數據行系結至 **`long`** 、字元字串、時間戳記和 `DB_NUMERIC` 整數。

```cpp
// db_column_2.cpp
// compile with: /LD
#include <atlbase.h>
#include <atlplus.h>
#include <atldbcli.h>

[ db_command(L"Select * from Products") ]
class CProducts {
   [db_column("1")] LONG m_OrderID;
   [db_column("2")] TCHAR m_CustomerID[6];
   [db_column("4")] DB_NUMERIC m_OrderDate;
   [db_column("7", dbtype="DBTYPE_NUMERIC")] DB_NUMERIC m_ShipVia;
};
```

## <a name="requirements"></a>需求

### <a name="attribute-context"></a>屬性內容

|||
|-|-|
|**適用於**|**`class`**、 **`struct`** 、member、method|
|**可重複**|否|
|**必要的屬性**|無|
|**無效屬性**|無|

如需有關屬性內容的詳細資訊，請參閱 [屬性內容](cpp-attributes-com-net.md#contexts)。

## <a name="see-also"></a>另請參閱

[OLE DB 取用者屬性](ole-db-consumer-attributes.md)<br/>
[類別屬性](class-attributes.md)
