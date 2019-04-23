---
title: async_uuid (C++ COM 屬性)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.async_uuid
helpviewer_keywords:
- async_uuid attribute
ms.assetid: 235cb0d7-be58-4dd9-983c-e2a21bbc42c6
ms.openlocfilehash: 4c2bca9165d8b23f8cfa4f0f5523c882fd2f52bf
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59035792"
---
# <a name="asyncuuid"></a>async_uuid

指定會指示 MIDL 編譯器定義 COM 介面的同步和非同步版本的 UUID。

## <a name="syntax"></a>語法

```cpp
[async_uuid (uuid)]
```

### <a name="parameters"></a>參數

*uuid*<br/>
UUID 可識別介面的版本。

## <a name="remarks"></a>備註

**Async_uuid** C++屬性具有相同的功能[async_uuid](/windows/desktop/Midl/async-uuid) MIDL 屬性。

## <a name="example"></a>範例

```cpp
// cpp_attr_ref_async_uuid.cpp
// compile with: /LD
#include <Windows.h>
[module(name="Test")];
[object, uuid("9e66a290-4365-11d2-a997-00c04fa37ddb"),
async_uuid("e8583106-38fd-487e-912e-4fc8645c677e")]
__interface ICustom {
   HRESULT Custom([in] long l, [out, retval] long *pLong);
};
```

## <a name="requirements"></a>需求

### <a name="attribute-context"></a>屬性內容

|||
|-|-|
|**適用於**|`interface`|
|**可重複**|否|
|**必要屬性**|None|
|**無效屬性**|**雙重**， **dispinterface**|

如需有關屬性內容的詳細資訊，請參閱 [屬性內容](cpp-attributes-com-net.md#contexts)。

## <a name="see-also"></a>另請參閱

[IDL 屬性](idl-attributes.md)<br/>
[介面屬性](interface-attributes.md)