---
title: 'appobject (c + + COM 屬性) '
ms.date: 10/02/2018
f1_keywords:
- vc-attr.appobject
helpviewer_keywords:
- appobject attribute
ms.assetid: 8ce30b73-e945-403e-a755-6bc78078a695
ms.openlocfilehash: 6562702a93273e4fc24ba138a1eb20b1ab6b076e
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/25/2020
ms.locfileid: "88836344"
---
# <a name="appobject"></a>appobject

將 coclass 識別為與完整 .exe 應用程式相關聯的應用程式物件，並指出 coclass 的函式和屬性在此 [類型程式庫](../../mfc/automation-clients-using-type-libraries.md)中為全域可用。

## <a name="syntax"></a>語法

```cpp
[appobject]
```

## <a name="remarks"></a>備註

**Appobject** c + + 屬性具有與[appobject](/windows/win32/Midl/appobject) MIDL 屬性相同的功能。

## <a name="example"></a>範例

下列程式碼顯示一個簡單的類別定義，其前面會有包含 **appobject**的屬性區塊：

```cpp
// cpp_attr_ref_appobject.cpp
// compile with: /LD
#include <windows.h>
[module(name="MyLib", uuid="f1ce17f0-a5df-4d26-95f6-0a122197ac5b")];

[object, uuid="905de6db-7a12-45ab-9f8b-b39f5112f010"]
__interface ICustom {};

[coclass, appobject,uuid="00395340-745f-4b69-bd58-e2921452b9fc"]
class A : public ICustom {
   int i;
};
```

## <a name="requirements"></a>規格需求

| 屬性內容 | 值 |
|-|-|
|**適用於**|**`class`**, **`struct`**|
|**重複**|否|
|**必要的屬性**|`coclass`|
|**無效屬性**|無|

如需有關屬性內容的詳細資訊，請參閱 [屬性內容](cpp-attributes-com-net.md#contexts)。

## <a name="see-also"></a>另請參閱

[IDL 屬性](idl-attributes.md)<br/>
[類別屬性](class-attributes.md)<br/>
[Typedef、Enum、Union 和 Struct 屬性](typedef-enum-union-and-struct-attributes.md)
