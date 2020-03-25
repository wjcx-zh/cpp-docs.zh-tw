---
title: registration_script （C++ COM 屬性）
ms.date: 10/02/2018
f1_keywords:
- vc-attr.registration_script
helpviewer_keywords:
- registration_script attribute
ms.assetid: 786f8072-9187-4163-a979-7a604dd4c888
ms.openlocfilehash: 780f3d41676d01458f47542d6f0862a278edff6a
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80214574"
---
# <a name="registration_script"></a>registration_script

執行指定的自訂註冊腳本。

## <a name="syntax"></a>語法

```cpp
[ registration_script(script) ]
```

### <a name="parameters"></a>參數

*文字*<br/>
自訂註冊腳本（.rgs）檔案的完整路徑。 值為 [**無**] （例如 `script = "none"`）表示 coclass 沒有註冊需求。

## <a name="remarks"></a>備註

**Registration_script** C++屬性會執行*腳本*所指定的自訂註冊腳本。 如果未指定這個屬性，則會使用標準的 .rgs 檔案（包含註冊元件的資訊）。 如需 .rgs 檔案的詳細資訊，請參閱[ATL 登錄元件（註冊機構）](../../atl/atl-registry-component-registrar.md)。

此屬性需要 [coclass](coclass.md)、 [progid](progid.md)或 [vi_progid](vi-progid.md) 屬性 (或表示上述其中一項的另一個屬性) 也套用至相同的項目。

## <a name="example"></a>範例

下列程式碼指定元件具有名為 cpp_attr_ref_registration_script 的登入指令檔。

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

## <a name="requirements"></a>需求

### <a name="attribute-context"></a>屬性內容

|||
|-|-|
|**適用於**|**class**、 **struct**|
|**可重複**|否|
|**必要屬性**|下列一或多項： `coclass`、`progid`或 `vi_progid`。|
|**無效屬性**|None|

如需有關屬性內容的詳細資訊，請參閱 [屬性內容](cpp-attributes-com-net.md#contexts)。

## <a name="see-also"></a>另請參閱

[COM 屬性](com-attributes.md)<br/>
[類別屬性](class-attributes.md)<br/>
[rdx](rdx.md)
