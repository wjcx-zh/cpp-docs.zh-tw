---
title: 字串 (C++ COM 屬性)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.string
helpviewer_keywords:
- string attribute
ms.assetid: ddde900a-2e99-4fcd-86e8-57e1bdba7c93
ms.openlocfilehash: e1b528fb922a15655de403c6099ee1d36e2fb3de
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62407272"
---
# <a name="string-c"></a>string (C++)

表示一維**char**， **wchar_t**， `byte` （或同等權限） 做為字串，則必須處理陣列或這類陣列的指標。

## <a name="syntax"></a>語法

```cpp
[string]
```

## <a name="remarks"></a>備註

**字串**C++屬性具有相同的功能[字串](/windows/desktop/Midl/string)MIDL 屬性。

## <a name="example"></a>範例

下列程式碼示範如何使用**字串**介面上，並在 typedef 上：

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
|**適用於**|陣列或指標的陣列、 介面參數、 介面方法|
|**可重複**|否|
|**必要屬性**|None|
|**無效屬性**|None|

如需有關屬性內容的詳細資訊，請參閱 [屬性內容](cpp-attributes-com-net.md#contexts)。

## <a name="see-also"></a>另請參閱

[IDL 屬性](idl-attributes.md)<br/>
[陣列屬性](array-attributes.md)<br/>
[export](export.md)