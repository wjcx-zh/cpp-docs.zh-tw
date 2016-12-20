---
title: "建議使用的文件註解標記 (Visual C++) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
ms.assetid: 6548e798-5235-4a38-9482-bdc7b88f40a9
caps.latest.revision: 10
caps.handback.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 建議使用的文件註解標記 (Visual C++)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Visual C\+\+ 編譯器處理文件註解程式碼並建立每個的 .xdc 檔案，因此， xdcmake.exe 處理 .xdc 檔案至 .xml 檔案。  處理 .xml 檔案建立文件是需要在您的網站已實作的詳細資料。  
  
 標記在建構處理 \(例如型別和型別成員。  
  
 標記必須緊接在型別或成員之前。  
  
> [!NOTE]
>  文件註解不能套用到命名空間或不在座標定義為屬性和事件;文件註解在類別宣告必須。  
  
 編譯器會處理任何合法的 XML 標記。  下列標記會在使用者文件的常用的功能:  
  
||||  
|-|-|-|  
|[\<c\>](../ide/c-visual-cpp.md)|[\<code\>](../ide/code-visual-cpp.md)|[\<example\>](../ide/example-visual-cpp.md)|  
|[\<exception\>](../ide/exception-visual-cpp.md)1|[\<include\>](../ide/include-visual-cpp.md)1|[\<list\>](../ide/list-visual-cpp.md)|  
|[\<para\>](../ide/para-visual-cpp.md)|[\<param\>](../ide/param-visual-cpp.md)1|[\<paramref\>](../ide/paramref-visual-cpp.md)1|  
|[\<permission\>](../ide/permission-visual-cpp.md)1|[\<remarks\>](../ide/remarks-visual-cpp.md)|[\<returns\>](../ide/returns-visual-cpp.md)|  
|[\<see\>](../ide/see-visual-cpp.md)1|[\<seealso\>](../ide/seealso-visual-cpp.md)1|[\<summary\>](../ide/summary-visual-cpp.md)|  
|[\<value\>](../ide/value-visual-cpp.md)|||  
  
 1.  編譯器會驗證語法。  
  
 在目前版本中， Visual C\+\+ 編譯器不支援 `<paramref>`，由其他 Visual Studio 編譯器支援的標記。  Visual C\+\+ 會支援在未來版本的 `<paramref>` 。  
  
## 請參閱  
 [XML 文件](../ide/xml-documentation-visual-cpp.md)