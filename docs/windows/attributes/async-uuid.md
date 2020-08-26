---
title: 'async_uuid (c + + COM 屬性) '
ms.date: 10/02/2018
f1_keywords:
- vc-attr.async_uuid
helpviewer_keywords:
- async_uuid attribute
ms.assetid: 235cb0d7-be58-4dd9-983c-e2a21bbc42c6
ms.openlocfilehash: cb0abdcedc26c5ffe197e52d5da4fbad1ec516d2
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/25/2020
ms.locfileid: "88836240"
---
# <a name="async_uuid"></a>async_uuid

指定會指示 MIDL 編譯器定義 COM 介面之同步和非同步版本的 UUID。

## <a name="syntax"></a>語法

```cpp
[async_uuid (uuid)]
```

### <a name="parameters"></a>參數

*uuid*<br/>
識別介面版本的 UUID。

## <a name="remarks"></a>備註

**Async_uuid** c + + 屬性具有與[async_uuid](/windows/win32/Midl/async-uuid) MIDL 屬性相同的功能。

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

## <a name="requirements"></a>規格需求

| 屬性內容 | 值 |
|-|-|
|**適用於**|`interface`|
|**重複**|否|
|**必要的屬性**|無|
|**無效屬性**|**雙重**、分配 **介面**|

如需有關屬性內容的詳細資訊，請參閱 [屬性內容](cpp-attributes-com-net.md#contexts)。

## <a name="see-also"></a>另請參閱

[IDL 屬性](idl-attributes.md)<br/>
[介面屬性](interface-attributes.md)
