---
title: 'switch_type (c + + COM 屬性) '
ms.date: 10/02/2018
f1_keywords:
- vc-attr.switch_type
helpviewer_keywords:
- switch_type attribute
ms.assetid: e24544dc-b3bc-48ae-b249-f967db49271e
ms.openlocfilehash: 0c39aa442c9d4eaf3a482e411cda762fe0cc34b3
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/25/2020
ms.locfileid: "88838525"
---
# <a name="switch_type"></a>switch_type

識別當做聯集判別使用之變數的類型。

## <a name="syntax"></a>語法

```cpp
[switch_type(
type
}]
```

### <a name="parameters"></a>參數

*type*<br/>
參數類型可以是整數、字元、布林值或列舉類型。

## <a name="remarks"></a>備註

**Switch_type** c + + 屬性具有與[switch_type](/windows/win32/Midl/switch-type) MIDL 屬性相同的功能。

C + + 屬性不支援 [封裝](/windows/win32/Midl/encapsulated-unions)的等位。 只有下列格式支援[Nonencapsulated](/windows/win32/Midl/nonencapsulated-unions)聯集：

```cpp
// cpp_attr_ref_switch_type.cpp
// compile with: /LD
#include <windows.h>
[module(name="MyLibrary")];
[ export ]
struct SizedValue2 {
   [switch_type("char"), switch_is(kind)] union {
      [case(1), string]
         wchar_t* wval;
      [default, string]
         char* val;
   };
   char kind;
};
```

## <a name="example"></a>範例

如需**switch_type**的使用範例，請參閱[案例](case-cpp.md)範例。

## <a name="requirements"></a>規格需求

| 屬性內容 | 值 |
|-|-|
|**適用於**|**`typedef`**|
|**重複**|否|
|**必要的屬性**|無|
|**無效屬性**|無|

如需有關屬性內容的詳細資訊，請參閱 [屬性內容](cpp-attributes-com-net.md#contexts)。

## <a name="see-also"></a>另請參閱

[IDL 屬性](idl-attributes.md)<br/>
[Typedef、Enum、Union 和 Struct 屬性](typedef-enum-union-and-struct-attributes.md)<br/>
[出口](export.md)
