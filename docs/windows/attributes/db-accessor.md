---
title: 'db_accessor (c + + COM 屬性) '
ms.date: 10/02/2018
f1_keywords:
- vc-attr.db_accessor
helpviewer_keywords:
- db_accessor attribute
ms.assetid: ec407a9f-24d7-4822-96d4-7cc6a0301815
ms.openlocfilehash: 559838201e3d1c425b6b1bf7f3650d9635c44c97
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/25/2020
ms.locfileid: "88833136"
---
# <a name="db_accessor"></a>db_accessor

群組參與以系結為基礎之系結 `db_column` 的屬性 `IAccessor` 。

## <a name="syntax"></a>語法

```cpp
[ db_accessor(num, auto) ]
```

#### <a name="parameters"></a>參數

*num*<br/>
指定 (以零為基底的整數索引) 的存取子數目。 您必須使用整數或定義的值，以遞增順序指定存取子數位。

*自動*<br/>
布林值，這個值會指定是否自動將存取子 (TRUE) 或未 (FALSE) 取出。

## <a name="remarks"></a>備註

**db_accessor** 定義 `db_column` `db_param` 相同類別或函式中後續和屬性的基礎 OLE DB 存取子。 **db_accessor** 可用於成員層級，而且可用來將 `db_column` 參與 OLE DB 系結的屬性分組 `IAccessor` 。 它會與 `db_table` 或屬性搭配使用 `db_command` 。 呼叫這個屬性類似于呼叫 [BEGIN_ACCESSOR](../../data/oledb/begin-accessor.md) 並 [END_ACCESSOR](../../data/oledb/end-accessor.md) 宏。

**db_accessor** 會產生資料列集，並將它系結至對應的存取子對應。 如果您未呼叫 **db_accessor**，則會自動產生存取子0，而且所有資料行系結都會對應至此存取子區塊。

**db_accessor** 將資料庫資料行系結群組至一個或多個存取子。 如需使用多個存取子之案例的討論，請參閱在資料列 [集上使用多重存取子](../../data/oledb/using-multiple-accessors-on-a-rowset.md)。 另請參閱 [使用者記錄](../../data/oledb/user-records.md)中的「多個存取子的使用者記錄支援」。

當取用者屬性提供者將此屬性套用至類別時，編譯器會將類別重新命名為 \_ *YourClassName*存取子，其中*YourClassName*是您賦予類別的名稱，而編譯器也會建立名為*YourClassName*的類別，該類別衍生自 \_ *YourClassName*存取子。  在 [類別] 檢視中，您會看到這兩個類別。

## <a name="example"></a>範例

下列範例會使用 **db_accessor** ，將 Orders 資料表中的資料行從 Northwind 資料庫群組到兩個存取子。 存取子0是自動存取子，而存取子1則不是。

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

## <a name="requirements"></a>規格需求

| 屬性內容 | 值 |
|-|-|
|**適用於**|屬性區塊|
|**重複**|否|
|**必要的屬性**|無|
|**無效屬性**|無|

如需有關屬性內容的詳細資訊，請參閱 [屬性內容](cpp-attributes-com-net.md#contexts)。

## <a name="see-also"></a>另請參閱

[OLE DB 取用者屬性](ole-db-consumer-attributes.md)
