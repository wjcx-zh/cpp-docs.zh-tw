---
title: noncreatable （c + + COM 屬性）
ms.date: 10/02/2018
f1_keywords:
- vc-attr.noncreatable
helpviewer_keywords:
- noncreatable attribute
ms.assetid: 4d17937b-0bff-41af-ba57-53e18b7ab5a9
ms.openlocfilehash: 716cc741de92be73fc2fcdda6b019de736387efd
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50578356"
---
# <a name="noncreatable"></a>noncreatable

定義本身無法具現化的物件。

## <a name="syntax"></a>語法

```cpp
[noncreatable]
```

## <a name="remarks"></a>備註

**Noncreatable** c + + 屬性具有相同的功能[noncreatable](/windows/desktop/Midl/noncreatable) MIDL 屬性會自動傳至所產生。編譯器的 IDL 檔案。

使用 ATL 的專案中使用這個屬性時，屬性的行為變更。 除了上述的行為，該屬性也會插入[OBJECT_ENTRY_NON_CREATEABLE_EX_AUTO](../../atl/reference/object-map-macros.md#object_entry_non_createable_ex_auto)巨集。 這個巨集表示 ATL 物件無法從外部建立。

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
|**適用於**|**類別**，**結構**|
|**可重複**|否|
|**必要屬性**|**coclass**|
|**無效屬性**|無|

如需有關屬性內容的詳細資訊，請參閱 [屬性內容](cpp-attributes-com-net.md#contexts)。

## <a name="see-also"></a>另請參閱

[IDL 屬性](idl-attributes.md)<br/>
[類別屬性](class-attributes.md)
