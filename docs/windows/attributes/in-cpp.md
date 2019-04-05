---
title: 在 （c + + COM 屬性）
ms.date: 10/02/2018
f1_keywords:
- vc-attr.in
helpviewer_keywords:
- in attribute
ms.assetid: 7b450cc4-4d2e-4910-a195-7487c6b7c373
ms.openlocfilehash: 06d78552ef2ebb878ed630eb377e6249ba60cad4
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/05/2019
ms.locfileid: "59034533"
---
# <a name="in-c"></a>in (C++)

指出參數是要呼叫的程序從傳遞至呼叫的程序。

## <a name="syntax"></a>語法

```cpp
[in]
```

## <a name="remarks"></a>備註

**中**c + + 屬性具有相同的功能[在](/windows/desktop/Midl/in)MIDL 屬性。

## <a name="example"></a>範例

請參閱[可繫結](bindable.md)如需如何使用的範例**在**。

## <a name="requirements"></a>需求

### <a name="attribute-context"></a>屬性內容

|||
|-|-|
|**適用於**|介面參數，介面方法|
|**可重複**|否|
|**必要屬性**|None|
|**無效屬性**|**retval**|

如需有關屬性內容的詳細資訊，請參閱 [屬性內容](cpp-attributes-com-net.md#contexts)。

## <a name="see-also"></a>另請參閱

[IDL 屬性](idl-attributes.md)<br/>
[參數屬性](parameter-attributes.md)<br/>
[方法屬性](method-attributes.md)<br/>
[defaultvalue](defaultvalue.md)<br/>
[id](id.md)<br/>
[out](out-cpp.md)