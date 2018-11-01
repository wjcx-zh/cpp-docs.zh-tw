---
title: propputref （c + + COM 屬性）
ms.date: 10/02/2018
f1_keywords:
- vc-attr.propputref
helpviewer_keywords:
- propputref attribute
ms.assetid: 9b0aed74-fdc7-4e59-9117-949bea4f86dd
ms.openlocfilehash: 0ebf39be6d83e7c5a64ad29f34f9accf0743dbf4
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50551277"
---
# <a name="propputref"></a>propputref

指定使用參考而非值的屬性設定函式。

## <a name="syntax"></a>語法

```cpp
[propputref]
```

## <a name="remarks"></a>備註

**Propputref** c + + 屬性具有相同的功能[propputref](/windows/desktop/Midl/propputref) MIDL 屬性。

## <a name="example"></a>範例

範例，請參閱[可繫結](bindable.md)範例使用**propputref**。

## <a name="requirements"></a>需求

### <a name="attribute-context"></a>屬性內容

|||
|-|-|
|**適用於**|方法|
|**可重複**|否|
|**必要屬性**|無|
|**無效屬性**|`propget`、 `propput`|

如需有關屬性內容的詳細資訊，請參閱 [屬性內容](cpp-attributes-com-net.md#contexts)。

## <a name="see-also"></a>另請參閱

[IDL 屬性](idl-attributes.md)<br/>
[方法屬性](method-attributes.md)<br/>
[propget](propget.md)<br/>
[propput](propput.md)