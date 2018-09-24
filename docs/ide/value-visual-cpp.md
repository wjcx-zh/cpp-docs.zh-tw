---
title: '&lt;value&gt; (Visual C++) | Microsoft Docs'
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
ms.openlocfilehash: 0a194e45fd79ae59dc91abb21a9fb038d3ec4008
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46041684"
---
# <a name="ltvaluegt-visual-c"></a>&lt;value&gt; (Visual C++)
\<value> 標記可讓您描述屬性和屬性存取子方法。 請注意，當您在 Visual Studio 整合式開發環境中使用程式碼精靈新增屬性時，會新增新屬性的 [\<summary>](../ide/summary-visual-cpp.md) 標記。 您接著應該手動新增 \<value> 標記，來描述屬性所代表的值。  
  
## <a name="syntax"></a>語法  
  
```  
<value>property-description</value>  
```  
  
#### <a name="parameters"></a>參數  
*property-description*<br/>
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
  
## <a name="see-also"></a>請參閱  
 [XML 文件](../ide/xml-documentation-visual-cpp.md)