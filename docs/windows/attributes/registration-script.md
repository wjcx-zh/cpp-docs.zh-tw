---
title: 'registration_script (c + + COM 屬性) '
ms.date: 10/02/2018
f1_keywords:
- vc-attr.registration_script
helpviewer_keywords:
- registration_script attribute
ms.assetid: 786f8072-9187-4163-a979-7a604dd4c888
ms.openlocfilehash: 8a57f0b3d0925d1e1096a31734fa4c9d666c5743
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/25/2020
ms.locfileid: "88846078"
---
# <a name="registration_script"></a>registration_script

執行指定的自訂註冊腳本。

## <a name="syntax"></a>語法

```cpp
[ registration_script(script) ]
```

### <a name="parameters"></a>參數

*指令碼*<br/>
自訂註冊腳本的完整路徑， ( .rgs) 檔。 值為 **none**（例如 `script = "none"` ）表示 coclass 沒有註冊需求。

## <a name="remarks"></a>備註

**Registration_script** c + + 屬性會執行*腳本*所指定的自訂註冊腳本。 如果未指定此屬性，則會使用標準的 .rgs 檔 (包含註冊元件) 的資訊。 如需 .rgs 檔案的詳細資訊，請參閱 [ (註冊機構) 的 ATL 登錄元件 ](../../atl/atl-registry-component-registrar.md)。

此屬性需要 [coclass](coclass.md)、 [progid](progid.md)或 [vi_progid](vi-progid.md) 屬性 (或表示上述其中一項的另一個屬性) 也套用至相同的項目。

## <a name="example"></a>範例

下列程式碼指定元件具有稱為 cpp_attr_ref_registration_script 的登入指令檔。

```cpp
// cpp_attr_ref_registration_script.cpp
// compile with: /LD
#define _ATL_ATTRIBUTES
#include "atlbase.h"
#include "atlcom.h"

[module (name="REG")];

[object, uuid("d9cd196b-6836-470b-9b9b-5b04b828e5b0")]
__interface IFace {};

// requires "cpp_attr_ref_registration_script.rgs"
// create sample .RGS file "cpp_attr_ref_registration_script.rgs" if it does not exist
[ coclass, registration_script(script="cpp_attr_ref_registration_script.rgs"),
  uuid("50d3ad42-3601-4f26-8cfe-0f1f26f98f67")]
class CMyClass:public IFace {};
```

## <a name="requirements"></a>規格需求

| 屬性內容 | 值 |
|-|-|
|**適用於**|**`class`**, **`struct`**|
|**重複**|否|
|**必要的屬性**|下列其中一項或多項： `coclass` 、 `progid` 或 `vi_progid` 。|
|**無效屬性**|無|

如需有關屬性內容的詳細資訊，請參閱 [屬性內容](cpp-attributes-com-net.md#contexts)。

## <a name="see-also"></a>另請參閱

[COM 屬性](com-attributes.md)<br/>
[類別屬性](class-attributes.md)<br/>
[rdx](rdx.md)
