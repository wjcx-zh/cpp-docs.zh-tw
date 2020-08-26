---
title: 'defaultvtable (c + + COM 屬性) '
ms.date: 10/02/2018
f1_keywords:
- vc-attr.defaultvtable
helpviewer_keywords:
- defaultvtable attribute
ms.assetid: 5b3ed483-f69e-44dd-80fc-952028eb9d73
ms.openlocfilehash: 6b1d6960a065bf2df46852d3df1ca53d4239f1bc
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/25/2020
ms.locfileid: "88839487"
---
# <a name="defaultvtable"></a>defaultvtable

將介面定義為 COM 物件的預設 vtable 介面。

## <a name="syntax"></a>語法

```cpp
[ defaultvtable(interface) ]
```

### <a name="parameters"></a>參數

*interface*<br/>
您想要讓 COM 物件具有預設 vtable 的指定介面。

## <a name="remarks"></a>備註

**Defaultvtable** c + + 屬性具有與[defaultvtable](/windows/win32/Midl/defaultvtable) MIDL 屬性相同的功能。

## <a name="example"></a>範例

下列程式碼顯示使用 **defaultvtable** 來指定預設介面之類別上的屬性：

```cpp
// cpp_attr_ref_defaultvtable.cpp
// compile with: /LD
#include <unknwn.h>
[module(name="MyLib")];

[object, uuid("00000000-0000-0000-0000-000000000001")]
__interface IMyI1 {
   HRESULT x();
};

[object, uuid("00000000-0000-0000-0000-000000000002")]
__interface IMyI2 {
   HRESULT x();
};

[object, uuid("00000000-0000-0000-0000-000000000003")]
__interface IMyI3 {
   HRESULT x();
};

[coclass, source(IMyI3, IMyI1), default(IMyI3, IMyI2), defaultvtable(IMyI1),
uuid("00000000-0000-0000-0000-000000000004")]
class CMyC3 : public IMyI3 {};
```

## <a name="requirements"></a>規格需求

| 屬性內容 | 值 |
|-|-|
|**適用於**|**`class`**, **`struct`**|
|**重複**|否|
|**必要的屬性**|**coclass**|
|**無效屬性**|無|

如需詳細資訊，請參閱 [屬性內容](cpp-attributes-com-net.md#contexts)。

## <a name="see-also"></a>另請參閱

[IDL 屬性](idl-attributes.md)<br/>
[類別屬性](class-attributes.md)
