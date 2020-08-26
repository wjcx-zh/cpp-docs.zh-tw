---
title: 'implements_category (c + + COM 屬性) '
ms.date: 10/02/2018
f1_keywords:
- vc-attr.implements_category
helpviewer_keywords:
- implements_category attribute
ms.assetid: fb162df3-1ebe-43dc-a084-668d7ef8c03f
ms.openlocfilehash: cd9a4de8834bc22368393e9ea4639884785af0f2
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/25/2020
ms.locfileid: "88846117"
---
# <a name="implements_category"></a>implements_category

指定目標類別所執行的元件類別。

## <a name="syntax"></a>語法

```cpp
[ implements_category(implements_category="uuid") ]
```

### <a name="parameters"></a>參數

*implements_category*<br/>
已執行類別的識別碼。

## <a name="remarks"></a>備註

**Implements_category** c + + 屬性會指定目標類別所執行的元件類別。 這是藉由建立類別目錄對應，並新增 **implements_category** 屬性指定的個別專案來完成。 如需詳細資訊，請參閱 [元件類別和其運作方式](/windows/win32/com/component-categories-and-how-they-work)。

此屬性需要 [coclass](coclass.md)、 [progid](progid.md)或 [vi_progid](vi-progid.md) 屬性 (或表示上述其中一項的另一個屬性) 也套用至相同的項目。 如果使用任何單一屬性，則會自動套用其他兩項。 例如，如果套用 `progid` ，則 `vi_progid` `coclass` 也會套用。

## <a name="example"></a>範例

下列程式碼指定下列物件會執行 `Control` 類別目錄。

```cpp
// cpp_attr_ref_implements_category.cpp
// compile with: /LD
#define _ATL_ATTRIBUTES
#include "atlbase.h"
#include "atlcom.h"

[module (name="MyLib")];
[ coclass, implements_category("CATID_Control"),
  uuid("20a0d0cc-5172-40f5-99ae-5e032f3205ae")]
class CMyClass {};
```

## <a name="requirements"></a>規格需求

| 屬性內容 | 值 |
|-|-|
|**適用於**|**`class`**, **`struct`**|
|**重複**|是|
|**必要的屬性**|下列其中一項： `coclass` 、 `progid` 或 `vi_progid`|
|**無效屬性**|無|

如需詳細資訊，請參閱 [屬性內容](cpp-attributes-com-net.md#contexts)。

## <a name="see-also"></a>另請參閱

[COM 屬性](com-attributes.md)<br/>
[類別屬性](class-attributes.md)<br/>
[IMPLEMENTED_CATEGORY](../../atl/reference/category-macros.md#implemented_category)
