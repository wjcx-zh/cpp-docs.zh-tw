---
title: unique (C++ COM 屬性)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.unique
helpviewer_keywords:
- unique attribute
ms.assetid: abd7ed14-5ae7-44a8-8333-0058e9c92b2f
ms.openlocfilehash: 91e563ed121ba09e0c2ca2660f30c75956232ea0
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/15/2019
ms.locfileid: "69514909"
---
# <a name="unique-c"></a>unique (C++)

指定唯一的指標。

## <a name="syntax"></a>語法

```cpp
[unique]
```

## <a name="remarks"></a>備註

**Unique** C++屬性的功能與[唯一](/windows/win32/Midl/unique)的 MIDL 屬性相同。

## <a name="example"></a>範例

如需使用**unique**的範例, 請參閱[ref](ref-cpp.md)範例。

## <a name="requirements"></a>需求

### <a name="attribute-context"></a>屬性內容

|||
|-|-|
|**適用於**|**typedef**、 **struct**、 **union**、interface 參數、interface 方法|
|**可重複**|否|
|**必要屬性**|None|
|**無效屬性**|無|

如需有關屬性內容的詳細資訊，請參閱 [屬性內容](cpp-attributes-com-net.md#contexts)。

## <a name="see-also"></a>另請參閱

[IDL 屬性](idl-attributes.md)<br/>
[Typedef、Enum、Union 和 Struct 屬性](typedef-enum-union-and-struct-attributes.md)<br/>
[參數屬性](parameter-attributes.md)