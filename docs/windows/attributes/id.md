---
title: 'id (c + + COM 屬性) '
ms.date: 10/02/2018
f1_keywords:
- vc-attr.id
helpviewer_keywords:
- id attribute
ms.assetid: a48d2c99-c5d2-4f46-bf96-5ac88dcb5d0c
ms.openlocfilehash: f67bf21fbe0040884cba4a54ed8d2a230cb20cd6
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/25/2020
ms.locfileid: "88830549"
---
# <a name="id"></a>id

指定成員函式的 *dispid* 參數， (在介面或) 中的屬性或方法。

## <a name="syntax"></a>語法

```cpp
[ id(dispid) ]
```

### <a name="parameters"></a>參數

*dispid*<br/>
介面方法的分派識別碼。

## <a name="remarks"></a>備註

**Id** c + + 屬性具有與[id](/windows/win32/Midl/id) MIDL 屬性相同的功能。

## <a name="example"></a>範例

如需如何使用**id**的[範例，請](bindable.md)參閱可系結的範例。

## <a name="requirements"></a>規格需求

| 屬性內容 | 值 |
|-|-|
|**適用於**|介面方法|
|**重複**|否|
|**必要的屬性**|無|
|**無效屬性**|無|

如需詳細資訊，請參閱 [屬性內容](cpp-attributes-com-net.md#contexts)。

## <a name="see-also"></a>另請參閱

[IDL 屬性](idl-attributes.md)<br/>
[方法屬性](method-attributes.md)<br/>
[資料成員屬性](data-member-attributes.md)<br/>
[值](defaultvalue.md)<br/>
[in](in-cpp.md)<br/>
[擴展](out-cpp.md)
