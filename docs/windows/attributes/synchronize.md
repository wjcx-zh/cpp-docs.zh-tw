---
title: 同步處理 （c + + COM 屬性）
ms.date: 10/02/2018
f1_keywords:
- vc-attr.synchronize
helpviewer_keywords:
- synchronize attribute
ms.assetid: 15fc8544-955d-4765-b3d5-0f619c8b3f40
ms.openlocfilehash: e5afec6257c421c0d3d5c95ba77c29767d0df280
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50620892"
---
# <a name="synchronize"></a>synchronize

同步處理至目標方法的存取。

## <a name="syntax"></a>語法

```cpp
[synchronize]
```

## <a name="remarks"></a>備註

**同步處理**c + + 屬性會實作同步處理物件的目標方法的支援。 同步處理可讓多個物件，以使用常見的資源 （例如類別的方法），藉由控制目標方法的存取權。

這個屬性所插入的程式碼會呼叫適當`Lock`方法 （由執行緒模型），在目標方法的開頭。 當此方法會結束時，`Unlock`會自動呼叫。 如需有關這些函式的詳細資訊，請參閱[CComAutoThreadModule::Lock](../../atl/reference/ccomautothreadmodule-class.md#lock)

此屬性需要 [coclass](coclass.md)、 [progid](progid.md)或 [vi_progid](vi-progid.md) 屬性 (或表示上述其中一項的另一個屬性) 也套用至相同的項目。 如果使用任何單一屬性，則會自動套用其他兩項。 例如，如果`progid`會套用`vi_progid`和`coclass`也會套用。

## <a name="example"></a>範例

下列程式碼提供的同步處理`UpdateBalance`方法的`CMyClass`物件。

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
|**適用於**|類別方法方法|
|**可重複**|否|
|**必要屬性**|一或多個項目： `coclass`， `progid`，或`vi_progid`。|
|**無效屬性**|無|

如需有關屬性內容的詳細資訊，請參閱 [屬性內容](cpp-attributes-com-net.md#contexts)。

## <a name="see-also"></a>另請參閱

[COM 屬性](com-attributes.md)