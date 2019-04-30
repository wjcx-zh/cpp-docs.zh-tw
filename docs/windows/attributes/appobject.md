---
title: appobject (C++ COM 屬性)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.appobject
helpviewer_keywords:
- appobject attribute
ms.assetid: 8ce30b73-e945-403e-a755-6bc78078a695
ms.openlocfilehash: 8219c8fdd1b1df93f92fc6c1d0324a2475d3384b
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62409703"
---
# <a name="appobject"></a>appobject

識別做為應用程式物件，這是完整的.exe 應用程式相關聯，表示全域可用在此函式和屬性的 coclass coclass[型別程式庫](../../mfc/automation-clients-using-type-libraries.md)。

## <a name="syntax"></a>語法

```cpp
[appobject]
```

## <a name="remarks"></a>備註

**Appobject** C++屬性具有相同的功能[appobject](/windows/desktop/Midl/appobject) MIDL 屬性。

## <a name="example"></a>範例

下列程式碼示範簡單的類別定義，加上包含的屬性區塊**appobject**:

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
|**適用於**|**類別**，**結構**|
|**可重複**|否|
|**必要屬性**|`coclass`|
|**無效屬性**|None|

如需有關屬性內容的詳細資訊，請參閱 [屬性內容](cpp-attributes-com-net.md#contexts)。

## <a name="see-also"></a>另請參閱

[IDL 屬性](idl-attributes.md)<br/>
[類別屬性](class-attributes.md)<br/>
[Typedef、Enum、Union 和 Struct 屬性](typedef-enum-union-and-struct-attributes.md)