---
title: '匯出 (c + + COM 屬性) '
ms.date: 10/02/2018
f1_keywords:
- vc-attr.export
helpviewer_keywords:
- export attribute
ms.assetid: 70b3e848-fad6-4e09-8c72-be60ca72a4df
ms.openlocfilehash: 4854789d9f977b3b747fd9b546cb92642942be88
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/25/2020
ms.locfileid: "88845272"
---
# <a name="export"></a>匯出

使資料結構放在 .idl 檔案中。

## <a name="syntax"></a>語法

```cpp
[export]
```

## <a name="remarks"></a>備註

**`[export]`** C + + 屬性會導致將資料結構放在 .idl 檔案中，然後在類型程式庫中以二進位相容格式提供，使其可用於任何語言。

您無法將 **`[export]`** 屬性套用至類別，即使類別只有 public 成員 () 的對等專案 **`struct`** 。

如果您匯出未命名的 **`enum`** 或 **`struct`** ，則會指定名稱的開頭為 **__unnamed**<em>x</em>，其中 *x* 是序號。

對匯出有效的 typedef 包括基底類型、結構、等位、列舉或類型識別碼。  如需詳細資訊，請參閱 [`typedef`](/windows/win32/Midl/typedef) 。

## <a name="example"></a>範例

下列程式碼說明如何使用 **`[export]`** 屬性：

```cpp
// cpp_attr_ref_export.cpp
// compile with: /LD
[module(name="MyLibrary")];

[export]
struct MyStruct {
   int i;
};
```

## <a name="requirements"></a>規格需求

| 屬性內容 | 值 |
|-|-|
|**適用於**|**`union`**、 **`typedef`** 、 **`enum`** 、 **`struct`** 或 **`interface`**|
|**重複**|否|
|**必要的屬性**|無|
|**無效屬性**|無|

如需詳細資訊，請參閱 [屬性內容](cpp-attributes-com-net.md#contexts)。

## <a name="see-also"></a>另請參閱

[編譯器屬性](compiler-attributes.md)<br/>
[Typedef、Enum、Union 和 Struct 屬性](typedef-enum-union-and-struct-attributes.md)
