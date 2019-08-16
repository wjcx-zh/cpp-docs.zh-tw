---
title: 匯總 (C++ COM 屬性)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.aggregates
helpviewer_keywords:
- aggregates attribute
- aggregation [C++]
- aggregate objects [C++], aggregates attribute
- aggregates [C++]
ms.assetid: 67a084c9-941f-474b-a029-9c93b38ebe9a
ms.openlocfilehash: c9e3f84fbc781bd5187ae0c3461a6c8d68a29aa0
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/15/2019
ms.locfileid: "69501875"
---
# <a name="aggregates"></a>彙總

表示物件會彙總 CLSID 所指定的物件。

## <a name="syntax"></a>語法

```cpp
[ aggregates(clsid, variable_name) ]
```

### <a name="parameters"></a>參數

*clsid*<br/>
指定可彙總物件的 CLSID。

*variable_name*<br/>
要插入的變數名稱。 這個變數包含`IUnknown`要匯總之物件的。

## <a name="remarks"></a>備註

套用至物件時， **aggregates** C++ 屬性會實作所彙總物件的外部包裝函式 (透過 `clsid`所指定)。

此屬性需要 [coclass](coclass.md)、 [progid](progid.md)或 [vi_progid](vi-progid.md) 屬性 (或表示上述其中一項的另一個屬性) 也套用至相同的項目。 如果使用任何單一屬性，則會自動套用其他兩項。 例如, 如果`progid`套用, `vi_progid`和`coclass`也會套用。

### <a name="atl-projects"></a>ATL 專案

如果在使用 ATL 的專案內使用此屬性，則屬性的行為會變更。 首先，會在目標物件的 COM 對應中新增下列項目︰

```
COM_INTERFACE_ENTRY_AUTOAGGREGATE_BLIND(_m_spAttrXXX, clsid)
```

其次，也會新增 [DECLARE_GET_CONTROLLING_UNKNOWN](../../atl/reference/aggregation-and-class-factory-macros.md#declare_get_controlling_unknown) 巨集。

## <a name="example"></a>範例

```cpp
// cpp_attr_ref_aggregates.cpp
// compile with: /LD
#define _ATL_ATTRIBUTES
#include "atlbase.h"
#include "atlcom.h"

// requires 'aggregatable.dll'
// see aggregatable attribute to create 'aggregatable.dll'
class DECLSPEC_UUID("1a8369cc-1c91-42c4-befa-5a5d8c9d2529") CMyClass;

[module (name="MYObject")];
[object, uuid("ab006d85-e754-47c5-9ef4-2744ff32a20c")]
__interface IObject
{
};

[ coclass, aggregates(__uuidof(CMyClass)),
  uuid("91cb2c06-8931-432a-baac-206e55c4edfb")]
struct CObject : IObject
{
   int i;
};
```

## <a name="requirements"></a>需求

### <a name="attribute-context"></a>屬性內容

|||
|-|-|
|**適用於**|**class**、 **struct**|
|**可重複**|是|
|**必要屬性**|下列一或多項: `coclass`、 `progid`或`vi_progid`。|
|**無效屬性**|無|

如需有關屬性內容的詳細資訊，請參閱 [屬性內容](cpp-attributes-com-net.md#contexts)。

## <a name="see-also"></a>另請參閱

[COM 屬性](com-attributes.md)<br/>
[類別屬性](class-attributes.md)<br/>
[Typedef、Enum、Union 和 Struct 屬性](typedef-enum-union-and-struct-attributes.md)<br/>
[彙總](/windows/win32/com/aggregation)<br/>
[聚集](/windows/win32/Midl/aggregatable)<br/>
[COM_INTERFACE_ENTRY_AUTOAGGREGATE_BLIND](../../atl/reference/com-interface-entry-macros.md#com_interface_entry_autoaggregate_blind)