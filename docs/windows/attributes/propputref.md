---
title: 'propputref (c + + COM 屬性) '
ms.date: 10/02/2018
f1_keywords:
- vc-attr.propputref
helpviewer_keywords:
- propputref attribute
ms.assetid: 9b0aed74-fdc7-4e59-9117-949bea4f86dd
ms.openlocfilehash: dbb5d5966fc82f69be0ed7d2fa0a66ad558a7915
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/25/2020
ms.locfileid: "88839903"
---
# <a name="propputref"></a>propputref

指定使用參考而非值的屬性設定函數。

## <a name="syntax"></a>語法

```cpp
[propputref]
```

## <a name="remarks"></a>備註

**Propputref** c + + 屬性具有與[propputref](/windows/win32/Midl/propputref) MIDL 屬性相同的功能。

## <a name="example"></a>範例

[如需](bindable.md) **propputref**的範例用法，請參閱可系結的範例。

## <a name="requirements"></a>規格需求

| 屬性內容 | 值 |
|-|-|
|**適用於**|方法|
|**重複**|否|
|**必要的屬性**|無|
|**無效屬性**|`propget`, `propput`|

如需有關屬性內容的詳細資訊，請參閱 [屬性內容](cpp-attributes-com-net.md#contexts)。

## <a name="see-also"></a>另請參閱

[IDL 屬性](idl-attributes.md)<br/>
[方法屬性](method-attributes.md)<br/>
[propget](propget.md)<br/>
[propput](propput.md)
