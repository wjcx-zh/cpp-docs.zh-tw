---
title: propput (C++ COM 屬性)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.propput
helpviewer_keywords:
- propput attribute
ms.assetid: 1f84dda9-9cce-4e16-aaf0-b2c5219827f2
ms.openlocfilehash: c9853b38675abfa0a94a319ac752eb2ef61a48e0
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62407519"
---
# <a name="propput"></a>propput

指定屬性設定函式。

## <a name="syntax"></a>語法

```cpp
[propput]
```

## <a name="remarks"></a>備註

**Propput** C++屬性具有相同的功能[propput](/windows/desktop/Midl/propput) MIDL 屬性。

## <a name="example"></a>範例

範例，請參閱[可繫結](bindable.md)範例使用**propput**。

## <a name="requirements"></a>需求

### <a name="attribute-context"></a>屬性內容

|||
|-|-|
|**適用於**|方法|
|**可重複**|否|
|**必要屬性**|None|
|**無效屬性**|`propget`、 `propputref`|

如需有關屬性內容的詳細資訊，請參閱 [屬性內容](cpp-attributes-com-net.md#contexts)。

## <a name="see-also"></a>另請參閱

[IDL 屬性](idl-attributes.md)<br/>
[方法屬性](method-attributes.md)<br/>
[propget](propget.md)<br/>
[propputref](propputref.md)