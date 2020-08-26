---
title: '在 (c + + COM 屬性) '
ms.date: 10/02/2018
f1_keywords:
- vc-attr.in
helpviewer_keywords:
- in attribute
ms.assetid: 7b450cc4-4d2e-4910-a195-7487c6b7c373
ms.openlocfilehash: 2838a00ffe365f42fb7778b654306eb0c73b5996
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/25/2020
ms.locfileid: "88842230"
---
# <a name="in-c"></a>in (C++)

指出參數要從呼叫程式傳遞至被呼叫的進程。

## <a name="syntax"></a>語法

```cpp
[in]
```

## <a name="remarks"></a>備註

**In** c + + 屬性具有[與 MIDL 屬性相同的功能](/windows/win32/Midl/in)。

## <a name="example"></a>範例

如需如何**在中**使用的範例[，請參閱](bindable.md)可系結。

## <a name="requirements"></a>規格需求

| 屬性內容 | 值 |
|-|-|
|**適用於**|介面參數，介面方法|
|**重複**|否|
|**必要的屬性**|無|
|**無效屬性**|**retval**|

如需有關屬性內容的詳細資訊，請參閱 [屬性內容](cpp-attributes-com-net.md#contexts)。

## <a name="see-also"></a>另請參閱

[IDL 屬性](idl-attributes.md)<br/>
[參數屬性](parameter-attributes.md)<br/>
[方法屬性](method-attributes.md)<br/>
[值](defaultvalue.md)<br/>
[id](id.md)<br/>
[擴展](out-cpp.md)
