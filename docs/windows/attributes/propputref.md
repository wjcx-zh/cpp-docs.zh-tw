---
title: propputref (C++ COM 屬性)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.propputref
helpviewer_keywords:
- propputref attribute
ms.assetid: 9b0aed74-fdc7-4e59-9117-949bea4f86dd
ms.openlocfilehash: e471e467c55e0b8a17be96fd1bcb3cd24cfafe06
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62407467"
---
# <a name="propputref"></a>propputref

指定使用參考而非值的屬性設定函式。

## <a name="syntax"></a>語法

```cpp
[propputref]
```

## <a name="remarks"></a>備註

**Propputref** C++屬性具有相同的功能[propputref](/windows/desktop/Midl/propputref) MIDL 屬性。

## <a name="example"></a>範例

範例，請參閱[可繫結](bindable.md)範例使用**propputref**。

## <a name="requirements"></a>需求

### <a name="attribute-context"></a>屬性內容

|||
|-|-|
|**適用於**|方法|
|**可重複**|否|
|**必要屬性**|None|
|**無效屬性**|`propget`、 `propput`|

如需有關屬性內容的詳細資訊，請參閱 [屬性內容](cpp-attributes-com-net.md#contexts)。

## <a name="see-also"></a>另請參閱

[IDL 屬性](idl-attributes.md)<br/>
[方法屬性](method-attributes.md)<br/>
[propget](propget.md)<br/>
[propput](propput.md)