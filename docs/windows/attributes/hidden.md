---
title: hidden （C++ COM 屬性）
ms.date: 10/02/2018
f1_keywords:
- vc-attr.hidden
helpviewer_keywords:
- hidden attribute
ms.assetid: 199c96dd-fc07-46c7-af93-92020aebebe7
ms.openlocfilehash: 75b03877b1204d6e1c4770f5ba9c8c88338b3394
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/15/2019
ms.locfileid: "69501453"
---
# <a name="hidden"></a>隱藏

表示專案存在，但不應該顯示在使用者導向的瀏覽器中。

## <a name="syntax"></a>語法

```cpp
[hidden]
```

## <a name="remarks"></a>備註

**Hidden** C++屬性的功能與[隱藏](/windows/win32/Midl/hidden)的 MIDL 屬性相同。

## <a name="example"></a>範例

如需如何使用**hidden**的範例，請參閱可系[結的範例](bindable.md)。

## <a name="requirements"></a>需求

### <a name="attribute-context"></a>屬性內容

|||
|-|-|
|**適用於**|**介面**、**類別**、**結構**、方法、屬性|
|**可重複**|否|
|**必要屬性**|**coclass**（套用至**類別**或**結構**時）|
|**無效屬性**|None|

如需詳細資訊，請參閱 [屬性內容](cpp-attributes-com-net.md#contexts)。

## <a name="see-also"></a>另請參閱

[IDL 屬性](idl-attributes.md)<br/>
[介面屬性](interface-attributes.md)<br/>
[類別屬性](class-attributes.md)<br/>
[方法屬性](method-attributes.md)