---
title: immediatebind (C++ COM 屬性)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.immediatebind
helpviewer_keywords:
- immediatebind attribute
ms.assetid: 186d40e6-9166-4d0c-9853-4e7e4d25226f
ms.openlocfilehash: 1844e72ecd1fe7c0f4255426eb48f5c70471e5f5
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62409469"
---
# <a name="immediatebind"></a>immediatebind

表示資料庫將會立即被告知資料繫結物件的屬性的所有變更。

## <a name="syntax"></a>語法

```cpp
[immediatebind]
```

## <a name="remarks"></a>備註

**Immediatebind** C++屬性具有相同的功能[immediatebind](/windows/desktop/Midl/immediatebind) MIDL 屬性。

## <a name="example"></a>範例

請參閱[可繫結](bindable.md)如需如何使用的範例**immediatebind**。

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