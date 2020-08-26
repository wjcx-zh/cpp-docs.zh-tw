---
title: 'retval (c + + COM 屬性) '
ms.date: 10/02/2018
f1_keywords:
- vc-attr.retval
helpviewer_keywords:
- retval attribute
ms.assetid: bfa16f08-157d-4eea-afde-1232c54b8501
ms.openlocfilehash: f90893390bc67cb495e646f61e3d61a994e42e50
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/25/2020
ms.locfileid: "88845987"
---
# <a name="retval"></a>retval

指定接收成員傳回值的參數。

## <a name="syntax"></a>語法

```cpp
[retval]
```

## <a name="remarks"></a>備註

**Retval** c + + 屬性具有與[retval](/windows/win32/Midl/retval) MIDL 屬性相同的功能。

**retval** 必須出現在函式宣告中的最後一個引數上。

## <a name="example"></a>範例

請參閱可系結的 [範例，以](bindable.md) 取得 **retval**的範例使用。

## <a name="requirements"></a>規格需求

| 屬性內容 | 值 |
|-|-|
|**適用於**|介面參數，介面方法|
|**重複**|否|
|**必要的屬性**|**擴展**|
|**無效屬性**|**in**|

如需有關屬性內容的詳細資訊，請參閱 [屬性內容](cpp-attributes-com-net.md#contexts)。

## <a name="see-also"></a>另請參閱

[IDL 屬性](idl-attributes.md)<br/>
[參數屬性](parameter-attributes.md)<br/>
[方法屬性](method-attributes.md)
