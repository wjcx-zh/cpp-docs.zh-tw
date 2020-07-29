---
title: size_is （c + + COM 屬性）
ms.date: 10/02/2018
f1_keywords:
- vc-attr.size_is
helpviewer_keywords:
- size_is attribute
ms.assetid: 70192d09-f6c5-4d52-b3fe-303f8cb10aa5
ms.openlocfilehash: 36b960982d1f88cd30bab707dfe7aec73381dfab
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87213836"
---
# <a name="size_is"></a>size_is

指定配置給大小指標的記憶體大小、大小指標的大小指標，以及單一或多維陣列。

## <a name="syntax"></a>語法

```cpp
[ size_is("expression") ]
```

### <a name="parameters"></a>參數

*expression*<br/>
配置給大小指標的記憶體大小。

## <a name="remarks"></a>備註

**Size_is** c + + 屬性具有與[size_is](/windows/win32/Midl/size-is) MIDL 屬性相同的功能。

## <a name="example"></a>範例

如需如何指定陣列區段的範例，請參閱[first_is](first-is.md)的範例。

## <a name="requirements"></a>需求

### <a name="attribute-context"></a>屬性內容

|||
|-|-|
|**適用於**|或中的欄位 **`struct`** **`union`** ，介面參數，介面方法|
|**可重複**|否|
|**必要的屬性**|無|
|**無效屬性**|`max_is`|

如需有關屬性內容的詳細資訊，請參閱 [屬性內容](cpp-attributes-com-net.md#contexts)。

## <a name="see-also"></a>另請參閱

[IDL 屬性](idl-attributes.md)<br/>
[Typedef、Enum、Union 和 Struct 屬性](typedef-enum-union-and-struct-attributes.md)<br/>
[參數屬性](parameter-attributes.md)<br/>
[first_is](first-is.md)<br/>
[last_is](last-is.md)<br/>
[max_is](max-is.md)<br/>
[length_is](length-is.md)
