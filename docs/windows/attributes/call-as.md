---
title: call_as （c + + COM 屬性） |Microsoft Docs
ms.custom: ''
ms.date: 10/02/2018
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.call_as
dev_langs:
- C++
helpviewer_keywords:
- call_as attribute
ms.assetid: a09d7f1f-353b-4870-9b45-f0284161695d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 7ca6336a79b3e218e1e3a68112f1c12d7e4822a4
ms.sourcegitcommit: 955ef0f9d966e7c9c65e040f1e28fa83abe102a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/04/2018
ms.locfileid: "48790597"
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

**Call_as** c + + 屬性具有相同的功能[call_as](/windows/desktop/Midl/call-as) MIDL 屬性。

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
|**必要屬性**|無|
|**無效屬性**|無|

如需有關屬性內容的詳細資訊，請參閱 <<c0> [ 屬性內容](cpp-attributes-com-net.md#contexts)。

## <a name="see-also"></a>另請參閱

[IDL 屬性](idl-attributes.md)<br/>
[方法屬性](method-attributes.md)<br/>
[local](local-cpp.md)  