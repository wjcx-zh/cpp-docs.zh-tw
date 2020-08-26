---
title: 'propput (c + + COM 屬性) '
ms.date: 10/02/2018
f1_keywords:
- vc-attr.propput
helpviewer_keywords:
- propput attribute
ms.assetid: 1f84dda9-9cce-4e16-aaf0-b2c5219827f2
ms.openlocfilehash: 11f216dd183f3977aee9af90c6579d01cad45fdf
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/25/2020
ms.locfileid: "88839942"
---
# <a name="propput"></a>propput

指定屬性設定函式。

## <a name="syntax"></a>語法

```cpp
[propput]
```

## <a name="remarks"></a>備註

**Propput** c + + 屬性具有與[propput](/windows/win32/Midl/propput) MIDL 屬性相同的功能。

## <a name="example"></a>範例

[如需](bindable.md) **propput**的範例用法，請參閱可系結的範例。

## <a name="requirements"></a>規格需求

| 屬性內容 | 值 |
|-|-|
|**適用於**|方法|
|**重複**|否|
|**必要的屬性**|無|
|**無效屬性**|`propget`, `propputref`|

如需有關屬性內容的詳細資訊，請參閱 [屬性內容](cpp-attributes-com-net.md#contexts)。

## <a name="see-also"></a>另請參閱

[IDL 屬性](idl-attributes.md)<br/>
[方法屬性](method-attributes.md)<br/>
[propget](propget.md)<br/>
[propputref](propputref.md)
