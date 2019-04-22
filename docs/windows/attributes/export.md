---
title: 匯出 (C++ COM 屬性)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.export
helpviewer_keywords:
- export attribute
ms.assetid: 70b3e848-fad6-4e09-8c72-be60ca72a4df
ms.openlocfilehash: 5ffa4283b8a2b265809d06b72be96e217cf8bf9f
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59023603"
---
# <a name="export"></a>匯出

會導致資料結構，以放入.idl 檔案。

## <a name="syntax"></a>語法

```cpp
[export]
```

## <a name="remarks"></a>備註

**匯出**C++屬性會導致放入.idl 檔案，然後才能在類型程式庫中的二進位檔相容的格式，使它可以用於任何語言中的 使用的資料結構。

您不能套用**匯出**屬性的類別，即使類別只有公用成員 (相當於**結構**)。

如果您匯出未命名**列舉**或是**結構**，它指定名稱的開頭 **__unnamed**<em>x</em>，其中*x*是一個循序號碼。

適用於匯出的 typedef 基底類型、 結構、 等位、 列舉、 或型別識別項。  請參閱[typedef](/windows/desktop/Midl/typedef)如需詳細資訊。

## <a name="example"></a>範例

下列程式碼示範如何使用**匯出**屬性：

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
|**適用於**|**union**， **typedef**，**列舉**，**結構**，或**介面**|
|**可重複**|否|
|**必要屬性**|None|
|**無效屬性**|None|

如需詳細資訊，請參閱 [屬性內容](cpp-attributes-com-net.md#contexts)。

## <a name="see-also"></a>另請參閱

[編譯器屬性](compiler-attributes.md)<br/>
[Typedef、Enum、Union 和 Struct 屬性](typedef-enum-union-and-struct-attributes.md)