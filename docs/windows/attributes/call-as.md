---
title: call_as (C++ COM 屬性)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.call_as
helpviewer_keywords:
- call_as attribute
ms.assetid: a09d7f1f-353b-4870-9b45-f0284161695d
ms.openlocfilehash: a0051cdca6673800b37d5733c0b849da24010fcb
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59023915"
---
# <a name="callas"></a>call_as

可讓[本機](local-cpp.md)函式對應至遠端函式，以便遠端函式呼叫時，區域函式會叫用。

## <a name="syntax"></a>語法

```cpp
[ call_as(function) ]
```

### <a name="parameters"></a>參數

*function*<br/>
您想要遠端函式會叫用時呼叫區域函式。

## <a name="remarks"></a>備註

**Call_as** C++屬性具有相同的功能[call_as](/windows/desktop/Midl/call-as) MIDL 屬性。

## <a name="example"></a>範例

下列程式碼會示範如何使用**call_as**對應不可遠端處理函式 (`f1`) 可遠端處理函式 (`Remf1`):

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
[local](local-cpp.md)