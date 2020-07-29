---
title: length_is （c + + COM 屬性）
ms.date: 10/02/2018
f1_keywords:
- vc-attr.length_is
helpviewer_keywords:
- length_is attribute
ms.assetid: 1d99b883-84bb-4b1e-b098-eb780fc94f40
ms.openlocfilehash: 7e6ab9ec0f6f55ab0be9624b7343b087b41f2a54
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87215240"
---
# <a name="length_is"></a>length_is

指定要傳送的陣列元素數目。

## <a name="syntax"></a>語法

```cpp
[ length_is("expression") ]
```

### <a name="parameters"></a>參數

*expression*<br/>
一或多個 C 語言運算式。 允許空的引數位置。

## <a name="remarks"></a>備註

**Length_is** c + + 屬性具有與[length_is](/windows/win32/Midl/length-is) MIDL 屬性相同的功能。

## <a name="example"></a>範例

如需如何指定陣列區段的範例，請參閱[first_is](first-is.md) 。

## <a name="requirements"></a>需求

### <a name="attribute-context"></a>屬性內容

|||
|-|-|
|**適用於**|或中的欄位 **`struct`** **`union`** ，介面參數，介面方法|
|**可重複**|否|
|**必要的屬性**|無|
|**無效屬性**|無|

如需詳細資訊，請參閱 [屬性內容](cpp-attributes-com-net.md#contexts)。

## <a name="see-also"></a>另請參閱

[IDL 屬性](idl-attributes.md)<br/>
[Typedef、Enum、Union 和 Struct 屬性](typedef-enum-union-and-struct-attributes.md)<br/>
[參數屬性](parameter-attributes.md)<br/>
[first_is](first-is.md)<br/>
[max_is](max-is.md)<br/>
[last_is](last-is.md)<br/>
[size_is](size-is.md)
