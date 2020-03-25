---
title: synchronize （C++ COM 屬性）
ms.date: 10/02/2018
f1_keywords:
- vc-attr.synchronize
helpviewer_keywords:
- synchronize attribute
ms.assetid: 15fc8544-955d-4765-b3d5-0f619c8b3f40
ms.openlocfilehash: a0f4702de4cfde8586cc573f9ff5a6195984d207
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80214509"
---
# <a name="synchronize"></a>synchronize

同步處理對目標方法的存取。

## <a name="syntax"></a>語法

```cpp
[synchronize]
```

## <a name="remarks"></a>備註

Synchronize 屬性會執行同步**處理** C++物件之目標方法的支援。 同步處理可透過控制目標方法的存取，讓多個物件使用通用資源（例如類別的方法）。

這個屬性所插入的程式碼會在目標方法的開頭呼叫適當的 `Lock` 方法（由執行緒模型決定）。 當此方法結束時，會自動呼叫 `Unlock`。 如需這些函數的詳細資訊，請參閱[CComAutoThreadModule：： Lock](../../atl/reference/ccomautothreadmodule-class.md#lock)

此屬性需要 [coclass](coclass.md)、 [progid](progid.md)或 [vi_progid](vi-progid.md) 屬性 (或表示上述其中一項的另一個屬性) 也套用至相同的項目。 如果使用任何單一屬性，則會自動套用其他兩項。 例如，如果套用了 `progid`，也會套用 `vi_progid` 和 `coclass`。

## <a name="example"></a>範例

下列程式碼提供 `CMyClass` 物件之 `UpdateBalance` 方法的同步處理。

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

## <a name="requirements"></a>需求

### <a name="attribute-context"></a>屬性內容

|||
|-|-|
|**適用於**|Class 方法，方法|
|**可重複**|否|
|**必要屬性**|下列一或多項： `coclass`、`progid`或 `vi_progid`。|
|**無效屬性**|None|

如需有關屬性內容的詳細資訊，請參閱 [屬性內容](cpp-attributes-com-net.md#contexts)。

## <a name="see-also"></a>另請參閱

[COM 屬性](com-attributes.md)
