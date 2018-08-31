---
title: wire_marshal |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.wire_marshal
dev_langs:
- C++
helpviewer_keywords:
- wire_marshal attribute
ms.assetid: 244f9d72-776d-4ebd-b60a-cee600a126b5
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 94504cea86059f835d9cbda7cbf2bcdeafab589b
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/29/2018
ms.locfileid: "43214106"
---
# <a name="wiremarshal"></a>wire_marshal

指定將用於傳輸，而不是應用程式特定資料類型的資料類型。

## <a name="syntax"></a>語法

```cpp
[wire_marshal]
```

## <a name="remarks"></a>備註

**Wire_marshal** c + + 屬性具有相同的功能[wire_marshal](/windows/desktop/Midl/wire-marshal) MIDL 屬性。

## <a name="example"></a>範例

下列程式碼範例將示範用法**wire_marshal**:

```cpp
// cpp_attr_ref_wire_marshal.cpp
// compile with: /LD
#include "windows.h"
[module(name="MyLibrary")];

[export, public] typedef unsigned long _FOUR_BYTE_DATA;

[export] typedef struct _TWO_X_TWO_BYTE_DATA {
   unsigned short low;
   unsigned short high;
} TWO_X_TWO_BYTE_DATA ;

[export, wire_marshal(TWO_X_TWO_BYTE_DATA)] typedef _FOUR_BYTE_DATA FOUR_BYTE_DATA;
```

## <a name="requirements"></a>需求

### <a name="attribute-context"></a>屬性內容

|||
|-|-|
|**適用於**|**typedef**|
|**可重複**|否|
|**必要屬性**|無|
|**無效屬性**|無|

如需有關屬性內容的詳細資訊，請參閱 [屬性內容](../windows/attribute-contexts.md)。

## <a name="see-also"></a>另請參閱

[IDL 屬性](../windows/idl-attributes.md)  
[Typedef、Enum、Union 和 Struct 屬性](../windows/typedef-enum-union-and-struct-attributes.md)  