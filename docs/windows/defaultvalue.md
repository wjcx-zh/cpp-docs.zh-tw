---
title: defaultvalue |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.defaultvalue
dev_langs:
- C++
helpviewer_keywords:
- defaultvalue attribute
ms.assetid: efa5d050-b2cc-4d9e-9b8e-79954f218d3a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 70be45d1a7221590912ea71b38d3aa4404197df1
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2018
ms.locfileid: "42599124"
---
# <a name="defaultvalue"></a>defaultvalue

允許指定的具類型的選擇性參數的預設值。

## <a name="syntax"></a>語法

```cpp
[ defaultvalue= value ]
```

### <a name="parameters"></a>參數

*值*  
參數的預設值。

## <a name="remarks"></a>備註

**Defaultvalue** c + + 屬性具有相同的功能[defaultvalue](http://msdn.microsoft.com/library/windows/desktop/aa366793) MIDL 屬性。

## <a name="example"></a>範例

下列程式碼會顯示介面的方法使用**defaultvalue**屬性：

```cpp
// cpp_attr_ref_defaultvalue.cpp
// compile with: /LD
#include <windows.h>

[export] typedef long HRESULT;
[export, ptr, string] typedef unsigned char * MY_STRING_TYPE;

[  uuid("479B29EE-9A2C-11D0-B696-00A0C903487A"),
   dual, oleautomation,
   helpstring("IFireTabCtrl Interface"),
   helpcontext(122), pointer_default(unique) ]

__interface IFireTabCtrl : IDispatch {
   [bindable, propget] HRESULT get_Size([out, retval, defaultvalue("33")] long *nSize);
   [bindable, propput] HRESULT put_Size([in] int nSize);
};

[ module(name="ATLFIRELib", uuid="479B29E1-9A2C-11D0-B696-00A0C903487A",
      version="1.0", helpstring="ATLFire 1.0 Type Library") ];
```

## <a name="requirements"></a>需求

### <a name="attribute-context"></a>屬性內容

|||
|-|-|
|**適用於**|介面參數|
|**可重複**|否|
|**必要屬性**|無|
|**無效屬性**|無|

如需詳細資訊，請參閱 [屬性內容](../windows/attribute-contexts.md)。

## <a name="see-also"></a>另請參閱

[IDL 屬性](../windows/idl-attributes.md)  
[參數屬性](../windows/parameter-attributes.md)  
[out](../windows/out-cpp.md)  
[retval](../windows/retval.md)  
[in](../windows/in-cpp.md)  
[pointer_default](../windows/pointer-default.md)  
[unique](../windows/unique-cpp.md)  