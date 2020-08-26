---
title: 'public (c + + 屬性)  (c + + COM 屬性) '
ms.date: 10/02/2018
f1_keywords:
- vc-attr.public
helpviewer_keywords:
- public attribute
ms.assetid: c42e1fd5-6cb1-48fe-8a03-95f2a2e0137c
ms.openlocfilehash: 6a19a9a2718ad5f0e7ac59c71e9b4df6a7e92dd2
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/25/2020
ms.locfileid: "88836903"
---
# <a name="public-c-attributes"></a>public (C++ 屬性)

確保 typedef 會進入類型程式庫，即使它不是從 .idl 檔中參考也一樣。

## <a name="syntax"></a>語法

```cpp
[public]
```

## <a name="remarks"></a>備註

**`public`** C + + 屬性具有與[公用](/windows/win32/Midl/public)MIDL 屬性相同的功能。

## <a name="example"></a>範例

下列程式碼說明如何使用 **`public`** 屬性：

```cpp
// cpp_attr_ref_public.cpp
// compile with: /LD
#include "unknwn.h"
[module(name="ATLFIRELib")];
[export, public] typedef long MEMBERID;

[dispinterface, uuid(99999999-9999-9999-9999-000000000000)]
__interface IFireTabCtrl : IDispatch
{
   [id(2)] long procedure ([in, optional] VARIANT i);
};
```

## <a name="requirements"></a>規格需求

| 屬性內容 | 值 |
|-|-|
|**適用於**|**`typedef`**|
|**重複**|否|
|**必要的屬性**|無|
|**無效屬性**|無|

如需有關屬性內容的詳細資訊，請參閱 [屬性內容](cpp-attributes-com-net.md#contexts)。

## <a name="see-also"></a>另請參閱

[IDL 屬性](idl-attributes.md)<br/>
[Typedef、Enum、Union 和 Struct 屬性](typedef-enum-union-and-struct-attributes.md)
