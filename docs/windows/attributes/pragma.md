---
title: pragma (C++ COM 屬性)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.pragma
helpviewer_keywords:
- pragma attribute
ms.assetid: 3f90d023-b8b5-4007-8311-008bb72cbea1
ms.openlocfilehash: 5c3ee0d3f99bd27ca41d68b11c11522e92c8d40a
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/15/2019
ms.locfileid: "69514272"
---
# <a name="pragma"></a>pragma

將指定的字串發出到產生的 .idl 檔案中, 而不使用引號。

## <a name="syntax"></a>語法

```cpp
[ pragma(pragma_statement) ];
```

### <a name="parameters"></a>參數

*pragma_statement*<br/>
您想要移入產生之 .idl 檔的 pragma。

## <a name="remarks"></a>備註

**Pragma** C++屬性的功能與[pragma](/windows/win32/Midl/pragma) MIDL 屬性相同。

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

## <a name="requirements"></a>需求

### <a name="attribute-context"></a>屬性內容

|||
|-|-|
|**適用於**|任何位置|
|**可重複**|否|
|**必要屬性**|無|
|**無效屬性**|無|

如需有關屬性內容的詳細資訊，請參閱 [屬性內容](cpp-attributes-com-net.md#contexts)。

## <a name="see-also"></a>另請參閱

[IDL 屬性](idl-attributes.md)<br/>
[獨立屬性](stand-alone-attributes.md)<br/>
[pack](../../preprocessor/pack.md)