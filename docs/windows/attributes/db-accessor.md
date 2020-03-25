---
title: db_accessor （C++ COM 屬性）
ms.date: 10/02/2018
f1_keywords:
- vc-attr.db_accessor
helpviewer_keywords:
- db_accessor attribute
ms.assetid: ec407a9f-24d7-4822-96d4-7cc6a0301815
ms.openlocfilehash: 1e9725dad39974b828d87bd8b4cdeac623f4e12f
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80214860"
---
# <a name="db_accessor"></a>db_accessor

`db_column` 參與 `IAccessor`型系結的屬性群組。

## <a name="syntax"></a>語法

```cpp
[ db_accessor(num, auto) ]
```

#### <a name="parameters"></a>參數

*num*<br/>
指定存取子編號（以零為基底的整數索引）。 您必須使用整數或定義的值，以遞增的順序來指定存取子數位。

*auto*<br/>
布林值，指定是否自動抓取存取子（TRUE）或不抓取（FALSE）。

## <a name="remarks"></a>備註

**db_accessor**會針對相同類別或函式中的後續 `db_column` 和 `db_param` 屬性，定義基礎 OLE DB 存取子。 **db_accessor**可在成員層級使用，而且可用來將參與 OLE DB `IAccessor`型系結的 `db_column` 屬性分組。 它會與 `db_table` 或 `db_command` 屬性一起使用。 呼叫這個屬性類似于呼叫[BEGIN_ACCESSOR](../../data/oledb/begin-accessor.md)並[END_ACCESSOR](../../data/oledb/end-accessor.md)宏。

**db_accessor**會產生資料列集，並將它系結至對應的存取子對應。 如果您未呼叫**db_accessor**，將會自動產生存取子0，而且所有資料行系結都會對應至此存取子區塊。

**db_accessor**將資料庫資料行系結分組到一個或多個存取子。 如需您需要使用多個存取子之案例的討論，請參閱在資料列[集上使用多個存取子](../../data/oledb/using-multiple-accessors-on-a-rowset.md)。 另請參閱[使用者記錄](../../data/oledb/user-records.md)中的「多個存取子的使用者記錄支援」。

當取用者屬性提供者將此屬性套用至類別時，編譯器會將類別重新命名為 \_*YourClassName*存取子，其中*YourClassName*是您提供給類別的名稱，而編譯器也會建立名為*YourClassName*的類別，其衍生自 \_*YourClassName*存取子。  在 [類別] 檢視中，您會看到這兩個類別。

## <a name="example"></a>範例

下列範例會使用**db_accessor** ，將 [Orders] 資料表中的資料行，從 Northwind 資料庫分組成兩個存取子。 存取子0是自動存取子，而且存取子1不是。

```cpp
// cpp_attr_ref_db_accessor.cpp
// compile with: /LD /link /OPT:NOREF
#define _ATL_ATTRIBUTES
#include <atlbase.h>
#include <atldbcli.h>

[ db_command(L"SELECT LastName, FirstName FROM Orders") ]
class CEmployees {
public:
   [ db_accessor(0, TRUE) ];
   [ db_column("1") ] LONG m_OrderID;
   [ db_column("2") ] TCHAR m_CustomerID[6];
   [ db_column("4") ] DBTIMESTAMP m_OrderDate;

   [ db_accessor(1, FALSE) ];
   [ db_column("8") ] CURRENCY m_Freight;
};
```

## <a name="requirements"></a>需求

### <a name="attribute-context"></a>屬性內容

|||
|-|-|
|**適用於**|屬性區塊|
|**可重複**|否|
|**必要屬性**|None|
|**無效屬性**|None|

如需有關屬性內容的詳細資訊，請參閱 [屬性內容](cpp-attributes-com-net.md#contexts)。

## <a name="see-also"></a>另請參閱

[OLE DB 消費者屬性](ole-db-consumer-attributes.md)
