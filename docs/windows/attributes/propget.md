---
title: propget (C++ COM 屬性)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.propget
helpviewer_keywords:
- propget attribute
ms.assetid: c9d4a97f-36dd-4b61-8eb0-b1a217598f14
ms.openlocfilehash: 8f60e8e8fc98ba3b75acefe80812069bfac78e6c
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62407623"
---
# <a name="propget"></a>propget

指定屬性存取子函式。

## <a name="syntax"></a>語法

```cpp
[propget]
```

## <a name="remarks"></a>備註

**Propget** C++屬性具有相同的功能[propget](/windows/desktop/Midl/propget) MIDL 屬性。

## <a name="example"></a>範例

範例，請參閱[可繫結](bindable.md)範例使用**propget**。

## <a name="requirements"></a>需求

### <a name="attribute-context"></a>屬性內容

|||
|-|-|
|**適用於**|方法|
|**可重複**|否|
|**必要屬性**|None|
|**無效屬性**|`propput`、 `propputref`|

如需有關屬性內容的詳細資訊，請參閱 [屬性內容](cpp-attributes-com-net.md#contexts)。

## <a name="see-also"></a>另請參閱

[IDL 屬性](idl-attributes.md)<br/>
[方法屬性](method-attributes.md)<br/>
[propput](propput.md)<br/>
[propputref](propputref.md)