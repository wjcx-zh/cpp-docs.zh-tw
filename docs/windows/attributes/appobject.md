---
title: appobject （C++ COM 屬性）
ms.date: 10/02/2018
f1_keywords:
- vc-attr.appobject
helpviewer_keywords:
- appobject attribute
ms.assetid: 8ce30b73-e945-403e-a755-6bc78078a695
ms.openlocfilehash: ebbb3ce71dc9b947ef49a42ee41a5ce2d5abbb34
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80168508"
---
# <a name="appobject"></a>appobject

將 coclass 識別為與完整 .exe 應用程式相關聯的應用程式物件，並指出 coclass 的函式和屬性在此[類型程式庫](../../mfc/automation-clients-using-type-libraries.md)中可全域使用。

## <a name="syntax"></a>語法

```cpp
[appobject]
```

## <a name="remarks"></a>備註

**Appobject** C++屬性具有與[appobject](/windows/win32/Midl/appobject) MIDL 屬性相同的功能。

## <a name="example"></a>範例

下列程式碼顯示一個簡單的類別定義，前面加上包含**appobject**的屬性區塊：

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

## <a name="requirements"></a>需求

### <a name="attribute-context"></a>屬性內容

|||
|-|-|
|**適用於**|**class**、 **struct**|
|**可重複**|否|
|**必要屬性**|`coclass`|
|**無效屬性**|None|

如需有關屬性內容的詳細資訊，請參閱 [屬性內容](cpp-attributes-com-net.md#contexts)。

## <a name="see-also"></a>另請參閱

[IDL 屬性](idl-attributes.md)<br/>
[類別屬性](class-attributes.md)<br/>
[Typedef、Enum、Union 和 Struct 屬性](typedef-enum-union-and-struct-attributes.md)
