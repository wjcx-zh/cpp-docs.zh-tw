---
title: 'ref (c + + COM 屬性) '
ms.date: 10/02/2018
f1_keywords:
- vc-attr.ref
helpviewer_keywords:
- ref attribute
ms.assetid: 67e82d3e-07d9-4ef8-bf2b-0a4491d12557
ms.openlocfilehash: 92b3c7b2cddf17a70a949914ef82540457696f20
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/25/2020
ms.locfileid: "88846104"
---
# <a name="ref-c"></a>ref (C++)

識別參考指標。

## <a name="syntax"></a>語法

```cpp
[ref]
```

## <a name="remarks"></a>備註

**Ref** c + + 屬性具有與[ref](/windows/win32/Midl/ref) MIDL 屬性相同的功能。

## <a name="example"></a>範例

下列程式碼顯示如何使用 **ref** 屬性：

```cpp
// cpp_attr_ref_ref.cpp
// compile with: /LD
#include <windows.h>
[module(name="ATLFIRELib")];
[dispinterface, uuid("00000000-0000-0000-0000-000000000001")]
__interface IFireTabCtrl
{
   [id(1), unique] char * GetFirstName([in, ref] char * pszFullName );
};
```

## <a name="requirements"></a>規格需求

| 屬性內容 | 值 |
|-|-|
|**適用於**|**`typedef`**、介面參數、介面方法|
|**重複**|否|
|**必要的屬性**|無|
|**無效屬性**|無|

如需有關屬性內容的詳細資訊，請參閱 [屬性內容](cpp-attributes-com-net.md#contexts)。

## <a name="see-also"></a>另請參閱

[IDL 屬性](idl-attributes.md)<br/>
[Typedef、Enum、Union 和 Struct 屬性](typedef-enum-union-and-struct-attributes.md)<br/>
[參數屬性](parameter-attributes.md)
