---
title: '&lt;另請參閱&gt;（Visual c + +） |Microsoft 文件'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-ide
ms.topic: conceptual
f1_keywords:
- <seealso>
- seealso
dev_langs:
- C++
helpviewer_keywords:
- seealso C++ XML tag
- <seealso> C++ XML tag
ms.assetid: cb33d100-9c50-4485-8d0c-573429eff155
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 6a726a2fa1694fd346a6632fdc5e40bd53547fc8
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="ltseealsogt-visual-c"></a>&lt;另請參閱&gt;（Visual c + +）
\<seealso> 標記可讓您指定要顯示在＜請參閱＞一節中的文字。 使用 [\<see>](../ide/see-visual-cpp.md)，以在文字內指定連結。  
  
## <a name="syntax"></a>語法  
  
```  
<seealso cref="member"/>  
```  
  
#### <a name="parameters"></a>參數  
 `member`  
 可從目前編譯環境呼叫的成員或欄位參考。  以單引號或雙引號將名稱括起來。  
  
 編譯器會檢查指定的程式碼項目存在，並解析`member`在輸出 XML 中的項目名稱。  如果編譯器找不到 `member`，它會發出警告。  
  
 如需如何建立泛型型別 cref 參考的資訊，請參閱[\<see>](../ide/see-visual-cpp.md)。  
  
## <a name="remarks"></a>備註  
 編譯搭配 [/doc](../build/reference/doc-process-documentation-comments-c-cpp.md) 可處理檔案的文件註解。  
  
 如需使用 \<seealso> 的範例，請參閱 [\<summary>](../ide/summary-visual-cpp.md)。  
  
 Visual C++ 編譯器會透過文件註解嘗試一次解決 cref 參考。  因此，如果使用 C++ 查閱規則，當編譯器找不到符號時，參考就會被標記為無法解析。  
  
## <a name="example"></a>範例  
 在下列範例中，無法解析的符號是在 cref 參考。 以 B::Test cref 的 XML 註解將會是`<seealso cref="!:B::Test" />`，而會語式正確的參考 A::Test `<seealso cref="M:A.Test" />`。  
  
```  
// xml_seealso_tag.cpp  
// compile with: /LD /clr /doc  
// post-build command: xdcmake xml_seealso_tag.dll  
  
/// Text for class A.  
public ref struct A {  
   /// <summary><seealso cref="A::Test"/>  
   /// <seealso cref="B::Test"/>  
   /// </summary>  
   void MyMethod(int Int1) {}  
  
   /// text  
   void Test() {}  
};  
  
/// Text for class B.  
public ref struct B {  
   void Test() {}  
};  
```  
  
## <a name="see-also"></a>另請參閱  
 [XML 文件](../ide/xml-documentation-visual-cpp.md)