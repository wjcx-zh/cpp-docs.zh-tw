---
title: '&lt;請參閱&gt;（Visual c + +） |Microsoft 文件'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-ide
ms.topic: conceptual
f1_keywords:
- <see>
- see
dev_langs:
- C++
helpviewer_keywords:
- <see> C++ XML tag
- see C++ XML tag
ms.assetid: 20ef66f4-b278-45cf-8613-63919edf5720
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: a03dd56320b948d47c765f253bf3e6b706ed2b56
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
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
  
## <a name="see-also"></a>另請參閱  
 [XML 文件](../ide/xml-documentation-visual-cpp.md)