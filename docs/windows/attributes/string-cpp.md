---
title: string (C++ COM 屬性)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.string
helpviewer_keywords:
- string attribute
ms.assetid: ddde900a-2e99-4fcd-86e8-57e1bdba7c93
ms.openlocfilehash: 978f1f546c0df8de4ff167ddf5ddf724feb31b6e
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/15/2019
ms.locfileid: "69514014"
---
# <a name="string-c"></a>string (C++)

表示一維**char**、 **wchar_t**、 `byte` (或對等) 陣列或這類陣列的指標必須被視為字串。

## <a name="syntax"></a>語法

```cpp
[string]
```

## <a name="remarks"></a>備註

**String** C++屬性的功能與[字串](/windows/win32/Midl/string)MIDL 屬性相同。

## <a name="example"></a>範例

下列程式碼示範如何在介面和 typedef 上使用**string** :

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

## <a name="requirements"></a>需求

### <a name="attribute-context"></a>屬性內容

|||
|-|-|
|**適用於**|陣列的陣列或指標, 介面參數, 介面方法|
|**可重複**|否|
|**必要屬性**|無|
|**無效屬性**|None|

如需有關屬性內容的詳細資訊，請參閱 [屬性內容](cpp-attributes-com-net.md#contexts)。

## <a name="see-also"></a>另請參閱

[IDL 屬性](idl-attributes.md)<br/>
[陣列屬性](array-attributes.md)<br/>
[export](export.md)