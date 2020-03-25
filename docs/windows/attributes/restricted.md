---
title: 受限制C++ （COM 屬性）
ms.date: 10/03/2018
f1_keywords:
- vc-attr.restricted
helpviewer_keywords:
- restricted attribute
ms.assetid: 504a96be-b904-4269-8be1-920feba201b4
ms.openlocfilehash: a47c56673e19f891b24ff433b9c614804f0bd51c
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80166363"
---
# <a name="restricted"></a>restricted

指定不能任意呼叫模組、介面或分配介面的成員。

## <a name="syntax"></a>語法

```cpp
[ restricted(
   interfaces
) ]
```

### <a name="parameters"></a>參數

*介面*<br/>
在 COM 物件上可能不會任意呼叫的一個或多個介面。 這個參數只有在套用至類別時才有效。

## <a name="remarks"></a>備註

**受限制** C++的屬性與[限制](/windows/win32/Midl/restricted)的 MIDL 屬性具有相同的功能。

## <a name="example"></a>範例

下列程式碼顯示如何使用**受限制**的屬性：

```cpp
// cpp_attr_ref_restricted.cpp
// compile with: /LD
#include "windows.h"
#include "unknwn.h"
[module(name="MyLib")];

[object, uuid("00000000-0000-0000-0000-000000000001")]
__interface a
{
};

[object, uuid("00000000-0000-0000-0000-000000000002")]
__interface b
{
};

[coclass, restricted(a,b), uuid("00000000-0000-0000-0000-000000000003")]
class c : public a, public b
{
};
```

## <a name="requirements"></a>需求

### <a name="attribute-context"></a>屬性內容

|||
|-|-|
|**適用於**|介面方法、**介面**、**類別**、**結構**|
|**可重複**|否|
|**必要屬性**|**coclass** （套用至**類別**或**結構**時）|
|**無效屬性**|None|

如需有關屬性內容的詳細資訊，請參閱 [屬性內容](cpp-attributes-com-net.md#contexts)。

## <a name="see-also"></a>另請參閱

[IDL 屬性](idl-attributes.md)<br/>
[介面屬性](interface-attributes.md)<br/>
[方法屬性](method-attributes.md)
