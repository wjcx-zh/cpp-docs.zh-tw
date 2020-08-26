---
title: 'helpstringdll (c + + COM 屬性) '
ms.date: 10/02/2018
f1_keywords:
- vc-attr.helpstringdll
helpviewer_keywords:
- helpstringdll attribute [C++]
ms.assetid: 121271fa-f061-492b-b87f-bbfcf4b02e7b
ms.openlocfilehash: 0c90a6a203189eff927819a3319fac6a8e9f6a55
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/25/2020
ms.locfileid: "88842841"
---
# <a name="helpstringdll"></a>helpstringdll

指定要用來執行檔字串查閱 (當地語系化) 的 DLL 名稱。

## <a name="syntax"></a>語法

```cpp
[ helpstringdll("string") ]
```

### <a name="parameters"></a>參數

*string*<br/>
用來執行檔字串查閱的 DLL。

## <a name="remarks"></a>備註

**Helpstringdll** c + + 屬性具有與[helpstringdll](/windows/win32/Midl/helpstringdll) MIDL 屬性相同的功能。

## <a name="example"></a>範例

```cpp
// cpp_attr_ref_helpstringdll.cpp
// compile with: /LD
#include <unknwn.h>
[module(name="MyLib", helpstringdll="xx.dll")];

[object, uuid("00000000-0000-0000-0000-000000000001")]
__interface IMyI
{
   HRESULT xxx();
};
```

## <a name="requirements"></a>規格需求

| 屬性內容 | 值 |
|-|-|
|**適用於**|**`class`**、 **介面**、介面方法|
|**重複**|否|
|**必要的屬性**|無|
|**無效屬性**|無|

如需詳細資訊，請參閱 [屬性內容](cpp-attributes-com-net.md#contexts)。

## <a name="see-also"></a>另請參閱

[IDL 屬性](idl-attributes.md)<br/>
[介面屬性](interface-attributes.md)<br/>
[類別屬性](class-attributes.md)<br/>
[方法屬性](method-attributes.md)
