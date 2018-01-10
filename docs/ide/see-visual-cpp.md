---
title: "&lt;請參閱&gt;（Visual c + +） |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-ide
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- <see>
- see
dev_langs: C++
helpviewer_keywords:
- <see> C++ XML tag
- see C++ XML tag
ms.assetid: 20ef66f4-b278-45cf-8613-63919edf5720
caps.latest.revision: "15"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 15e1aedefe6d20c181ff208f76a61f49e15f5214
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="ltseegt-visual-c"></a>&lt;請參閱&gt;（Visual c + +）
\<see> 標記可讓您在文字內指定連結。 使用[ \<seealso >](../ide/seealso-visual-cpp.md)表示您可能想要出現在另請參閱 > 一節中的文字。  
  
## <a name="syntax"></a>語法  
  
```  
<see cref="member"/>  
```  
  
#### <a name="parameters"></a>參數  
 `member`  
 可從目前編譯環境呼叫的成員或欄位參考。  以單引號或雙引號將名稱括起來。  
  
 編譯器會檢查指定的程式碼項目存在，並解析`member`在輸出 XML 中的項目名稱。  如果編譯器找不到 `member`，它會發出警告。  
  
## <a name="remarks"></a>備註  
 編譯搭配 [/doc](../build/reference/doc-process-documentation-comments-c-cpp.md) 可處理檔案的文件註解。  
  
 請參閱[\<摘要 >](../ide/summary-visual-cpp.md)的使用範例\<看到 >。  
  
 Visual C++ 編譯器會透過文件註解嘗試一次解決 cref 參考。  因此，如果使用 C++ 查閱規則，當編譯器找不到符號時，參考就會被標記為無法解析。 請參閱[ \<seealso >](../ide/seealso-visual-cpp.md)如需詳細資訊。  
  
## <a name="example"></a>範例  
 下列範例說明如何進行 cref 參考泛型型別，這樣就表示編譯器將會解析參考。  
  
```  
// xml_see_cref_example.cpp  
// compile with: /LD /clr /doc  
// the following cref shows how to specify the reference, such that,  
// the compiler will resolve the reference  
/// <see cref="C{T}">  
/// </see>  
ref class A {};  
  
// the following cref shows another way to specify the reference,   
// such that, the compiler will resolve the reference  
/// <see cref="C < T >"/>  
  
// the following cref shows how to hard-code the reference  
/// <see cref="T:C`1">  
/// </see>  
ref class B {};  
  
/// <see cref="A">  
/// </see>  
/// <typeparam name="T"></typeparam>  
generic<class T>  
ref class C {};  
```  
  
## <a name="see-also"></a>請參閱  
 [XML 文件](../ide/xml-documentation-visual-cpp.md)