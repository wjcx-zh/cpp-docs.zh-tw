---
title: "__identifier (C++/CLI) | Microsoft Docs"
ms.custom: ""
ms.date: "12/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "__identifier"
  - "__identifier_cpp"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "__identifier keyword [C++]"
ms.assetid: 348428af-afa7-4ff3-b571-acf874301cf2
caps.latest.revision: 18
caps.handback.revision: 18
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# __identifier (C++/CLI)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

啟用 Visual C\+\+ 關鍵字做為識別項。  
  
## 所有平台  
 **語法**  
  
```  
  
__identifier(  
Visual_C++_keyword  
)  
  
```  
  
 **備註**  
  
 對非關鍵字的識別碼使用 `__identifier` 關鍵字是得到允許的，不過，強烈建議您不要做為一種樣式。  
  
## [!INCLUDE[wrt](../atl/reference/includes/wrt_md.md)]  
  
### 需求  
 編譯器選項：**\/ZW**  
  
### 範例  
 **範例**  
  
 在下列範例中，名為 `template` 的類別以 C\# 建立並散發為 DLL。  在使用 `template` 類別的 Visual C\+\+ 程式中， `__identifier` 關鍵字隱藏 `template` 是標準 C\+\+ 關鍵字2的事實。  
  
```  
// identifier_template.cs  
// compile with: /target:library  
public class template {  
   public void Run() { }  
}  
```  
  
```  
// keyword__identifier.cpp  
// compile with: /ZW  
#using <identifier_template.dll>  
int main() {  
   __identifier(template)^ pTemplate = ref new __identifier(template)();  
   pTemplate->Run();  
}  
```  
  
## [!INCLUDE[clr_for_headings](../dotnet/includes/clr_for_headings_md.md)]  
 **備註**  
  
 `__identifier` 關鍵字適用於 **\/clr** 和 **\/clr:oldSyntax** 編譯器選項。  
  
### 需求  
 編譯器選項：**\/clr**  
  
### 範例  
 **範例**  
  
 在下列範例中，名為 `template` 的類別以 C\# 建立並散發為 DLL。  在使用 `template` 類別的 Visual C\+\+ 程式中， `__identifier` 關鍵字隱藏 `template` 是標準 C\+\+ 關鍵字的事實。  
  
```  
// identifier_template.cs  
// compile with: /target:library  
public class template {  
   public void Run() { }  
}  
```  
  
```  
// keyword__identifier.cpp  
// compile with: /clr  
#using <identifier_template.dll>  
  
int main() {  
   __identifier(template) ^pTemplate = gcnew __identifier(template)();  
   pTemplate->Run();  
}  
```  
  
## 請參閱  
 [Component Extensions for Runtime Platforms](../windows/component-extensions-for-runtime-platforms.md)   
 [Component Extensions for Runtime Platforms](../windows/component-extensions-for-runtime-platforms.md)