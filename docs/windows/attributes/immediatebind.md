---
title: immediatebind （C++ COM 屬性）
ms.date: 10/02/2018
f1_keywords:
- vc-attr.immediatebind
helpviewer_keywords:
- immediatebind attribute
ms.assetid: 186d40e6-9166-4d0c-9853-4e7e4d25226f
ms.openlocfilehash: d0fb85a3f5642bc5fffcad29892ca15bb13a1ce0
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80166910"
---
# <a name="immediatebind"></a>immediatebind

表示資料庫將會在資料系結物件之屬性的所有變更時立即收到通知。

## <a name="syntax"></a>語法

```cpp
[immediatebind]
```

## <a name="remarks"></a>備註

**Immediatebind** C++屬性具有與[immediatebind](/windows/win32/Midl/immediatebind) MIDL 屬性相同的功能。

## <a name="example"></a>範例

如需如何使用**immediatebind**的範例[，請參閱](bindable.md)可系結。

## <a name="requirements"></a>需求

### <a name="attribute-context"></a>屬性內容

|||
|-|-|
|**適用於**|介面方法|
|**可重複**|否|
|**必要屬性**|None|
|**無效屬性**|None|

如需詳細資訊，請參閱 [屬性內容](cpp-attributes-com-net.md#contexts)。

## <a name="see-also"></a>另請參閱

[IDL 屬性](idl-attributes.md)<br/>
[方法屬性](method-attributes.md)<br/>
[defaultbind](defaultbind.md)<br/>
[displaybind](displaybind.md)<br/>
[requestedit](requestedit.md)
