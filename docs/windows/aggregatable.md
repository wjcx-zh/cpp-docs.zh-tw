---
title: 彙總 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.aggregatable
dev_langs:
- C++
helpviewer_keywords:
- aggregatable attribute
ms.assetid: 9253a46a-cd76-41f2-b3b6-86f709bb069c
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: a9d65f77126ceb4268d41610c6d5fe3a07968d02
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/29/2018
ms.locfileid: "43200564"
---
# <a name="aggregatable"></a>aggregatable

表示類別，支援彙總。

## <a name="syntax"></a>語法

```cpp
[ aggregatable(
   value
) ]
```

### <a name="parameters"></a>參數

*值*（選擇性）  
表示 COM 物件可以彙總的參數：

- `never` 無法彙總的 COM 物件。

- `allowed` 可以直接建立 COM 物件，或可以彙總。 這是預設值。

- `always` COM 物件無法直接建立，且只會彙總。 當您呼叫`CoCreateInstance`這個物件中，您必須指定彙總的物件`IUnknown`介面 (控制`IUnknown`)。

## <a name="remarks"></a>備註

**彙總**c + + 屬性具有相同的功能[彙總](/windows/desktop/Midl/aggregatable)MIDL 屬性。 這表示，編譯器會通過**彙總**透過屬性設定為產生的.idl 檔案。

此屬性需要 [coclass](../windows/coclass.md)、 [progid](../windows/progid.md)或 [vi_progid](../windows/vi-progid.md) 屬性 (或表示上述其中一項的另一個屬性) 也套用至相同的項目。 如果使用任何單一屬性，則會自動套用其他兩項。 例如，如果`progid`會套用`vi_progid`和`coclass`也會套用。

### <a name="atl-projects"></a>ATL 專案

如果在使用 ATL 的專案內使用此屬性，則屬性的行為會變更。 除了先前所述的行為，該屬性也會加入下列巨集的其中一個目標類別：

|參數值|已插入的巨集|
|---------------------|--------------------|
|`Never`|[DECLARE_NOT_AGGREGATABLE](../atl/reference/aggregation-and-class-factory-macros.md#declare_not_aggregatable)|
|`Allowed`|[DECLARE_POLY_AGGREGATABLE](../atl/reference/aggregation-and-class-factory-macros.md#declare_poly_aggregatable)|
|`Always`|[DECLARE_ONLY_AGGREGATABLE](../atl/reference/aggregation-and-class-factory-macros.md#declare_only_aggregatable)|

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
|**適用於**|**類別**，**結構**|
|**可重複**|否|
|**必要屬性**|一或多個項目： `coclass`， `progid`，或`vi_progid`。|
|**無效屬性**|無|

如需有關屬性內容的詳細資訊，請參閱 [屬性內容](../windows/attribute-contexts.md)。

## <a name="see-also"></a>另請參閱

[IDL 屬性](../windows/idl-attributes.md)  
[類別屬性](../windows/class-attributes.md)  
[Typedef、Enum、Union 和 Struct 屬性](../windows/typedef-enum-union-and-struct-attributes.md)  
[彙總](/windows/desktop/com/aggregation)  