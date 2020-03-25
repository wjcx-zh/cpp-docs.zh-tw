---
title: 匯總（C++ COM 屬性）
ms.date: 10/02/2018
f1_keywords:
- vc-attr.aggregatable
helpviewer_keywords:
- aggregatable attribute
ms.assetid: 9253a46a-cd76-41f2-b3b6-86f709bb069c
ms.openlocfilehash: d929543f699dcd20471ff9a9b45f54119f82a40a
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80168521"
---
# <a name="aggregatable"></a>aggregatable

表示類別支援匯總。

## <a name="syntax"></a>語法

```cpp
[ aggregatable(value) ]
```

### <a name="parameters"></a>參數

*value*<br/>
選擇性參數，指出可以匯總 COM 物件的時機：

- `never` 無法匯總 COM 物件。

- `allowed` 可以直接建立 COM 物件，也可以加以匯總。 這是預設值。

- `always` 無法直接建立 COM 物件，而且只能進行匯總。 當您呼叫這個物件的 `CoCreateInstance` 時，您必須指定匯總物件的 `IUnknown` 介面（控制 `IUnknown`）。

## <a name="remarks"></a>備註

匯總**aggregatable** C++屬性的功能與匯總 MIDL 屬性相同[aggregatable](/windows/win32/Midl/aggregatable) 。 這表示編譯器會將**匯總屬性傳遞至產生的 .idl**檔案。

此屬性需要 [coclass](coclass.md)、 [progid](progid.md)或 [vi_progid](vi-progid.md) 屬性 (或表示上述其中一項的另一個屬性) 也套用至相同的項目。 如果使用任何單一屬性，則會自動套用其他兩項。 例如，如果套用了 `progid`，也會套用 `vi_progid` 和 `coclass`。

### <a name="atl-projects"></a>ATL 專案

如果在使用 ATL 的專案內使用此屬性，則屬性的行為會變更。 除了先前描述的行為之外，屬性也會在目標類別中加入下列其中一個宏：

|參數值|已插入宏|
|---------------------|--------------------|
|`Never`|[DECLARE_NOT_AGGREGATABLE](../../atl/reference/aggregation-and-class-factory-macros.md#declare_not_aggregatable)|
|`Allowed`|[DECLARE_POLY_AGGREGATABLE](../../atl/reference/aggregation-and-class-factory-macros.md#declare_poly_aggregatable)|
|`Always`|[DECLARE_ONLY_AGGREGATABLE](../../atl/reference/aggregation-and-class-factory-macros.md#declare_only_aggregatable)|

## <a name="example"></a>範例

```cpp
// cpp_attr_ref_aggregatable.cpp
// compile with: /LD
#define _ATL_ATTRIBUTES
#include "atlbase.h"
#include "atlcom.h"

[module(name="MyModule")];

[ coclass, aggregatable(allowed),
  uuid("1a8369cc-1c91-42c4-befa-5a5d8c9d2529")]
class CMyClass {};
```

## <a name="requirements"></a>需求

### <a name="attribute-context"></a>屬性內容

|||
|-|-|
|**適用於**|**class**、 **struct**|
|**可重複**|否|
|**必要屬性**|下列一或多項： `coclass`、`progid`或 `vi_progid`。|
|**無效屬性**|None|

如需有關屬性內容的詳細資訊，請參閱 [屬性內容](cpp-attributes-com-net.md#contexts)。

## <a name="see-also"></a>另請參閱

[IDL 屬性](idl-attributes.md)<br/>
[類別屬性](class-attributes.md)<br/>
[Typedef、Enum、Union 和 Struct 屬性](typedef-enum-union-and-struct-attributes.md)<br/>
[彙總](/windows/win32/com/aggregation)
