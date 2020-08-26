---
title: '來源 (c + + COM 屬性) '
ms.date: 10/02/2018
f1_keywords:
- vc-attr.source
helpviewer_keywords:
- source attribute
ms.assetid: 1878d05d-7709-4e97-b114-c62f38f5140e
ms.openlocfilehash: f9a1f576e26805c5dd84c2d83cdf3615d0661af3
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/25/2020
ms.locfileid: "88842763"
---
# <a name="source-c"></a>source (C++)

在類別上，指定連接點的 COM 物件來源介面。 在屬性或方法上，表示成員會傳回做為事件來源的物件或變異。

## <a name="syntax"></a>語法

```cpp
[ source(interfaces) ]
```

### <a name="parameters"></a>參數

*interfaces*<br/>
當您將來源屬性套用至類別時，您指定的一或多個介面。 當來源套用至屬性或方法時，不會使用這個參數。

## <a name="remarks"></a>備註

**來源**c + + 屬性具有與[來源](/windows/win32/Midl/source)MIDL 屬性相同的功能。

您可以使用 [預設](default-cpp.md) 屬性來指定物件的預設來源介面。

## <a name="example"></a>範例

```cpp
// cpp_attr_ref_source.cpp
// compile with: /LD
#include "windows.h"
#include "unknwn.h"
[module(name="MyLib")];

[object, uuid(11111111-1111-1111-1111-111111111111)]
__interface b
{
   [id(0), propget, bindable, displaybind, defaultbind, requestedit]
   HRESULT get_I([out, retval]long *i);
};

[object, uuid(11111111-1111-1111-1111-111111111131)]
__interface c
{
   [id(0), propget, bindable, displaybind, defaultbind, requestedit]
   HRESULT et_I([out, retval]long *i);
};

[coclass, default(c), uuid(11111111-1111-1111-1111-111111111132)]
class N : public b
{
};

[coclass, source(c), default(b, c), uuid(11111111-1111-1111-1111-111111111133)]
class NN : public b
{
};
```

## <a name="requirements"></a>規格需求

| 屬性內容 | 值 |
|-|-|
|**適用於**|**`class`**、 **`struct`** 、 **介面**|
|**重複**|否|
|**必要的屬性**|`coclass` 套用至類別或結構時的 () |
|**無效屬性**|無|

如需有關屬性內容的詳細資訊，請參閱 [屬性內容](cpp-attributes-com-net.md#contexts)。

## <a name="see-also"></a>另請參閱

[IDL 屬性](idl-attributes.md)<br/>
[類別屬性](class-attributes.md)<br/>
[方法屬性](method-attributes.md)<br/>
[coclass](coclass.md)
