---
title: "匯出 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- vc-attr.export
dev_langs:
- C++
helpviewer_keywords:
- export attribute
ms.assetid: 70b3e848-fad6-4e09-8c72-be60ca72a4df
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 24619e3a0e707b40590b0ffb37b415629a18b1cd
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="export"></a>匯出
會導致資料結構，以便放入.idl 檔案。  
  
## <a name="syntax"></a>語法  
  
```  
  
[export]  
  
```  
  
## <a name="remarks"></a>備註  
 **匯出**c + + 屬性會造成放入.idl 檔案，則是二進位檔相容的格式可搭配任何語言中的類型程式庫中的 可用的資料結構。  
  
 您不能套用**匯出**屬性的類別，即使此類別只具有公用成員 (相當於`struct`)。  
  
 如果您匯出未命名`enum`s 或`struct`s，將其指定名稱開頭為**__unnamed***x*，其中*x*是連續的數字。  
  
 適用於匯出 typedef 為基底類型、 結構、 等位、 列舉，或輸入識別項。  請參閱[typedef](http://msdn.microsoft.com/library/windows/desktop/aa367287)如需詳細資訊。  
  
## <a name="example"></a>範例  
 下列程式碼示範如何使用**匯出**屬性：  
  
```  
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
|**適用於**|**等位**， `typedef`， `enum`， `struct`，或`interface`|  
|**可重複**|否|  
|**必要屬性**|無|  
|**無效屬性**|無|  
  
 如需詳細資訊，請參閱 [屬性內容](../windows/attribute-contexts.md)。  
  
## <a name="see-also"></a>請參閱  
 [編譯器屬性](../windows/compiler-attributes.md)   
 [Typedef、Enum、Union 和 Struct 屬性](../windows/typedef-enum-union-and-struct-attributes.md)   
