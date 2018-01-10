---
title: "&lt;權限&gt;（Visual c + +） |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-ide
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- permission
- <permission>
dev_langs: C++
helpviewer_keywords:
- <permission> C++ XML tag
- permission C++ XML tag
ms.assetid: 537ee2bc-95bd-48e4-9ce6-3420c3da87f4
caps.latest.revision: "11"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 416467782be92760ac999301f9899be1260905aa
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="ltpermissiongt-visual-c"></a>&lt;權限&gt;（Visual c + +）
\<permission> 標記可讓您記載成員存取權。 <xref:System.Security.PermissionSet>可讓您指定成員的存取權。  
  
## <a name="syntax"></a>語法  
  
```  
<permission cref="member">description</permission>  
```  
  
#### <a name="parameters"></a>參數  
 `member`  
 可從目前編譯環境呼叫的成員或欄位參考。 編譯器會檢查指定的程式碼項目是否存在，並將 `member` 轉譯為輸出 XML 中的標準項目名稱。  以單引號或雙引號將名稱括起來。  
  
 如果編譯器找不到 `member`，它會發出警告。  
  
 如需如何建立泛型型別 cref 參考的資訊，請參閱[\<see>](../ide/see-visual-cpp.md)。  
  
 `description`  
 成員存取權的描述。  
  
## <a name="remarks"></a>備註  
 編譯搭配 [/doc](../build/reference/doc-process-documentation-comments-c-cpp.md) 可處理檔案的文件註解。  
  
 Visual C++ 編譯器會透過文件註解嘗試一次解決 cref 參考。  因此，如果使用 C++ 查閱規則，當編譯器找不到符號時，參考就會被標記為無法解析。 請參閱[ \<seealso >](../ide/seealso-visual-cpp.md)如需詳細資訊。  
  
## <a name="example"></a>範例  
  
```  
// xml_permission_tag.cpp  
// compile with: /clr /doc /LD  
// post-build command: xdcmake xml_permission_tag.dll  
using namespace System;  
/// Text for class TestClass.  
public ref class TestClass {  
   /// <permission cref="System::Security::PermissionSet">Everyone can access this method.</permission>  
   void Test() {}  
};  
```  
  
## <a name="see-also"></a>請參閱  
 [XML 文件](../ide/xml-documentation-visual-cpp.md)