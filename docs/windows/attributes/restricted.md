---
title: 限制 （c + + COM 屬性）
ms.date: 10/03/2018
f1_keywords:
- vc-attr.restricted
helpviewer_keywords:
- restricted attribute
ms.assetid: 504a96be-b904-4269-8be1-920feba201b4
ms.openlocfilehash: 1aa18255f7d7a0740494050a149d436fb167fe8a
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50521022"
---
# <a name="restricted"></a>restricted

指定的模組、 介面或 dispinterface 成員不能任意呼叫。

## <a name="syntax"></a>語法

```cpp
[ restricted(
   interfaces
) ]
```

### <a name="parameters"></a>參數

*interfaces*<br/>
Metodu nelze volat 任意 COM 物件的一或多個介面。 此參數才有效時套用至類別。

## <a name="remarks"></a>備註

**受限**c + + 屬性具有相同的功能[限制](/windows/desktop/Midl/restricted)MIDL 屬性。

## <a name="example"></a>範例

下列程式碼示範如何使用**限制**屬性：

```cpp
// cpp_attr_ref_restricted.cpp
// compile with: /LD
#include "windows.h"
#include "unknwn.h"
[module(name="MyLib")];

[object, uuid("00000000-0000-0000-0000-000000000001")]
__interface a
{
};

[object, uuid("00000000-0000-0000-0000-000000000002")]
__interface b
{
};

[coclass, restricted(a,b), uuid("00000000-0000-0000-0000-000000000003")]
class c : public a, public b
{
};
```

## <a name="requirements"></a>需求

### <a name="attribute-context"></a>屬性內容

|||
|-|-|
|**適用於**|介面方法，**介面**，**類別**，**結構**|
|**可重複**|否|
|**必要屬性**|**coclass** (當套用至**類別**或是**結構**)|
|**無效屬性**|無|

如需有關屬性內容的詳細資訊，請參閱 [屬性內容](cpp-attributes-com-net.md#contexts)。

## <a name="see-also"></a>另請參閱

[IDL 屬性](idl-attributes.md)<br/>
[介面屬性](interface-attributes.md)<br/>
[方法屬性](method-attributes.md)