---
title: 'defaultvalue (c + + COM 屬性) '
ms.date: 10/02/2018
f1_keywords:
- vc-attr.defaultvalue
helpviewer_keywords:
- defaultvalue attribute
ms.assetid: efa5d050-b2cc-4d9e-9b8e-79954f218d3a
ms.openlocfilehash: 53b6a50bd7156eb9d6873e5ef08f6d75508fa3e1
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/25/2020
ms.locfileid: "88841684"
---
# <a name="defaultvalue"></a>defaultvalue

允許指定具類型選擇性參數的預設值。

## <a name="syntax"></a>語法

```cpp
[ defaultvalue= value ]
```

### <a name="parameters"></a>參數

*value*<br/>
參數的預設值。

## <a name="remarks"></a>備註

**Defaultvalue** c + + 屬性具有與[defaultvalue](/windows/win32/Midl/defaultvalue) MIDL 屬性相同的功能。

## <a name="example"></a>範例

下列程式碼顯示使用 **defaultvalue** 屬性的介面方法：

```cpp
// cpp_attr_ref_defaultvalue.cpp
// compile with: /LD
#include <windows.h>

[export] typedef long HRESULT;
[export, ptr, string] typedef unsigned char * MY_STRING_TYPE;

[  uuid("479B29EE-9A2C-11D0-B696-00A0C903487A"), dual, oleautomation, helpstring("IFireTabCtrl Interface"), helpcontext(122), pointer_default(unique) ]

__interface IFireTabCtrl : IDispatch {
   [bindable, propget] HRESULT get_Size([out, retval, defaultvalue("33")] long *nSize);
   [bindable, propput] HRESULT put_Size([in] int nSize);
};

[ module(name="ATLFIRELib", uuid="479B29E1-9A2C-11D0-B696-00A0C903487A",    version="1.0", helpstring="ATLFire 1.0 Type Library") ];
```

## <a name="requirements"></a>規格需求

| 屬性內容 | 值 |
|-|-|
|**適用於**|介面參數|
|**重複**|否|
|**必要的屬性**|無|
|**無效屬性**|無|

如需詳細資訊，請參閱 [屬性內容](cpp-attributes-com-net.md#contexts)。

## <a name="see-also"></a>另請參閱

[IDL 屬性](idl-attributes.md)<br/>
[參數屬性](parameter-attributes.md)<br/>
[擴展](out-cpp.md)<br/>
[retval](retval.md)<br/>
[in](in-cpp.md)<br/>
[pointer_default](pointer-default.md)<br/>
[unique](unique-cpp.md)
