---
title: max_is （c + + COM 屬性）
ms.date: 10/02/2018
f1_keywords:
- vc-attr.max_is
helpviewer_keywords:
- max_is attribute
ms.assetid: 7c851f5c-6649-4d77-a792-247c37d8f560
ms.openlocfilehash: 2e30595a549eefc6a5eecc27be98ded5221dcc16
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87201306"
---
# <a name="max_is"></a>max_is

指定有效陣列索引的最大值。

## <a name="syntax"></a>語法

```cpp
[ max_is("expression") ]
```

### <a name="parameters"></a>參數

*expression*<br/>
一或多個 C 語言運算式。 允許空的引數位置。

## <a name="remarks"></a>備註

**Max_is** c + + 屬性具有與[max_is](/windows/win32/Midl/max-is) MIDL 屬性相同的功能。

## <a name="requirements"></a>需求

### <a name="attribute-context"></a>屬性內容

|||
|-|-|
|**適用於**|或中的欄位 **`struct`** **`union`** ，介面參數，介面方法|
|**可重複**|否|
|**必要的屬性**|無|
|**無效屬性**|**size_is**|

如需詳細資訊，請參閱 [屬性內容](cpp-attributes-com-net.md#contexts)。

## <a name="example"></a>範例

如需如何指定陣列區段的範例，請參閱[first_is](first-is.md) 。

## <a name="see-also"></a>另請參閱

[IDL 屬性](idl-attributes.md)<br/>
[Typedef、Enum、Union 和 Struct 屬性](typedef-enum-union-and-struct-attributes.md)<br/>
[參數屬性](parameter-attributes.md)<br/>
[first_is](first-is.md)<br/>
[last_is](last-is.md)<br/>
[length_is](length-is.md)<br/>
[size_is](size-is.md)
