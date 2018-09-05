---
title: '&lt;param&gt; (Visual C++) | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-ide
ms.topic: conceptual
f1_keywords:
- param
- <param>
dev_langs:
- C++
helpviewer_keywords:
- param C++ XML tag
- <param> C++ XML tag
ms.assetid: 66c1a1c3-4f98-4bcf-8c7d-9a40308982fb
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 69e2950fcc0b29fb819445f3216ef262a2657e4a
ms.sourcegitcommit: a7046aac86f1c83faba1088c80698474e25fe7c3
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/04/2018
ms.locfileid: "43686417"
---
# <a name="ltparamgt-visual-c"></a>&lt;param&gt; (Visual C++)
\<param> 標記應該在方法宣告的註解中用來描述參數的其中一個方法。  
  
## <a name="syntax"></a>語法  
  
```  
<param name='name'>description</param>  
```  
  
#### <a name="parameters"></a>參數  
 `name`  
 方法參數的名稱。  以單引號或雙引號將名稱括起來。  如果編譯器找不到 `name`，它會發出警告。  
  
 `description`  
 參數的描述。  
  
## <a name="remarks"></a>備註  
 \<param> 標記的文字將會顯示於 IntelliSense、[物件瀏覽器](/visualstudio/ide/viewing-the-structure-of-code)以及程式碼結構 Web 報告中。  
  
 編譯搭配 [/doc](../build/reference/doc-process-documentation-comments-c-cpp.md) 可處理檔案的文件註解。  
  
## <a name="example"></a>範例  
  
```  
// xml_param_tag.cpp  
// compile with: /clr /doc /LD  
// post-build command: xdcmake xml_param_tag.dll  
/// Text for class MyClass.  
public ref class MyClass {  
   /// <param name="Int1">Used to indicate status.</param>  
   void MyMethod(int Int1) {  
   }  
};  
```  
  
## <a name="see-also"></a>請參閱  
 [XML 文件](../ide/xml-documentation-visual-cpp.md)