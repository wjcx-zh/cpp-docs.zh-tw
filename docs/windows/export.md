---
title: 匯出 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
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
ms.openlocfilehash: ad5f886c4d475cb51b370ae25549387f191ab4b6
ms.sourcegitcommit: 37a10996022d738135999cbe71858379386bab3d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/08/2018
ms.locfileid: "39653127"
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
  
 如果您匯出未命名**enum**s 或**結構**s，將其指定名稱開頭為 **__unnamed * * * x*，其中*x*是循序數字。  
  
 適用於匯出的 typedef 基底類型、 結構、 等位、 列舉、 或型別識別項。  請參閱[typedef](http://msdn.microsoft.com/library/windows/desktop/aa367287)如需詳細資訊。  
  
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
  
 如需詳細資訊，請參閱 [屬性內容](../windows/attribute-contexts.md)。  
  
## <a name="see-also"></a>另請參閱  
 [編譯器屬性](../windows/compiler-attributes.md)   
 [Typedef、Enum、Union 和 Struct 屬性](../windows/typedef-enum-union-and-struct-attributes.md)   