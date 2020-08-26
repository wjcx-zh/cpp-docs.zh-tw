---
title: 'pointer_default (c + + COM 屬性) '
ms.date: 10/02/2018
f1_keywords:
- vc-attr.pointer_default
helpviewer_keywords:
- pointer_default attribute
ms.assetid: 2d0c7bbc-a1e8-4337-9e54-e304523e2735
ms.openlocfilehash: e4e5ce03e8c0e6ca19814f5d228305b0d97322f9
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/25/2020
ms.locfileid: "88836188"
---
# <a name="pointer_default"></a>pointer_default

指定所有指標的預設指標屬性，除了出現在參數清單中的最上層指標。

## <a name="syntax"></a>語法

```cpp
[ pointer_default(value) ]
```

### <a name="parameters"></a>參數

*value*<br/>
描述指標類型的值： **ptr**、 **ref**或 **unique**。

## <a name="remarks"></a>備註

**Pointer_default** c + + 屬性具有與[pointer_default](/windows/win32/Midl/pointer-default) MIDL 屬性相同的功能。

## <a name="example"></a>範例

如需**pointer_default**使用範例，請參閱[defaultvalue](defaultvalue.md)的範例。

## <a name="requirements"></a>規格需求

| 屬性內容 | 值 |
|-|-|
|**適用於**|**interface**|
|**重複**|否|
|**必要的屬性**|無|
|**無效屬性**|無|

如需有關屬性內容的詳細資訊，請參閱 [屬性內容](cpp-attributes-com-net.md#contexts)。

## <a name="see-also"></a>另請參閱

[IDL 屬性](idl-attributes.md)<br/>
[介面屬性](interface-attributes.md)
