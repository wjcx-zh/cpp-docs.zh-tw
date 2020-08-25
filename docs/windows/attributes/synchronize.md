---
title: '同步處理 (c + + COM 屬性) '
ms.date: 10/02/2018
f1_keywords:
- vc-attr.synchronize
helpviewer_keywords:
- synchronize attribute
ms.assetid: 15fc8544-955d-4765-b3d5-0f619c8b3f40
ms.openlocfilehash: a7edbaa4e572af18bec9b3b6bef54594d6511390
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/25/2020
ms.locfileid: "88831667"
---
# <a name="synchronize"></a>synchronize

同步處理對目標方法的存取。

## <a name="syntax"></a>語法

```cpp
[synchronize]
```

## <a name="remarks"></a>備註

Synchronize c + + 屬性會執行同步 **處理** 物件之目標方法的支援。 同步處理可讓多個物件使用一般資源 (例如，藉由控制目標方法的存取來) 類別的方法。

這個屬性所插入的程式碼會呼叫適當的 `Lock` 方法， (在目標方法的開頭) 由執行緒模型所決定。 當方法結束時，會 `Unlock` 自動呼叫。 如需這些函數的詳細資訊，請參閱[CComAutoThreadModule：： Lock](../../atl/reference/ccomautothreadmodule-class.md#lock) 。

此屬性需要 [coclass](coclass.md)、 [progid](progid.md)或 [vi_progid](vi-progid.md) 屬性 (或表示上述其中一項的另一個屬性) 也套用至相同的項目。 如果使用任何單一屬性，則會自動套用其他兩項。 例如，如果套用 `progid` ，則 `vi_progid` `coclass` 也會套用。

## <a name="example"></a>範例

下列程式碼提供 `UpdateBalance` 物件之方法的同步處理 `CMyClass` 。

```cpp
// cpp_attr_ref_synchronize.cpp
// compile with: /LD
#define _ATL_ATTRIBUTES
#include "atlbase.h"
#include "atlcom.h"

[module(name="SYNC")];

[coclass,
threading(both),
vi_progid("MyProject.MyClass"),
progid("MyProject.MyClass.1"),
uuid("7a7baa0d-59b8-4576-b754-79d07e1d1cc3")
]
class CMyClass {
   float m_nBalance;

   [synchronize]
   void UpdateBalance(float nAdjust) {
      m_nBalance += nAdjust;
   }
};
```

## <a name="requirements"></a>規格需求

| 屬性內容 | 值 |
|-|-|
|**適用於**|Class 方法，方法|
|**重複**|否|
|**必要的屬性**|下列其中一項或多項： `coclass` 、 `progid` 或 `vi_progid` 。|
|**無效屬性**|無|

如需有關屬性內容的詳細資訊，請參閱 [屬性內容](cpp-attributes-com-net.md#contexts)。

## <a name="see-also"></a>另請參閱

[COM 屬性](com-attributes.md)
