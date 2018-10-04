---
title: 預設值 （c + + COM 屬性） |Microsoft Docs
ms.custom: ''
ms.date: 10/02/2018
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
ms.openlocfilehash: 5fb7f205ccdf78e1ef64e2ba2c132e3c2b6b6000
ms.sourcegitcommit: 955ef0f9d966e7c9c65e040f1e28fa83abe102a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/04/2018
ms.locfileid: "48791002"
---
# <a name="default-c"></a>default (C++)

表示 coclass 內定義的自訂或 dispinterface，用以代表預設可程式性介面。

## <a name="syntax"></a>語法

```cpp
[ default(interface1, interface2) ]
```

### <a name="parameters"></a>參數

*interface1*<br/>
可讓指令碼環境使用的預設介面，會根據使用 **default** 屬性定義的類別來建立物件。

如果未指定預設介面，預設會使用第一個出現的非來源介面。

*介面 2*<br/>
（選擇性）預設來源介面。 您也必須指定此介面與[來源](source-cpp.md)屬性。

如果未指定預設來源介面，預設會使用第一個來源介面。

## <a name="remarks"></a>備註

**預設**c + + 屬性具有相同的功能[預設](/windows/desktop/Midl/default)MIDL 屬性。 **預設**屬性也可搭配[案例](case-cpp.md)屬性。

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

[   coclass, default(ICustomDispatch), source(IDual), uuid("9E66A294-4365-11D2-A997-00C04FA37DDB")  
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

[來源](source-cpp.md)屬性還會有的使用方式範例**預設**。

## <a name="requirements"></a>需求

### <a name="attribute-context"></a>屬性內容

|||
|-|-|
|**適用於**|**類別**， **struct**，資料成員|
|**可重複**|否|
|**必要屬性**|**coclass** (當套用至**類別**或是**結構**)|
|**無效屬性**|無|

如需詳細資訊，請參閱 <<c0> [ 屬性內容](cpp-attributes-com-net.md#contexts)。

## <a name="see-also"></a>另請參閱

[IDL 屬性](idl-attributes.md)<br/>
[類別屬性](class-attributes.md)<br/>
[coclass](coclass.md)  