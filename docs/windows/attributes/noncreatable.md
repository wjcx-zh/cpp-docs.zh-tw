---
title: 'noncreatable (c + + COM 屬性) '
ms.date: 10/02/2018
f1_keywords:
- vc-attr.noncreatable
helpviewer_keywords:
- noncreatable attribute
ms.assetid: 4d17937b-0bff-41af-ba57-53e18b7ab5a9
ms.openlocfilehash: b645d6d6cbcaeff346437d6457360ecdef8d3190
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/25/2020
ms.locfileid: "88840553"
---
# <a name="noncreatable"></a>noncreatable

定義無法本身具現化的物件。

## <a name="syntax"></a>語法

```cpp
[noncreatable]
```

## <a name="remarks"></a>備註

**Noncreatable** c + + 屬性具有與[noncreatable](/windows/win32/Midl/noncreatable) MIDL 屬性相同的功能，並且會自動傳遞至產生的。編譯器的 IDL 檔。

當這個屬性用於使用 ATL 的專案內時，屬性的行為會變更。 除了上述行為之外，屬性也會插入 [OBJECT_ENTRY_NON_CREATEABLE_EX_AUTO](../../atl/reference/object-map-macros.md#object_entry_non_createable_ex_auto) 宏。 這個宏指出無法從外部建立物件的 ATL。

## <a name="example"></a>範例

```cpp
// cpp_attr_ref_noncreatable.cpp
// compile with: /LD
#include <unknwn.h>
[module(name="MyLib")];

[object, uuid("11111111-1111-1111-1111-111111111111")]
__interface A
{
};

[coclass, uuid("11111111-1111-1111-1111-111111111112"), noncreatable]
class CMyClass : public A
{
   HRESULT xx();
};
```

## <a name="requirements"></a>規格需求

| 屬性內容 | 值 |
|-|-|
|**適用於**|**`class`**, **`struct`**|
|**重複**|否|
|**必要的屬性**|**coclass**|
|**無效屬性**|無|

如需有關屬性內容的詳細資訊，請參閱 [屬性內容](cpp-attributes-com-net.md#contexts)。

## <a name="see-also"></a>另請參閱

[IDL 屬性](idl-attributes.md)<br/>
[類別屬性](class-attributes.md)
