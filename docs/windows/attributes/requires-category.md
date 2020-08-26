---
title: 'requires_category (c + + COM 屬性) '
ms.date: 10/02/2018
f1_keywords:
- vc-attr.requires_category
helpviewer_keywords:
- requires_category attribute
ms.assetid: a645fdc6-1ef5-414d-8c56-5fe2686d4687
ms.openlocfilehash: d566e74a9019259e526fa27aec26500e9ef3e1c1
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/25/2020
ms.locfileid: "88846000"
---
# <a name="requires_category"></a>requires_category

指定目標類別的必要元件類別。

## <a name="syntax"></a>語法

```cpp
[ requires_category(
  requires_category) ]
```

### <a name="parameters"></a>參數

*requires_category*<br/>
必要類別的識別碼。

## <a name="remarks"></a>備註

**Requires_category** c + + 屬性會指定目標類別所需的元件類別。 如需詳細資訊，請參閱 [REQUIRED_CATEGORY](../../atl/reference/category-macros.md#required_category)。

此屬性需要 [coclass](coclass.md)、 [progid](progid.md)或 [vi_progid](vi-progid.md) 屬性 (或表示上述其中一項的另一個屬性) 也套用至相同的項目。

## <a name="example"></a>範例

下列程式碼會要求物件必須執行控制項分類。

```cpp
// cpp_attr_ref_requires_category.cpp
// compile with: /LD
#define _ATL_ATTRIBUTES
#include "atlbase.h"
#include "atlcom.h"

[module (name="MyLibrary")];

[ coclass, requires_category("CATID_Control"),
  uuid("1e1a2436-f3ea-4ff3-80bf-5409370e8144")]
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

[COM 屬性](com-attributes.md)<br/>
[implements_category](implements-category.md)
