---
title: '可匯總 (c + + COM 屬性) '
ms.date: 10/02/2018
f1_keywords:
- vc-attr.aggregatable
helpviewer_keywords:
- aggregatable attribute
ms.assetid: 9253a46a-cd76-41f2-b3b6-86f709bb069c
ms.openlocfilehash: 6782b1ca28eb07b3f726bd85cd7fffa9b1f1bad2
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/25/2020
ms.locfileid: "88836370"
---
# <a name="aggregatable"></a>aggregatable

指出類別支援匯總。

## <a name="syntax"></a>語法

```cpp
[ aggregatable(value) ]
```

### <a name="parameters"></a>參數

*value*<br/>
 (選擇性) 參數，以指出可以匯總 COM 物件的時間：

- `never` 無法匯總 COM 物件。

- `allowed` COM 物件可以直接建立，也可以進行匯總。 這是預設值。

- `always` 無法直接建立 COM 物件，且只能進行匯總。 當您呼叫 `CoCreateInstance` 這個物件時，您必須指定匯總物件的 `IUnknown` 介面 (控制 `IUnknown`) 。

## <a name="remarks"></a>備註

可匯總 **的 c +** + 屬性具有與匯總 [MIDL 屬性相同的功能](/windows/win32/Midl/aggregatable) 。 這表示編譯器會將 **匯總屬性傳遞至產生的 .idl** 檔案。

此屬性需要 [coclass](coclass.md)、 [progid](progid.md)或 [vi_progid](vi-progid.md) 屬性 (或表示上述其中一項的另一個屬性) 也套用至相同的項目。 如果使用任何單一屬性，則會自動套用其他兩項。 例如，如果套用 `progid` ，則 `vi_progid` `coclass` 也會套用。

### <a name="atl-projects"></a>ATL 專案

如果在使用 ATL 的專案內使用此屬性，則屬性的行為會變更。 除了先前所述的行為之外，屬性也會將下列其中一個宏新增至目標類別：

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

## <a name="requirements"></a>規格需求

| 屬性內容 | 值 |
|-|-|
|**適用於**|**`class`**, **`struct`**|
|**重複**|否|
|**必要的屬性**|下列其中一項或多項： `coclass` 、 `progid` 或 `vi_progid` 。|
|**無效屬性**|無|

如需有關屬性內容的詳細資訊，請參閱 [屬性內容](cpp-attributes-com-net.md#contexts)。

## <a name="see-also"></a>另請參閱

[IDL 屬性](idl-attributes.md)<br/>
[類別屬性](class-attributes.md)<br/>
[Typedef、Enum、Union 和 Struct 屬性](typedef-enum-union-and-struct-attributes.md)<br/>
[聚集](/windows/win32/com/aggregation)
