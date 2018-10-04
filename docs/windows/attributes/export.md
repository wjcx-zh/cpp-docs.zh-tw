---
title: 匯出 （c + + COM 屬性） |Microsoft Docs
ms.custom: ''
ms.date: 10/02/2018
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.export
dev_langs:
- C++
helpviewer_keywords:
- export attribute
ms.assetid: 70b3e848-fad6-4e09-8c72-be60ca72a4df
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: a636b7d4c943896bcd1e5e7b3580c2d3f7410fc8
ms.sourcegitcommit: 955ef0f9d966e7c9c65e040f1e28fa83abe102a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/04/2018
ms.locfileid: "48790638"
---
# <a name="export"></a>匯出

會導致資料結構，以放入.idl 檔案。

## <a name="syntax"></a>語法

```cpp
[export]
```

## <a name="remarks"></a>備註

**匯出**c + + 屬性會導致放入.idl 檔案，然後才能在類型程式庫中的二進位檔相容的格式，使它可以用於任何語言中的 使用的資料結構。

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
|**必要屬性**|無|
|**無效屬性**|無|

如需詳細資訊，請參閱 <<c0> [ 屬性內容](cpp-attributes-com-net.md#contexts)。

## <a name="see-also"></a>另請參閱

[編譯器屬性](compiler-attributes.md)<br/>
[Typedef、Enum、Union 和 Struct 屬性](typedef-enum-union-and-struct-attributes.md)  