---
title: 'pragma (c + + COM 屬性) '
ms.date: 10/02/2018
f1_keywords:
- vc-attr.pragma
helpviewer_keywords:
- pragma attribute
ms.assetid: 3f90d023-b8b5-4007-8311-008bb72cbea1
ms.openlocfilehash: e5683a6f52eccf9eae7c29010849a148e506b286
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/25/2020
ms.locfileid: "88836165"
---
# <a name="pragma"></a>pragma

將指定的字串發出至產生的 .idl 檔案，而不使用引號。

## <a name="syntax"></a>語法

```cpp
[ pragma(pragma_statement) ];
```

### <a name="parameters"></a>參數

*pragma_statement*<br/>
您要進入產生的 .idl 檔案的 pragma。

## <a name="remarks"></a>備註

**Pragma** c + + 屬性具有與[pragma](/windows/win32/Midl/pragma) MIDL 屬性相同的功能。

## <a name="example"></a>範例

```cpp
// cpp_attr_ref_pragma.cpp
// compile with: /LD
#include "unknwn.h"
[module(name="MyLib")];
[pragma(pack(4))];

[dispinterface, uuid("00000000-0000-0000-0000-000000000001")]
__interface A
{
   [id(1)] HRESULT MyMethod ([in, satype("BSTR")] SAFEARRAY **p);
};
```

## <a name="requirements"></a>規格需求

| 屬性內容 | 值 |
|-|-|
|**適用於**|任何位置|
|**重複**|否|
|**必要的屬性**|無|
|**無效屬性**|無|

如需有關屬性內容的詳細資訊，請參閱 [屬性內容](cpp-attributes-com-net.md#contexts)。

## <a name="see-also"></a>另請參閱

[IDL 屬性](idl-attributes.md)<br/>
[獨立屬性](stand-alone-attributes.md)<br/>
[pack](../../preprocessor/pack.md)
