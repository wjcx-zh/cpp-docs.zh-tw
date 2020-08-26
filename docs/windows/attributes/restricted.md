---
title: '受限的 (c + + COM 屬性) '
ms.date: 10/03/2018
f1_keywords:
- vc-attr.restricted
helpviewer_keywords:
- restricted attribute
ms.assetid: 504a96be-b904-4269-8be1-920feba201b4
ms.openlocfilehash: a1f543c4d8edac751195d37414c030dfe2df94fa
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/25/2020
ms.locfileid: "88846351"
---
# <a name="restricted"></a>restricted

指定無法任意呼叫模組、介面或分配介面的成員。

## <a name="syntax"></a>語法

```cpp
[ restricted(
   interfaces
) ]
```

### <a name="parameters"></a>參數

*interfaces*<br/>
可能不會在 COM 物件上任意呼叫的一或多個介面。 只有套用至類別時，此參數才有效。

## <a name="remarks"></a>備註

**受限制**的 c + + 屬性具有與[限制](/windows/win32/Midl/restricted)MIDL 屬性相同的功能。

## <a name="example"></a>範例

下列程式碼顯示如何使用 **受限制** 的屬性：

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

## <a name="requirements"></a>規格需求

| 屬性內容 | 值 |
|-|-|
|**適用於**|介面方法、 **介面**、 **`class`** 、 **`struct`**|
|**重複**|否|
|**必要的屬性**|**coclass**套用至 **`class`** 或) 的 coclass **`struct`** (|
|**無效屬性**|無|

如需有關屬性內容的詳細資訊，請參閱 [屬性內容](cpp-attributes-com-net.md#contexts)。

## <a name="see-also"></a>另請參閱

[IDL 屬性](idl-attributes.md)<br/>
[介面屬性](interface-attributes.md)<br/>
[方法屬性](method-attributes.md)
