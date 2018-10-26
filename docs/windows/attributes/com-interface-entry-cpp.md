---
title: com_interface_entry （c + + COM 屬性） |Microsoft Docs
ms.custom: ''
ms.date: 10/02/2018
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.com_interface_entry
dev_langs:
- C++
helpviewer_keywords:
- com_interface_entry attribute
ms.assetid: 10368f81-b99b-4a0f-ba4f-a142e6911a5c
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 6ccd3277b5ad627c6956e6f5620ee6aed1640cc5
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/25/2018
ms.locfileid: "50074003"
---
# <a name="cominterfaceentry-c"></a>com_interface_entry (C++)

新增到 COM 對應目標類別的介面項目。

## <a name="syntax"></a>語法

```cpp
[ com_interface_entry(
  com_interface_entry) ]
```

### <a name="parameters"></a>參數

*com_interface_entry*<br/>
字串，包含項目的實際的文字。 如需可能值的清單，請參閱 < [COM_INTERFACE_ENTRY 巨集](../../atl/reference/com-interface-entry-macros.md)。

## <a name="remarks"></a>備註

**Com_interface_entry** c + + 屬性會插入目標物件的 COM 介面對應中的字元字串的完整的內容。 如果屬性套用至目標物件的一次，則會將項目插入到現有的介面對應的開頭。 屬性重複套用至相同的目標物件，如果他們收到的順序中的介面對應的開頭插入項目。

此屬性需要 [coclass](coclass.md)、 [progid](progid.md)或 [vi_progid](vi-progid.md) 屬性 (或表示上述其中一項的另一個屬性) 也套用至相同的項目。 如果使用任何單一屬性，則會自動套用其他兩項。 例如，如果`progid`會套用`vi_progid`和`coclass`也會套用。

因為第一個的使用方式**com_interface_entry**會將新的介面的介面對應中，開頭插入它必須是下列一種 COM_INTERFACE_ENTRY 類型：

- COM_INTERFACE_ENTRY

- COM_INTERFACE_ENTRY_IID

- COM_INTERFACE_ENTRY2

- COM_INTERFACE_ENTRY2_IID

其他使用方式**com_interface_entry**屬性可以使用所有支援的 COM_INTERFACE_ENTRY 類型。

這項限制是必要的因為 ATL 介面對應中使用的第一個項目，做為識別`IUnknown`; 因此，項目必須是有效的介面。 例如，下列程式碼範例無效，因為在介面對應中的第一個項目不會指定實際的 COM 介面。

```cpp
[ coclass, com_interface_entry =
    "COM_INTERFACE_ENTRY_NOINTERFACE(IDebugTest)"
]
   class CMyClass
   {
   };
```

## <a name="example"></a>範例

下列程式碼會將兩個項目加入至現有的 COM 介面對應的`CMyBaseClass`。 第一個是標準的介面，和第二個隱藏`IDebugTest`介面。

```cpp
// cpp_attr_ref_com_interface_entry.cpp
// compile with: /LD
#define _ATL_ATTRIBUTES
#include "atlbase.h"
#include "atlcom.h"

[module (name ="ldld")];

[ object,
  uuid("7dbebed3-d636-4917-af62-c767a720a5b9")]
__interface IDebugTest{};

[ object,
  uuid("2875ceac-f94b-4087-8e13-d13dc167fcfc")]
__interface IMyClass{};

[ coclass,
  com_interface_entry ("COM_INTERFACE_ENTRY (IMyClass)"),
  com_interface_entry ("COM_INTERFACE_ENTRY_NOINTERFACE(IDebugTest)"),
  uuid("b85f8626-e76e-4775-b6a0-4826a9e94af2")
]

class CMyClass: public IMyClass, public IDebugTest
{
};
```

產生的 COM 物件對應的`CMyBaseClass`如下所示：

```cpp
BEGIN_COM_MAP(CMyClass)
    COM_INTERFACE_ENTRY (IMyClass)
    COM_INTERFACE_ENTRY_NOINTERFACE(IDebugTest)
    COM_INTERFACE_ENTRY(IMyClass)
    COM_INTERFACE_ENTRY2(IDispatch, IMyClass)
    COM_INTERFACE_ENTRY(IDebugTest)
    COM_INTERFACE_ENTRY(IProvideClassInfo)
END_COM_MAP()
```

## <a name="requirements"></a>需求

### <a name="attribute-context"></a>屬性內容

|||
|-|-|
|**適用於**|**類別**，**結構**|
|**可重複**|是|
|**必要屬性**|一或多個項目： `coclass`， `progid`，或`vi_progid`。|
|**無效屬性**|無|

如需有關屬性內容的詳細資訊，請參閱 [屬性內容](cpp-attributes-com-net.md#contexts)。

## <a name="see-also"></a>另請參閱

[COM 屬性](com-attributes.md)<br/>
[類別屬性](class-attributes.md)<br/>
[Typedef、Enum、Union 和 Struct 屬性](typedef-enum-union-and-struct-attributes.md)