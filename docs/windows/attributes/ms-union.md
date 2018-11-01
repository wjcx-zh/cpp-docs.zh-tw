---
title: ms_union （c + + COM 屬性）
ms.date: 10/02/2018
f1_keywords:
- vc-attr.ms_union
helpviewer_keywords:
- ms_union attribute
ms.assetid: bb548689-6962-457e-af56-8ffdf68987eb
ms.openlocfilehash: 6b9788fc02a3bf4d59d34823ba83d86f97298597
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50642464"
---
# <a name="msunion"></a>ms_union

控制 nonencapsulated 等位的網路資料表示法對齊方式。

## <a name="syntax"></a>語法

```cpp
[ms_union]
```

## <a name="remarks"></a>備註

**Ms_union** c + + 屬性具有相同的功能[ms_union](/windows/desktop/Midl/ms-union-attrib) MIDL 屬性。

## <a name="example"></a>範例

下列程式碼顯示的位置**ms_union**:

```cpp
// cpp_attr_ref_ms_union.cpp
// compile with: /LD
#include <unknwn.h>
[object, ms_union, uuid("00000000-0000-0000-0000-000000000001")]
__interface IFireTabCtrl {
   HRESULT DisplayString([in, string] char * p1);
};

[export, switch_type(short)] union _WILLIE_UNION_TYPE  {
   [case(24)]
      float fMays;
   [case(25)]
      double dMcCovey;
   [default]
      int x;
};

[public] typedef _WILLIE_UNION_TYPE WILLIE_UNION_TYPE;

[module(name="ATLFIRELib")];
```

## <a name="requirements"></a>需求

### <a name="attribute-context"></a>屬性內容

|||
|-|-|
|**適用於**|Nonencapsulated 等位|
|**可重複**|否|
|**必要屬性**|無|
|**無效屬性**|`dispinterface`|

如需詳細資訊，請參閱 [屬性內容](cpp-attributes-com-net.md#contexts)。

## <a name="see-also"></a>另請參閱

[IDL 屬性](idl-attributes.md)<br/>
[Typedef、Enum、Union 和 Struct 屬性](typedef-enum-union-and-struct-attributes.md)