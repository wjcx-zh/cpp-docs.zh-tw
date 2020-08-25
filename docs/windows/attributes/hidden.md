---
title: '隱藏 (c + + COM 屬性) '
ms.date: 10/02/2018
f1_keywords:
- vc-attr.hidden
helpviewer_keywords:
- hidden attribute
ms.assetid: 199c96dd-fc07-46c7-af93-92020aebebe7
ms.openlocfilehash: ffa1ce01cfd570de7b699e415f10b27acf525047
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/25/2020
ms.locfileid: "88830952"
---
# <a name="hidden"></a>隱藏

指出專案存在，但不應該在使用者導向的瀏覽器中顯示。

## <a name="syntax"></a>語法

```cpp
[hidden]
```

## <a name="remarks"></a>備註

**隱藏**的 c + + 屬性具有與[隱藏](/windows/win32/Midl/hidden)MIDL 屬性相同的功能。

## <a name="example"></a>範例

如需如何使用**hidden**的範例，請參閱可系[結的範例](bindable.md)。

## <a name="requirements"></a>規格需求

| 屬性內容 | 值 |
|-|-|
|**適用於**|**interface**、 **`class`** 、 **`struct`** 、method、property|
|**重複**|否|
|**必要的屬性**|**coclass**套用至 **`class`** 或) 的 coclass **`struct`** (|
|**無效屬性**|無|

如需詳細資訊，請參閱 [屬性內容](cpp-attributes-com-net.md#contexts)。

## <a name="see-also"></a>另請參閱

[IDL 屬性](idl-attributes.md)<br/>
[介面屬性](interface-attributes.md)<br/>
[類別屬性](class-attributes.md)<br/>
[方法屬性](method-attributes.md)
