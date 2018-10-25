---
title: last_is （c + + COM 屬性） |Microsoft Docs
ms.custom: ''
ms.date: 10/02/2018
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.last_is
dev_langs:
- C++
helpviewer_keywords:
- last_is attribute
ms.assetid: 9e045ac0-fa38-4249-af55-67bde5d0a58c
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 45b55886512c411cf82fe30c94b8d5087a811ad7
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/25/2018
ms.locfileid: "50053626"
---
# <a name="lastis"></a>last_is

指定要傳送的最後一個陣列元素的索引。

## <a name="syntax"></a>語法

```cpp
[ last_is("expression") ]
```

### <a name="parameters"></a>參數

*運算式*<br/>
一或多個 C 語言的運算式。 允許空白的引數位置。

## <a name="remarks"></a>備註

**Last_is** c + + 屬性具有相同的功能[last_is](/windows/desktop/Midl/last-is) MIDL 屬性。

## <a name="example"></a>範例

請參閱[first_is](first-is.md)如需如何指定的陣列區段的範例。

## <a name="requirements"></a>需求

### <a name="attribute-context"></a>屬性內容

|||
|-|-|
|**適用於**|欄位**結構**或是**聯集**，參數的介面，介面方法|
|**可重複**|否|
|**必要屬性**|無|
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