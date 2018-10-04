---
title: propget （c + + COM 屬性） |Microsoft Docs
ms.custom: ''
ms.date: 10/02/2018
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.propget
dev_langs:
- C++
helpviewer_keywords:
- propget attribute
ms.assetid: c9d4a97f-36dd-4b61-8eb0-b1a217598f14
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 44a5b06a4d94bc431d33fa29cdcef4738e43ca54
ms.sourcegitcommit: 955ef0f9d966e7c9c65e040f1e28fa83abe102a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/04/2018
ms.locfileid: "48790922"
---
# <a name="propget"></a>propget

指定屬性存取子函式。

## <a name="syntax"></a>語法

```cpp
[propget]
```

## <a name="remarks"></a>備註

**Propget** c + + 屬性具有相同的功能[propget](/windows/desktop/Midl/propget) MIDL 屬性。

## <a name="example"></a>範例

範例，請參閱[可繫結](bindable.md)範例使用**propget**。

## <a name="requirements"></a>需求

### <a name="attribute-context"></a>屬性內容

|||
|-|-|
|**適用於**|方法|
|**可重複**|否|
|**必要屬性**|無|
|**無效屬性**|`propput`, `propputref`|

如需有關屬性內容的詳細資訊，請參閱 <<c0> [ 屬性內容](cpp-attributes-com-net.md#contexts)。

## <a name="see-also"></a>另請參閱

[IDL 屬性](idl-attributes.md)<br/>
[方法屬性](method-attributes.md)<br/>
[propput](propput.md)<br/>
[propputref](propputref.md)  