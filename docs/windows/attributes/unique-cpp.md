---
title: unique （c + + COM 屬性）
ms.date: 10/02/2018
f1_keywords:
- vc-attr.unique
helpviewer_keywords:
- unique attribute
ms.assetid: abd7ed14-5ae7-44a8-8333-0058e9c92b2f
ms.openlocfilehash: a46d607ef03fcb75fea31835726d0e2d95e71df8
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87201020"
---
# <a name="unique-c"></a>unique (C++)

指定唯一的指標。

## <a name="syntax"></a>語法

```cpp
[unique]
```

## <a name="remarks"></a>備註

**Unique** c + + 屬性具有與[唯一](/windows/win32/Midl/unique)MIDL 屬性相同的功能。

## <a name="example"></a>範例

如需使用**unique**的範例，請參閱[ref](ref-cpp.md)範例。

## <a name="requirements"></a>需求

### <a name="attribute-context"></a>屬性內容

|||
|-|-|
|**適用於**|**`typedef`**、 **`struct`** 、 **`union`** 、interface 參數、interface 方法|
|**可重複**|否|
|**必要的屬性**|無|
|**無效屬性**|無|

如需有關屬性內容的詳細資訊，請參閱 [屬性內容](cpp-attributes-com-net.md#contexts)。

## <a name="see-also"></a>另請參閱

[IDL 屬性](idl-attributes.md)<br/>
[Typedef、Enum、Union 和 Struct 屬性](typedef-enum-union-and-struct-attributes.md)<br/>
[參數屬性](parameter-attributes.md)
