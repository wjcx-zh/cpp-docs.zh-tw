---
title: 受限制（c + + COM 屬性）
ms.date: 10/03/2018
f1_keywords:
- vc-attr.restricted
helpviewer_keywords:
- restricted attribute
ms.assetid: 504a96be-b904-4269-8be1-920feba201b4
ms.openlocfilehash: 0545c07936c59a59dd4712f4b0a2fd98a6701f2e
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87230022"
---
# <a name="restricted"></a>restricted

指定不能任意呼叫模組、介面或分配介面的成員。

## <a name="syntax"></a>語法

```cpp
[ restricted(
   interfaces
) ]
```

### <a name="parameters"></a>參數

*interfaces*<br/>
在 COM 物件上可能不會任意呼叫的一個或多個介面。 這個參數只有在套用至類別時才有效。

## <a name="remarks"></a>備註

**限制**的 c + + 屬性具有與[受限制](/windows/win32/Midl/restricted)MIDL 屬性相同的功能。

## <a name="example"></a>範例

下列程式碼顯示如何使用**受限制**的屬性：

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
|**適用於**|介面方法、**介面**、 **`class`** 、**`struct`**|
|**可重複**|否|
|**必要的屬性**|**coclass** （套用至 **`class`** 或時 **`struct`** ）|
|**無效屬性**|無|

如需有關屬性內容的詳細資訊，請參閱 [屬性內容](cpp-attributes-com-net.md#contexts)。

## <a name="see-also"></a>另請參閱

[IDL 屬性](idl-attributes.md)<br/>
[介面屬性](interface-attributes.md)<br/>
[方法屬性](method-attributes.md)
