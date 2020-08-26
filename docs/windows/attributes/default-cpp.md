---
title: '預設 (c + + COM 屬性) '
ms.date: 10/02/2018
f1_keywords:
- vc-attr.default
helpviewer_keywords:
- default attribute
- attributes [C#], default attribute
- defaults, default attribute
ms.assetid: 0cdca716-1ba8-46d7-9399-167e55492870
ms.openlocfilehash: b53420d721b43f9a51b19c4cc8e4a83fc8b94ed4
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/25/2020
ms.locfileid: "88842438"
---
# <a name="default-c"></a>default (C++)

表示 coclass 內定義的自訂或 dispinterface，用以代表預設可程式性介面。

## <a name="syntax"></a>語法

```cpp
[ default(interface1, interface2) ]
```

### <a name="parameters"></a>參數

*interface1*<br/>
將提供給腳本環境使用的預設介面，會根據以屬性定義的類別來建立物件 **`default`** 。

如果未指定預設介面，預設會使用第一個出現的非來源介面。

*interface2*<br/>
 (選擇性) 預設來源介面。 您也必須使用 [source](source-cpp.md) 屬性來指定此介面。

如果未指定預設來源介面，預設會使用第一個來源介面。

## <a name="remarks"></a>備註

**`default`** C + + 屬性具有與[預設](/windows/win32/Midl/default)MIDL 屬性相同的功能。 **`default`** 屬性也會與[case](case-cpp.md)屬性搭配使用。

## <a name="example"></a>範例

下列程式碼示範如何 **`default`** 在 coclass 的定義上使用，以指定 `ICustomDispatch` 為預設的可程式性介面：

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

[Source](source-cpp.md)屬性也有如何使用的範例 **`default`** 。

## <a name="requirements"></a>規格需求

| 屬性內容 | 值 |
|-|-|
|**適用於**|**`class`**、 **`struct`** 、資料成員|
|**重複**|否|
|**必要的屬性**|**coclass**套用至 **`class`** 或) 的 coclass **`struct`** (|
|**無效屬性**|無|

如需詳細資訊，請參閱 [屬性內容](cpp-attributes-com-net.md#contexts)。

## <a name="see-also"></a>另請參閱

[IDL 屬性](idl-attributes.md)<br/>
[類別屬性](class-attributes.md)<br/>
[coclass](coclass.md)
