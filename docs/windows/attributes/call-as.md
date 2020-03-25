---
title: call_as （C++ COM 屬性）
ms.date: 10/02/2018
f1_keywords:
- vc-attr.call_as
helpviewer_keywords:
- call_as attribute
ms.assetid: a09d7f1f-353b-4870-9b45-f0284161695d
ms.openlocfilehash: 755741faec6c0ba702d372ca8dee486edcb72ef3
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80167327"
---
# <a name="call_as"></a>call_as

讓[區域](local-cpp.md)函式能夠對應至遠端函式，以便在呼叫遠端函式時叫用區域函式。

## <a name="syntax"></a>語法

```cpp
[ call_as(function) ]
```

### <a name="parameters"></a>參數

*函數*<br/>
您想要在叫用遠端函數時呼叫的區域函式。

## <a name="remarks"></a>備註

**Call_as** C++屬性具有與[call_as](/windows/win32/Midl/call-as) MIDL 屬性相同的功能。

## <a name="example"></a>範例

下列程式碼示範如何使用**call_as**將不可遠端處理函式（`f1`）對應到可遠端處理的函式（`Remf1`）：

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
