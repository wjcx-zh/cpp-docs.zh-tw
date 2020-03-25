---
title: defaultvtable （C++ COM 屬性）
ms.date: 10/02/2018
f1_keywords:
- vc-attr.defaultvtable
helpviewer_keywords:
- defaultvtable attribute
ms.assetid: 5b3ed483-f69e-44dd-80fc-952028eb9d73
ms.openlocfilehash: a15b3552e6b67fb0347a14c48414741edf31ac93
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80168262"
---
# <a name="defaultvtable"></a>defaultvtable

將介面定義為 COM 物件的預設 vtable 介面。

## <a name="syntax"></a>語法

```cpp
[ defaultvtable(interface) ]
```

### <a name="parameters"></a>參數

*interface*<br/>
您想要讓 COM 物件具有預設 vtable 的指定介面。

## <a name="remarks"></a>備註

**Defaultvtable** C++屬性具有與[defaultvtable](/windows/win32/Midl/defaultvtable) MIDL 屬性相同的功能。

## <a name="example"></a>範例

下列程式碼顯示使用**defaultvtable**指定預設介面之類別上的屬性：

```cpp
// cpp_attr_ref_defaultvtable.cpp
// compile with: /LD
#include <unknwn.h>
[module(name="MyLib")];

[object, uuid("00000000-0000-0000-0000-000000000001")]
__interface IMyI1 {
   HRESULT x();
};

[object, uuid("00000000-0000-0000-0000-000000000002")]
__interface IMyI2 {
   HRESULT x();
};

[object, uuid("00000000-0000-0000-0000-000000000003")]
__interface IMyI3 {
   HRESULT x();
};

[coclass, source(IMyI3, IMyI1), default(IMyI3, IMyI2), defaultvtable(IMyI1),
uuid("00000000-0000-0000-0000-000000000004")]
class CMyC3 : public IMyI3 {};
```

## <a name="requirements"></a>需求

### <a name="attribute-context"></a>屬性內容

|||
|-|-|
|**適用於**|**class**、 **struct**|
|**可重複**|否|
|**必要屬性**|**coclass**|
|**無效屬性**|None|

如需詳細資訊，請參閱 [屬性內容](cpp-attributes-com-net.md#contexts)。

## <a name="see-also"></a>另請參閱

[IDL 屬性](idl-attributes.md)<br/>
[類別屬性](class-attributes.md)
