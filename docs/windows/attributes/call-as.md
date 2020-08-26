---
title: 'call_as (c + + COM 屬性) '
ms.date: 10/02/2018
f1_keywords:
- vc-attr.call_as
helpviewer_keywords:
- call_as attribute
ms.assetid: a09d7f1f-353b-4870-9b45-f0284161695d
ms.openlocfilehash: 9ae620ed6f2b01cc52e4a9c76217f044db925f11
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/25/2020
ms.locfileid: "88838916"
---
# <a name="call_as"></a>call_as

讓 [區域](local-cpp.md) 函式對應至遠端函式，以便在呼叫遠端函式時叫用區域函數。

## <a name="syntax"></a>語法

```cpp
[ call_as(function) ]
```

### <a name="parameters"></a>參數

*函數*<br/>
當叫用遠端函式時，您想要呼叫的區域函式。

## <a name="remarks"></a>備註

**Call_as** c + + 屬性具有與[call_as](/windows/win32/Midl/call-as) MIDL 屬性相同的功能。

## <a name="example"></a>範例

下列程式碼示範如何使用 **call_as** 將不可遠端處理函式 () 對應到可遠端處理的函式 `f1` (`Remf1`) ：

```cpp
// cpp_attr_ref_call_as.cpp
// compile with: /LD
#include "unknwn.h"
[module(name="MyLib")];
[dual, uuid("00000000-0000-0000-0000-000000000001")]
__interface IMInterface {
   [local] HRESULT f1 ( int i );
   [call_as(f1)] HRESULT Remf1 ( int i );
};
```

## <a name="requirements"></a>規格需求

| 屬性內容 | 值 |
|-|-|
|**適用於**|介面方法|
|**重複**|否|
|**必要的屬性**|無|
|**無效屬性**|無|

如需有關屬性內容的詳細資訊，請參閱 [屬性內容](cpp-attributes-com-net.md#contexts)。

## <a name="see-also"></a>另請參閱

[IDL 屬性](idl-attributes.md)<br/>
[方法屬性](method-attributes.md)<br/>
[當地](local-cpp.md)
