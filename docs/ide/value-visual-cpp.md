---
title: '&lt;值&gt;（Visual c + +） |Microsoft 文件'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-ide
ms.topic: conceptual
f1_keywords:
- value
- <value>
dev_langs:
- C++
helpviewer_keywords:
- value C++ XML tag
- <value> C++ XML tag
ms.assetid: 0ba0a0d5-bcd7-4862-a169-83f2721ad80e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 8e78c8ace8b482baa29fbabaf102a8a1bccadd06
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="ltvaluegt-visual-c"></a>&lt;值&gt;（Visual c + +）
\<值 > 標記可讓您描述的屬性和屬性存取子方法。 請注意，當您使用 Visual Studio 整合式的開發環境中的程式碼精靈加入屬性，它會新增[\<摘要 >](../ide/summary-visual-cpp.md)新屬性的標記。 您接著應該手動新增 \<value> 標記，來描述屬性所代表的值。  
  
## <a name="syntax"></a>語法  
  
```  
<value>property-description</value>  
```  
  
#### <a name="parameters"></a>參數  
 `property-description`  
 屬性的描述。  
  
## <a name="remarks"></a>備註  
 編譯搭配 [/doc](../build/reference/doc-process-documentation-comments-c-cpp.md) 可處理檔案的文件註解。  
  
## <a name="example"></a>範例  
  
```  
// xml_value_tag.cpp  
// compile with: /LD /clr /doc  
// post-build command: xdcmake xml_value_tag.dll  
using namespace System;  
/// Text for class Employee.  
public ref class Employee {  
private:  
   String ^ name;  
   /// <value>Name accesses the value of the name data member</value>  
public:  
   property String ^ Name {  
      String ^ get() {  
         return name;   
      }  
      void set(String ^ i) {  
         name = i;  
      }  
   }  
};  
```  
  
## <a name="see-also"></a>另請參閱  
 [XML 文件](../ide/xml-documentation-visual-cpp.md)