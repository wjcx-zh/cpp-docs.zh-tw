---
title: 'odl (c + + COM 屬性) '
ms.date: 10/02/2018
f1_keywords:
- vc-attr.odl
helpviewer_keywords:
- odl attribute
ms.assetid: 75dcb314-b50f-4a63-9180-507ac1bc78f3
ms.openlocfilehash: a2f3c58e40dc14d256ca694bb1266aed13dc9620
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/25/2020
ms.locfileid: "88842815"
---
# <a name="odl"></a>odl

將介面識別為物件描述語言， (ODL) 介面。 MIDL 編譯器不需要 **odl** 屬性;它只會辨識為與較舊的 odl 檔案相容。

## <a name="syntax"></a>語法

```cpp
[odl]
```

## <a name="remarks"></a>備註

**Odl** c + + 屬性具有與[odl](/windows/win32/Midl/odl) MIDL 屬性相同的功能。

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

## <a name="requirements"></a>規格需求

| 屬性內容 | 值 |
|-|-|
|**適用於**|**interface**|
|**重複**|否|
|**必要的屬性**|無|
|**無效屬性**|無|

如需有關屬性內容的詳細資訊，請參閱 [屬性內容](cpp-attributes-com-net.md#contexts)。

## <a name="see-also"></a>另請參閱

[IDL 屬性](idl-attributes.md)<br/>
[介面屬性](interface-attributes.md)
