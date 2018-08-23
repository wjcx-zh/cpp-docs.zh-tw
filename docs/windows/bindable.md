---
title: 可繫結 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.bindable
dev_langs:
- C++
helpviewer_keywords:
- bindable attribute
ms.assetid: a2360f92-927b-4af8-98cc-6eca7f4ec954
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 4c529abb1ade786bf7ec0a2d5cff5c49f6197be7
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2018
ms.locfileid: "42601585"
---
# <a name="bindable"></a>bindable

表示支援資料繫結的屬性。

## <a name="syntax"></a>語法

```cpp
[bindable]
```

## <a name="remarks"></a>備註

**可繫結**c + + 屬性具有相同的功能[可繫結](http://msdn.microsoft.com/library/windows/desktop/aa366738)MIDL 屬性。 您可以利用定義的屬性上使用它[propget](../windows/propget.md)， [propput](../windows/propput.md)，或[propputref](../windows/propputref.md)屬性，或者您可以手動定義的可繫結的方法。

下列的 MFC 範例示範如何使用**可繫結**:

- [控制項的範例： MFC 為基礎的 ActiveX 控制項](http://msdn.microsoft.com/a44adf86-0ba0-4504-bedb-512b6cba2e63)

- [CIRC 範例： ActiveX 控制項](http://msdn.microsoft.com/9ba34d04-280e-49f4-90ae-41a6be44c95b)

- [工具提示與說明 TESTHELP 範例： ActiveX 控制項](http://msdn.microsoft.com/d822861d-c6f0-4d0a-ad11-970eebb1e8cd)

## <a name="example"></a>範例

下列程式碼會示範如何使用**可繫結**屬性：

```cpp
// cpp_attr_ref_bindable.cpp
// compile with: /LD
#include <windows.h>
[
   uuid("479B29E3-9A2C-11D0-B696-00A0C903487A"),
   dispinterface,
   helpstring("property demo Interface")  
]
__interface IPropDemo : IDispatch {

   [propget, id(1), bindable, displaybind, defaultbind, requestedit] HRESULT P1([out, retval] long *nSize);
   [propput, id(1), bindable, displaybind, defaultbind, requestedit] HRESULT P1([in] long nSize);
   [id(3), bindable, propget] HRESULT Object([out, retval] IDispatch **ppObj);
   [id(3), bindable, propputref] HRESULT Object([in] IDispatch* pObj);
   [id(-552), helpstring("method AboutBox")] HRESULT AboutBox();
};

[ module(name="PropDemoLib", uuid="479B29E2-9A2C-11D0-B696-00A0C903487A", version="1.0", helpstring="property demo") ];
```

## <a name="requirements"></a>需求

### <a name="attribute-context"></a>屬性內容

|||
|-|-|
|**適用於**|介面方法|
|**可重複**|否|
|**必要屬性**|無|
|**無效屬性**|無|

如需有關屬性內容的詳細資訊，請參閱 [屬性內容](../windows/attribute-contexts.md)。

## <a name="see-also"></a>另請參閱

[IDL 屬性](../windows/idl-attributes.md)  
[方法屬性](../windows/method-attributes.md)  
[defaultbind](../windows/defaultbind.md)  
[displaybind](../windows/displaybind.md)  
[immediatebind](../windows/immediatebind.md)  
[requestedit](../windows/requestedit.md)  