---
title: registration_script （c + + COM 屬性） |Microsoft Docs
ms.custom: ''
ms.date: 10/02/2018
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.registration_script
dev_langs:
- C++
helpviewer_keywords:
- registration_script attribute
ms.assetid: 786f8072-9187-4163-a979-7a604dd4c888
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: edc9d5aa1d7c49de34ee3dbb02d2a55542962a50
ms.sourcegitcommit: 955ef0f9d966e7c9c65e040f1e28fa83abe102a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/04/2018
ms.locfileid: "48790935"
---
# <a name="registrationscript"></a>registration_script

執行指定的自訂註冊指令碼。

## <a name="syntax"></a>語法

```cpp
[ registration_script(script) ]
```

### <a name="parameters"></a>參數

*指令碼*<br/>
自訂註冊指令碼 (.rgs) 檔案的完整路徑。 值為**無**，例如`script = "none"`，指出 coclass 有沒有註冊需求。

## <a name="remarks"></a>備註

**Registration_script** c + + 屬性執行所指定的自訂註冊指令碼*指令碼*。 如果未指定此屬性，則會使用標準的.rgs 檔案 （包含註冊元件的資訊）。 如需有關.rgs 檔案的詳細資訊，請參閱[ATL 登錄元件 （登錄器）](../../atl/atl-registry-component-registrar.md)。

此屬性需要[coclass](coclass.md)， [progid](progid.md)，或[vi_progid](vi-progid.md)屬性 （或其中一種表示另一個屬性） 也套用至相同的項目。

## <a name="example"></a>範例

下列程式碼會指定此元件可稱為 cpp_attr_ref_registration_script.rgs 登錄指令碼。

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
|**適用於**|**類別**，**結構**|
|**可重複**|否|
|**必要屬性**|一或多個項目： `coclass`， `progid`，或`vi_progid`。|
|**無效屬性**|無|

如需有關屬性內容的詳細資訊，請參閱 <<c0> [ 屬性內容](cpp-attributes-com-net.md#contexts)。

## <a name="see-also"></a>另請參閱

[COM 屬性](com-attributes.md)<br/>
[類別屬性](class-attributes.md)<br/>
[rdx](rdx.md)  