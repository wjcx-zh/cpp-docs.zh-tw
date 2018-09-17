---
title: 預設值 （c + +） |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.default
dev_langs:
- C++
helpviewer_keywords:
- default attribute
- attributes [C#], default attribute
- defaults, default attribute
ms.assetid: 0cdca716-1ba8-46d7-9399-167e55492870
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 6baefb7ef0af5054cb46ed4ad74b6a6bf80fbb61
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/17/2018
ms.locfileid: "45699917"
---
# <a name="default-c"></a>default (C++)

表示 coclass 內定義的自訂或 dispinterface，用以代表預設可程式性介面。

## <a name="syntax"></a>語法

```cpp
[ default(
   interface1,
   interface2
) ]
```

### <a name="parameters"></a>參數

*interface1*  
可讓指令碼環境使用的預設介面，會根據使用 **default** 屬性定義的類別來建立物件。

如果未指定預設介面，預設會使用第一個出現的非來源介面。

*介面 2*<br/>
（選擇性）預設來源介面。 您也必須使用 [source](../windows/source-cpp.md) 屬性來指定此介面。

如果未指定預設來源介面，預設會使用第一個來源介面。

## <a name="remarks"></a>備註

**預設**c + + 屬性具有相同的功能[預設](/windows/desktop/Midl/default)MIDL 屬性。 **default** 屬性也可搭配 [case](../windows/case-cpp.md) 屬性使用。

## <a name="example"></a>範例

下列程式碼示範如何**預設**coclass 的定義來指定`ICustomDispatch`為預設可程式性介面：

```cpp
// cpp_attr_ref_default.cpp
// compile with: /LD
#include "windows.h"
[module(name="MyLibrary")];

[object, uuid("9E66A290-4365-11D2-A997-00C04FA37DDB")]
__interface ICustom {
   HRESULT Custom([in] long l, [out, retval] long *pLong);
};

[dual, uuid("9E66A291-4365-11D2-A997-00C04FA37DDB")]
__interface IDual {
   HRESULT Dual([in] long l, [out, retval] long *pLong);
};

[object, uuid("9E66A293-4365-11D2-A997-00C04FA37DDB")]
__interface ICustomDispatch : public IDispatch {
   HRESULT Dispatch([in] long l, [out, retval] long *pLong);
};

[   coclass,
   default(ICustomDispatch),
   source(IDual),
   uuid("9E66A294-4365-11D2-A997-00C04FA37DDB")  
]
class CClass : public ICustom, public IDual, public ICustomDispatch {
   HRESULT Custom(long l, long *pLong) { return(S_OK); }
   HRESULT Dual(long l, long *pLong) { return(S_OK); }
   HRESULT Dispatch(long l, long *pLong) { return(S_OK); }
};

int main() {
#if 0 // Can't instantiate without implementations of IUnknown/IDispatch
   CClass *pClass = new CClass;

   long llong;

   pClass->custom(1, &llong);
   pClass->dual(1, &llong);
   pClass->dispinterface(1, &llong);
   pClass->dispatch(1, &llong);

   delete pClass;
#endif
   return(0);
}
```

[source](../windows/source-cpp.md) 屬性也會示範如何使用 **default**。

## <a name="requirements"></a>需求

### <a name="attribute-context"></a>屬性內容

|||
|-|-|
|**適用於**|**類別**， **struct**，資料成員|
|**可重複**|否|
|**必要屬性**|**coclass** (當套用至**類別**或是**結構**)|
|**無效屬性**|無|

如需詳細資訊，請參閱 [屬性內容](../windows/attribute-contexts.md)。

## <a name="see-also"></a>另請參閱

[IDL 屬性](../windows/idl-attributes.md)  
[類別屬性](../windows/class-attributes.md)  
[coclass](../windows/coclass.md)  