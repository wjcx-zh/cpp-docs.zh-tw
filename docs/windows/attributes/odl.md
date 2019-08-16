---
title: odl (C++ COM 屬性)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.odl
helpviewer_keywords:
- odl attribute
ms.assetid: 75dcb314-b50f-4a63-9180-507ac1bc78f3
ms.openlocfilehash: a4ae1aa7f27348e37c565b35e3dc0b2b1011c9cb
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/15/2019
ms.locfileid: "69514312"
---
# <a name="odl"></a>odl

將介面識別為物件描述語言 (ODL) 介面。 MIDL 編譯器不需要**odl**屬性。它僅能與較舊的 odl 檔案相容。

## <a name="syntax"></a>語法

```cpp
[odl]
```

## <a name="remarks"></a>備註

**Odl** C++屬性具有與[odl](/windows/win32/Midl/odl) MIDL 屬性相同的功能。

## <a name="example"></a>範例

```cpp
// cpp_attr_ref_odl.cpp
// compile with: /LD
#include <unknwn.h>
[module(name="MyLIb")];

[odl, oleautomation, dual, uuid("00000000-0000-0000-0000-000000000001")]
__interface IMyInterface
{
   HRESULT x();
};

[coclass, uuid("00000000-0000-0000-0000-000000000002")]
class cmyClass : public IMyInterface
{
public:
   HRESULT x(){}
};
```

## <a name="requirements"></a>需求

### <a name="attribute-context"></a>屬性內容

|||
|-|-|
|**適用於**|**interface**|
|**可重複**|否|
|**必要屬性**|無|
|**無效屬性**|無|

如需有關屬性內容的詳細資訊，請參閱 [屬性內容](cpp-attributes-com-net.md#contexts)。

## <a name="see-also"></a>另請參閱

[IDL 屬性](idl-attributes.md)<br/>
[介面屬性](interface-attributes.md)