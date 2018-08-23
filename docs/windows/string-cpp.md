---
title: 字串 （c + +） |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.string
dev_langs:
- C++
helpviewer_keywords:
- string attribute
ms.assetid: ddde900a-2e99-4fcd-86e8-57e1bdba7c93
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: eb3a57cec78c0ea02e16edd890d2a66362bfc011
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2018
ms.locfileid: "42594865"
---
# <a name="string-c"></a>string (C++)

表示一維**char**， **wchar_t**， `byte` （或同等權限） 做為字串，則必須處理陣列或這類陣列的指標。

## <a name="syntax"></a>語法

```cpp
[string]
```

## <a name="remarks"></a>備註

**字串**c + + 屬性具有相同的功能[字串](http://msdn.microsoft.com/library/windows/desktop/aa367270)MIDL 屬性。

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
|**必要屬性**|無|
|**無效屬性**|無|

如需有關屬性內容的詳細資訊，請參閱 [屬性內容](../windows/attribute-contexts.md)。

## <a name="see-also"></a>另請參閱

[IDL 屬性](../windows/idl-attributes.md)  
[陣列屬性](../windows/array-attributes.md)  
[export](../windows/export.md)  