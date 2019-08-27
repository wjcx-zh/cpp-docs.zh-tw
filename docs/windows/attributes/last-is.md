---
title: last_is (C++ COM 屬性)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.last_is
helpviewer_keywords:
- last_is attribute
ms.assetid: 9e045ac0-fa38-4249-af55-67bde5d0a58c
ms.openlocfilehash: 4745d4eb59fd2adb79937b34184081dbbd0814fb
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/15/2019
ms.locfileid: "69514514"
---
# <a name="last_is"></a>last_is

指定要傳送之最後一個陣列元素的索引。

## <a name="syntax"></a>語法

```cpp
[ last_is("expression") ]
```

### <a name="parameters"></a>參數

*expression*<br/>
一或多個 C 語言運算式。 允許空的引數位置。

## <a name="remarks"></a>備註

**Last_is** C++屬性具有與[last_is](/windows/win32/Midl/last-is) MIDL 屬性相同的功能。

## <a name="example"></a>範例

如需如何指定陣列區段的範例, 請參閱[first_is](first-is.md) 。

## <a name="requirements"></a>需求

### <a name="attribute-context"></a>屬性內容

|||
|-|-|
|**適用於**|**Struct**或**union**中的欄位, 介面參數, 介面方法|
|**可重複**|否|
|**必要屬性**|None|
|**無效屬性**|無|

如需詳細資訊，請參閱 [屬性內容](cpp-attributes-com-net.md#contexts)。

## <a name="see-also"></a>另請參閱

[IDL 屬性](idl-attributes.md)<br/>
[Typedef、Enum、Union 和 Struct 屬性](typedef-enum-union-and-struct-attributes.md)<br/>
[參數屬性](parameter-attributes.md)<br/>
[first_is](first-is.md)<br/>
[max_is](max-is.md)<br/>
[length_is](length-is.md)<br/>
[size_is](size-is.md)