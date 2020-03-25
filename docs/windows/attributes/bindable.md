---
title: 可系C++結（COM 屬性）
ms.date: 10/02/2018
f1_keywords:
- vc-attr.bindable
helpviewer_keywords:
- bindable attribute
ms.assetid: a2360f92-927b-4af8-98cc-6eca7f4ec954
ms.openlocfilehash: 9e476183374ad2a70864fd46aaa19c616cd3ce91
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80167351"
---
# <a name="bindable"></a>bindable

表示支援資料繫結的屬性。

## <a name="syntax"></a>語法

```cpp
[bindable]
```

## <a name="remarks"></a>備註

可系結C++屬性的功能與可系[結的](/windows/win32/Midl/bindable) **MIDL 屬性相同**。 您可以在使用[propget](propget.md)、 [propput](propput.md)或[propputref](propputref.md)屬性定義的屬性上使用它，或者您可以手動定義可系結的方法。

下列 MFC 範例示範如何使用可系**結：**

- [控制項範例：以 MFC 為基礎的 ActiveX 控制項](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/MFC/controls)

- [CIRC 範例： ActiveX 控制項](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/MFC/controls)

- [TESTHELP 範例：具有工具提示和說明的 ActiveX 控制項](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/MFC/controls)

## <a name="example"></a>範例

下列程式碼說明如何在**屬性上使用**可系結：

```cpp
// cpp_attr_ref_bindable.cpp
// compile with: /LD
#include <windows.h>
[
   uuid("479B29E3-9A2C-11D0-B696-00A0C903487A"), dispinterface, helpstring("property demo Interface")
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
|**必要屬性**|None|
|**無效屬性**|None|

如需有關屬性內容的詳細資訊，請參閱 [屬性內容](cpp-attributes-com-net.md#contexts)。

## <a name="see-also"></a>另請參閱

[IDL 屬性](idl-attributes.md)<br/>
[方法屬性](method-attributes.md)<br/>
[defaultbind](defaultbind.md)<br/>
[displaybind](displaybind.md)<br/>
[immediatebind](immediatebind.md)<br/>
[requestedit](requestedit.md)
