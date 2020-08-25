---
title: " (c + + COM 屬性) 授權"
ms.date: 10/02/2018
f1_keywords:
- vc-attr.licensed
helpviewer_keywords:
- licensed attribute
ms.assetid: 09cf3b4a-d3f2-43e3-9180-d420333b23bf
ms.openlocfilehash: 07a2b68517721ac4244fc1952e4fe3c5f2fbb153
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/25/2020
ms.locfileid: "88832486"
---
# <a name="licensed"></a>licensed

指出它所套用的 COM 物件已獲得授權，而且必須使用具現化 `IClassFactory2` 。

## <a name="syntax"></a>語法

```cpp
[licensed]
```

## <a name="remarks"></a>備註

**授權**c + + 屬性具有與[授權](/windows/win32/Midl/licensed)MIDL 屬性相同的功能。

## <a name="example"></a>範例

```cpp
// cpp_attr_ref_licensed.cpp
// compile with: /LD
#include "unknwn.h"
[object, uuid("00000000-0000-0000-0000-000000000001")]
__interface IMyI : IUnknown {
   HRESULT f();
};

[coclass, version("2.1"), uuid(12345678-1111-2222-3333-123456789012),
licensed, threading(free), progid(some.name)]
class CSample : public IMyI {
public:
   int nSize;
};

[module(name="MyLibrary", version="1.0", helpstring="My Library Block")];
```

## <a name="requirements"></a>規格需求

| 屬性內容 | 值 |
|-|-|
|**適用於**|**`class`**, **`struct`**|
|**重複**|否|
|**必要的屬性**|`coclass`|
|**無效屬性**|無|

如需詳細資訊，請參閱 [屬性內容](cpp-attributes-com-net.md#contexts)。

## <a name="see-also"></a>另請參閱

[IDL 屬性](idl-attributes.md)<br/>
[類別屬性](class-attributes.md)
