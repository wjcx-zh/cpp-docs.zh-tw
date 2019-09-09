---
title: in （C++ COM 屬性）
ms.date: 10/02/2018
f1_keywords:
- vc-attr.in
helpviewer_keywords:
- in attribute
ms.assetid: 7b450cc4-4d2e-4910-a195-7487c6b7c373
ms.openlocfilehash: e97008d0399764beeca73dbbc5914e4b891df748
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/15/2019
ms.locfileid: "69514599"
---
# <a name="in-c"></a>in (C++)

表示參數會從呼叫程式傳遞至被呼叫的進程。

## <a name="syntax"></a>語法

```cpp
[in]
```

## <a name="remarks"></a>備註

**In** C++屬性的功能與 MIDL 屬性[中](/windows/win32/Midl/in)的相同。

## <a name="example"></a>範例

如需如何**在中**使用的範例[，請參閱](bindable.md)可系結。

## <a name="requirements"></a>需求

### <a name="attribute-context"></a>屬性內容

|||
|-|-|
|**適用於**|介面參數，介面方法|
|**可重複**|否|
|**必要屬性**|無|
|**無效屬性**|**retval**|

如需有關屬性內容的詳細資訊，請參閱 [屬性內容](cpp-attributes-com-net.md#contexts)。

## <a name="see-also"></a>另請參閱

[IDL 屬性](idl-attributes.md)<br/>
[參數屬性](parameter-attributes.md)<br/>
[方法屬性](method-attributes.md)<br/>
[defaultvalue](defaultvalue.md)<br/>
[id](id.md)<br/>
[out](out-cpp.md)