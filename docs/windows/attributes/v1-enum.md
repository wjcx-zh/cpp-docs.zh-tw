---
title: 'v1_enum (c + + COM 屬性) '
ms.date: 10/02/2018
f1_keywords:
- vc-attr.v1_enum
helpviewer_keywords:
- v1_enum attribute
ms.assetid: 2fe92d92-81b9-4a1c-b6ce-437d0eb770ca
ms.openlocfilehash: 6529a32b0bfe2de09191e9cced8f6bd98e7ffdcc
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/25/2020
ms.locfileid: "88832980"
---
# <a name="v1_enum"></a>v1_enum

指示以32位實體（而非16位預設值）傳輸指定的列舉型別。

## <a name="syntax"></a>語法

```cpp
[v1_enum]
```

## <a name="remarks"></a>備註

**V1_enum** c + + 屬性具有與[v1_enum](/windows/win32/Midl/v1-enum) MIDL 屬性相同的功能。

## <a name="example"></a>範例

下列程式碼示範如何使用 **v1_enum**：

```cpp
// cpp_attr_ref_v1_enum.cpp
// compile with: /LD
[module(name="MyLibrary")];

[export, v1_enum]
enum eList {
   e1 = 1, e2 = 2
};
```

## <a name="requirements"></a>規格需求

| 屬性內容 | 值 |
|-|-|
|**適用於**|列舉型別|
|**重複**|否|
|**必要的屬性**|無|
|**無效屬性**|無|

如需有關屬性內容的詳細資訊，請參閱 [屬性內容](cpp-attributes-com-net.md#contexts)。

## <a name="see-also"></a>另請參閱

[IDL 屬性](idl-attributes.md)<br/>
[Typedef、Enum、Union 和 Struct 屬性](typedef-enum-union-and-struct-attributes.md)
