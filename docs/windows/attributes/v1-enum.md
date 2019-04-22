---
title: v1_enum (C++ COM 屬性)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.v1_enum
helpviewer_keywords:
- v1_enum attribute
ms.assetid: 2fe92d92-81b9-4a1c-b6ce-437d0eb770ca
ms.openlocfilehash: 08654eed7ad467dc22d2cbbf811c9169e5292f16
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59024558"
---
# <a name="v1enum"></a>v1_enum

指示指定的列舉型別會傳輸為 32 位元的實體，而不是 16 位元的預設值。

## <a name="syntax"></a>語法

```cpp
[v1_enum]
```

## <a name="remarks"></a>備註

**V1_enum** C++屬性具有相同的功能[v1_enum](/windows/desktop/Midl/v1-enum) MIDL 屬性。

## <a name="example"></a>範例

下列程式碼範例將示範用法**v1_enum**:

```cpp
// cpp_attr_ref_v1_enum.cpp
// compile with: /LD
[module(name="MyLibrary")];

[export, v1_enum]
enum eList {
   e1 = 1, e2 = 2
};
```

## <a name="requirements"></a>需求

### <a name="attribute-context"></a>屬性內容

|||
|-|-|
|**適用於**|列舉型別|
|**可重複**|否|
|**必要屬性**|None|
|**無效屬性**|None|

如需有關屬性內容的詳細資訊，請參閱 [屬性內容](cpp-attributes-com-net.md#contexts)。

## <a name="see-also"></a>另請參閱

[IDL 屬性](idl-attributes.md)<br/>
[Typedef、Enum、Union 和 Struct 屬性](typedef-enum-union-and-struct-attributes.md)