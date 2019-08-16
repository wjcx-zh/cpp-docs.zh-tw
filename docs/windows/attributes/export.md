---
title: export (C++ COM 屬性)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.export
helpviewer_keywords:
- export attribute
ms.assetid: 70b3e848-fad6-4e09-8c72-be60ca72a4df
ms.openlocfilehash: 771bfdfe4eab2acf31e97a606795066e8938a8a1
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/15/2019
ms.locfileid: "69501609"
---
# <a name="export"></a>匯出

導致將資料結構放在 .idl 檔案中。

## <a name="syntax"></a>語法

```cpp
[export]
```

## <a name="remarks"></a>備註

**Export** C++屬性會將資料結構放在 .idl 檔案中, 然後在類型程式庫中以二進位相容格式提供, 讓它可與任何語言搭配使用。

即使類別只有公用成員 (等同于**結構**), 您也無法將**export**屬性套用至類別。

如果您匯出未命名的**列舉**或**結構**, 它會被指定一個以 **__unnamed**<em>x</em>開頭的名稱, 其中*x*是一個連續的數位。

適用于匯出的 typedef 是基底類型、結構、等位、列舉或類型識別碼。  如需詳細資訊, 請參閱[typedef](/windows/win32/Midl/typedef) 。

## <a name="example"></a>範例

下列程式碼顯示如何使用**export**屬性:

```cpp
// cpp_attr_ref_export.cpp
// compile with: /LD
[module(name="MyLibrary")];

[export]
struct MyStruct {
   int i;
};
```

## <a name="requirements"></a>需求

### <a name="attribute-context"></a>屬性內容

|||
|-|-|
|**適用於**|**union**、 **typedef**、 **enum**、 **struct**或**interface**|
|**可重複**|否|
|**必要屬性**|無|
|**無效屬性**|None|

如需詳細資訊，請參閱 [屬性內容](cpp-attributes-com-net.md#contexts)。

## <a name="see-also"></a>另請參閱

[編譯器屬性](compiler-attributes.md)<br/>
[Typedef、Enum、Union 和 Struct 屬性](typedef-enum-union-and-struct-attributes.md)