---
title: noncreatable （c + + COM 屬性）
ms.date: 10/02/2018
f1_keywords:
- vc-attr.noncreatable
helpviewer_keywords:
- noncreatable attribute
ms.assetid: 4d17937b-0bff-41af-ba57-53e18b7ab5a9
ms.openlocfilehash: c5d51d7c5628a875f036b4e48b03b317490b37ff
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87224392"
---
# <a name="noncreatable"></a>noncreatable

定義無法自行具現化的物件。

## <a name="syntax"></a>語法

```cpp
[noncreatable]
```

## <a name="remarks"></a>備註

**Noncreatable** c + + 屬性具有與[noncreatable](/windows/win32/Midl/noncreatable) MIDL 屬性相同的功能，而且會自動傳遞至產生的。由編譯器所進行的 IDL 檔案。

當此屬性在使用 ATL 的專案內使用時，屬性的行為會變更。 除了上述行為之外，屬性也會插入[OBJECT_ENTRY_NON_CREATEABLE_EX_AUTO](../../atl/reference/object-map-macros.md#object_entry_non_createable_ex_auto)宏。 這個宏會向 ATL 指出無法在外部建立物件。

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

## <a name="requirements"></a>需求

### <a name="attribute-context"></a>屬性內容

|||
|-|-|
|**適用於**|**`class`**, **`struct`**|
|**可重複**|否|
|**必要的屬性**|**coclass**|
|**無效屬性**|無|

如需有關屬性內容的詳細資訊，請參閱 [屬性內容](cpp-attributes-com-net.md#contexts)。

## <a name="see-also"></a>另請參閱

[IDL 屬性](idl-attributes.md)<br/>
[類別屬性](class-attributes.md)
