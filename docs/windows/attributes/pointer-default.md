---
title: pointer_default (C++ COM 屬性)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.pointer_default
helpviewer_keywords:
- pointer_default attribute
ms.assetid: 2d0c7bbc-a1e8-4337-9e54-e304523e2735
ms.openlocfilehash: c70c372e5f1c3a9c2f620a1fa3505fb9d0436e79
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/15/2019
ms.locfileid: "69514266"
---
# <a name="pointer_default"></a>pointer_default

指定所有指標的預設指標屬性, 但出現在參數清單中的最上層指標除外。

## <a name="syntax"></a>語法

```cpp
[ pointer_default(value) ]
```

### <a name="parameters"></a>參數

*value*<br/>
描述指標類型的值: **ptr**、 **ref**或**unique**。

## <a name="remarks"></a>備註

**Pointer_default** C++屬性具有與[pointer_default](/windows/win32/Midl/pointer-default) MIDL 屬性相同的功能。

## <a name="example"></a>範例

如需使用**pointer_default**的範例, 請參閱[defaultvalue](defaultvalue.md)的範例。

## <a name="requirements"></a>需求

### <a name="attribute-context"></a>屬性內容

|||
|-|-|
|**適用於**|**interface**|
|**可重複**|否|
|**必要屬性**|None|
|**無效屬性**|無|

如需有關屬性內容的詳細資訊，請參閱 [屬性內容](cpp-attributes-com-net.md#contexts)。

## <a name="see-also"></a>另請參閱

[IDL 屬性](idl-attributes.md)<br/>
[介面屬性](interface-attributes.md)