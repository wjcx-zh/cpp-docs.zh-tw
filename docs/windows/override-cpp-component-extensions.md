---
title: "override  (C++ Component Extensions) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "overriding, override keyword [C++]"
  - "override keyword [C++]"
ms.assetid: 34d19257-1686-4fcd-96f5-af07c70ba914
caps.latest.revision: 19
caps.handback.revision: 19
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# override  (C++ Component Extensions)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

`override` 內容相關性關鍵字表示，型別成員覆寫基底類別或基底介面成員。  
  
## 備註  
 `override` 關鍵字在編譯為原生目標 \(預設編譯器選項\)、Windows 執行階段物件 \(**\/ZW** 編譯器選項\) 或 Common Language Runtime 目標 \(**\/clr** 編譯器選項\) 時有效。  
  
 如需覆寫規範的詳細資訊，請參閱 [override 規範](../cpp/override-specifier.md)和[覆寫規範與原生編譯](../dotnet/how-to-declare-override-specifiers-in-native-compilations-cpp-cli.md)。  
  
 如需內容相關性關鍵字的詳細資訊，請參閱[視內容而有所區別的關鍵字](../windows/context-sensitive-keywords-cpp-component-extensions.md)。  
  
## 範例  
 **範例**  
  
 下列程式碼範例顯示，`override` 也可以用於原生編譯。  
  
```cpp#  
// override_keyword_1.cpp  
// compile with: /c  
struct I1 {  
   virtual void f();  
};  
  
struct X : public I1 {  
   virtual void f() override {}  
};  
```  
  
 **範例**  
  
 下列程式碼範例顯示，`override` 可以用於 Windows 執行階段編譯。  
  
```cpp#  
// override_keyword_2.cpp  
// compile with: /ZW /c  
ref struct I1 {  
   virtual void f();  
};  
  
ref struct X : public I1 {  
   virtual void f() override {}  
};  
```  
  
 **需求**  
  
 編譯器選項：**\/ZW**  
  
 **範例**  
  
 下列程式碼範例顯示，`override` 可以用於 Common Language Runtime 編譯。  
  
```cpp#  
// override_keyword_3.cpp  
// compile with: /clr /c  
ref struct I1 {  
   virtual void f();  
};  
  
ref struct X : public I1 {  
   virtual void f() override {}  
};  
```  
  
 **需求**  
  
 編譯器選項：**\/clr**  
  
## 請參閱  
 [override 規範](../cpp/override-specifier.md)   
 [覆寫規範](../windows/override-specifiers-cpp-component-extensions.md)