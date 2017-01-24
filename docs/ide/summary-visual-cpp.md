---
title: "&lt;summary&gt; (Visual C++) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "<summary>"
  - "summary"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "<summary> C++ XML 標記"
  - "summary C++ XML 標記"
ms.assetid: cdeeefbb-1339-45d6-9002-10042a9a2726
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# &lt;summary&gt; (Visual C++)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

\<summary\> 標記應用於描述型別或型別成員。  使用 [\<remarks\>](../ide/remarks-visual-cpp.md) 為型別描述加入補充資訊。  
  
## 語法  
  
```  
<summary>description</summary>  
```  
  
#### 參數  
 `description`  
 為物件的摘要。  
  
## 備註  
 \<summary\> 標記中的文字是唯一的資訊來源型別相關 IntelliSense 中也會顯示 [物件瀏覽器](http://msdn.microsoft.com/zh-tw/f89acfc5-1152-413d-9f56-3dc16e3f0470) 並在程式碼結構 Web 報告。  
  
 使用 [\/doc](../build/reference/doc-process-documentation-comments-c-cpp.md) 進行編譯，將文件註解處理為檔案。  
  
## 範例  
  
```  
// xml_summary_tag.cpp  
// compile with: /LD /clr /doc  
// post-build command: xdcmake xml_summary_tag.dll  
  
/// Text for class MyClass.  
public ref class MyClass {  
public:  
   /// <summary>MyMethod is a method in the MyClass class.  
   /// <para>Here's how you could make a second paragraph in a description. <see cref="System::Console::WriteLine"/> for information about output statements.</para>  
   /// <seealso cref="MyClass::MyMethod2"/>  
   /// </summary>  
   void MyMethod(int Int1) {}  
  
   /// text  
   void MyMethod2() {}  
};  
```  
  
## 請參閱  
 [XML 文件](../ide/xml-documentation-visual-cpp.md)