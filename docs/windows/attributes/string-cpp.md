---
title: '字串 (c + + COM 屬性) '
ms.date: 10/02/2018
f1_keywords:
- vc-attr.string
helpviewer_keywords:
- string attribute
ms.assetid: ddde900a-2e99-4fcd-86e8-57e1bdba7c93
ms.openlocfilehash: 119e0aa60d123324c60825a9418e0b8c93696c5f
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/25/2020
ms.locfileid: "88845376"
---
# <a name="string-c"></a>string (C++)

指出一維 **`char`** 、 **`wchar_t`** 、 `byte` (或對等的) 陣列或這類陣列的指標必須視為字串。

## <a name="syntax"></a>語法

```cpp
[string]
```

## <a name="remarks"></a>備註

**字串**c + + 屬性具有與[字串](/windows/win32/Midl/string)MIDL 屬性相同的功能。

## <a name="example"></a>範例

下列程式碼示範如何在介面和 typedef 上使用 **字串** ：

```cpp
// cpp_attr_ref_string.cpp
// compile with: /LD
#include "unknwn.h"
[module(name="ATLFIRELib")];
[export, string] typedef char a[21];
[dispinterface, restricted, uuid("00000000-0000-0000-0000-000000000001")]
__interface IFireTabCtrl
{
   [id(1)] HRESULT Method3([in, string] char *pC);
};
```

## <a name="requirements"></a>規格需求

| 屬性內容 | 值 |
|-|-|
|**適用於**|陣列、介面參數、介面方法的陣列或指標|
|**重複**|否|
|**必要的屬性**|無|
|**無效屬性**|無|

如需有關屬性內容的詳細資訊，請參閱 [屬性內容](cpp-attributes-com-net.md#contexts)。

## <a name="see-also"></a>另請參閱

[IDL 屬性](idl-attributes.md)<br/>
[陣列屬性](array-attributes.md)<br/>
[出口](export.md)
