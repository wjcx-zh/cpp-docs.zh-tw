---
title: id （C++ COM 屬性）
ms.date: 10/02/2018
f1_keywords:
- vc-attr.id
helpviewer_keywords:
- id attribute
ms.assetid: a48d2c99-c5d2-4f46-bf96-5ac88dcb5d0c
ms.openlocfilehash: 6f1d1d2b9d147e8b33b3b5fae629e0805971bb71
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/15/2019
ms.locfileid: "69501412"
---
# <a name="id"></a>id

指定成員函式的*dispid*參數（屬性或方法，在介面或分配介面中）。

## <a name="syntax"></a>語法

```cpp
[ id(dispid) ]
```

### <a name="parameters"></a>參數

*dispid*<br/>
介面方法的分派識別碼。

## <a name="remarks"></a>備註

**Id** C++屬性的功能與[id](/windows/win32/Midl/id) MIDL 屬性相同。

## <a name="example"></a>範例

如需如何使用**id**的[範例，請](bindable.md)參閱可系結的範例。

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
[資料成員屬性](data-member-attributes.md)<br/>
[defaultvalue](defaultvalue.md)<br/>
[in](in-cpp.md)<br/>
[out](out-cpp.md)