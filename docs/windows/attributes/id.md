---
title: 識別碼 (C++ COM 屬性)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.id
helpviewer_keywords:
- id attribute
ms.assetid: a48d2c99-c5d2-4f46-bf96-5ac88dcb5d0c
ms.openlocfilehash: 5faf08418771deda3086a434cff6b1900a37e36e
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62409495"
---
# <a name="id"></a>id

指定*dispid* （屬性或方法，在介面或 dispinterface） 的成員函式的參數。

## <a name="syntax"></a>語法

```cpp
[ id(dispid) ]
```

### <a name="parameters"></a>參數

*dispid*<br/>
介面方法的分派識別碼。

## <a name="remarks"></a>備註

**識別碼**C++屬性具有相同的功能[識別碼](/windows/desktop/Midl/id)MIDL 屬性。

## <a name="example"></a>範例

範例，請參閱[可繫結](bindable.md)如需如何使用的範例**識別碼**。

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