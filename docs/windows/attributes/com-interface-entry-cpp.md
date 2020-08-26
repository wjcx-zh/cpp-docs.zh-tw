---
title: 'com_interface_entry (c + + COM 屬性) '
ms.date: 10/02/2018
f1_keywords:
- vc-attr.com_interface_entry
helpviewer_keywords:
- com_interface_entry attribute
ms.assetid: 10368f81-b99b-4a0f-ba4f-a142e6911a5c
ms.openlocfilehash: 8339afb97df57f5080629dfed08823c5c091c5a3
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/25/2020
ms.locfileid: "88844115"
---
# <a name="com_interface_entry-c"></a>com_interface_entry (C++)

將介面專案加入至目標類別的 COM 對應。

## <a name="syntax"></a>語法

```cpp
[ com_interface_entry(
  com_interface_entry) ]
```

### <a name="parameters"></a>參數

*com_interface_entry*<br/>
字串，其中包含專案的實際文字。 如需可能值的清單，請參閱 [COM_INTERFACE_ENTRY 宏](../../atl/reference/com-interface-entry-macros.md)。

## <a name="remarks"></a>備註

**Com_interface_entry** c + + 屬性會將字元字串的 unabridged 內容插入目標物件的 com 介面對應中。 如果將屬性套用至目標物件一次，則會將專案插入至現有介面對應的開頭。 如果將屬性重複套用至相同的目標物件，則會依照接收的順序，將專案插入介面對應的開頭。

此屬性需要 [coclass](coclass.md)、 [progid](progid.md)或 [vi_progid](vi-progid.md) 屬性 (或表示上述其中一項的另一個屬性) 也套用至相同的項目。 如果使用任何單一屬性，則會自動套用其他兩項。 例如，如果套用 `progid` ，則 `vi_progid` `coclass` 也會套用。

因為第一次使用 **com_interface_entry** 會導致新介面插入介面對應的開頭，所以必須是下列其中一種 COM_INTERFACE_ENTRY 類型：

- COM_INTERFACE_ENTRY

- COM_INTERFACE_ENTRY_IID

- COM_INTERFACE_ENTRY2

- COM_INTERFACE_ENTRY2_IID

**Com_interface_entry**屬性的其他用法可以使用所有支援的 COM_INTERFACE_ENTRY 類型。

這項限制是必要的，因為 ATL 會使用介面對應中的第一個專案做為身分識別 `IUnknown` ，因此，專案必須是有效的介面。 例如，下列程式碼範例無效，因為介面對應中的第一個專案未指定實際的 COM 介面。

```cpp
[ coclass, com_interface_entry =
    "COM_INTERFACE_ENTRY_NOINTERFACE(IDebugTest)"
]
   class CMyClass
   {
   };
```

## <a name="example"></a>範例

下列程式碼會將兩個專案加入至現有的 COM 介面對應 `CMyBaseClass` 。 第一個是標準介面，而第二個則隱藏 `IDebugTest` 介面。

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

產生的 COM 物件對應如下所示 `CMyBaseClass` ：

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

## <a name="requirements"></a>規格需求

| 屬性內容 | 值 |
|-|-|
|**適用於**|**`class`**, **`struct`**|
|**重複**|是|
|**必要的屬性**|下列其中一項或多項： `coclass` 、 `progid` 或 `vi_progid` 。|
|**無效屬性**|無|

如需有關屬性內容的詳細資訊，請參閱 [屬性內容](cpp-attributes-com-net.md#contexts)。

## <a name="see-also"></a>另請參閱

[COM 屬性](com-attributes.md)<br/>
[類別屬性](class-attributes.md)<br/>
[Typedef、Enum、Union 和 Struct 屬性](typedef-enum-union-and-struct-attributes.md)
