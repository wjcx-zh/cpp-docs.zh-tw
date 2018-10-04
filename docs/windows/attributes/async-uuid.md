---
title: async_uuid （c + + COM 屬性） |Microsoft Docs
ms.custom: ''
ms.date: 10/02/2018
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.async_uuid
dev_langs:
- C++
helpviewer_keywords:
- async_uuid attribute
ms.assetid: 235cb0d7-be58-4dd9-983c-e2a21bbc42c6
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 336bbf00edc84335972171aba0e7fc01e206984e
ms.sourcegitcommit: 955ef0f9d966e7c9c65e040f1e28fa83abe102a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/04/2018
ms.locfileid: "48790703"
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

**Async_uuid** c + + 屬性具有相同的功能[async_uuid](/windows/desktop/Midl/async-uuid) MIDL 屬性。

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
|**必要屬性**|無|
|**無效屬性**|**雙重**， **dispinterface**|

如需有關屬性內容的詳細資訊，請參閱 <<c0> [ 屬性內容](cpp-attributes-com-net.md#contexts)。

## <a name="see-also"></a>另請參閱

[IDL 屬性](idl-attributes.md)<br/>
[介面屬性](interface-attributes.md)  