---
title: "視內容而有所區別的關鍵字 (C++ 元件擴充功能) | Microsoft Docs"
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
  - "internal_CPP"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "視內容而有所區別的關鍵字"
ms.assetid: e33da089-f434-44e9-8cce-4668d05a8939
caps.latest.revision: 19
caps.handback.revision: 17
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 視內容而有所區別的關鍵字 (C++ 元件擴充功能)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

「*內容相關性關鍵字*」\(Context\-Sensitive Keyword\) 是在特定內容中才會辨識的語言項目。  在特定內容之外，內容相關性關鍵字可以是使用者定義的符號。  
  
## 所有執行階段  
 **備註**  
  
 下列是內容相關性關鍵字清單：  
  
-   [abstract](../windows/abstract-cpp-component-extensions.md)  
  
-   [Delegate \- 委派](../windows/delegate-cpp-component-extensions.md)  
  
-   [event](../windows/event-cpp-component-extensions.md)  
  
-   [finally](../dotnet/finally.md)  
  
-   [for each、in](../dotnet/for-each-in.md)  
  
-   [initonly](../dotnet/initonly-cpp-cli.md)  
  
-   `internal` \(請參閱[成員可視性](../misc/member-visibility.md)\)  
  
-   [literal](../windows/literal-cpp-component-extensions.md)  
  
-   [override](../windows/override-cpp-component-extensions.md)  
  
-   [property](../windows/property-cpp-component-extensions.md)  
  
-   [sealed](../windows/sealed-cpp-component-extensions.md)  
  
-   `where` \([Generics](../windows/generics-cpp-component-extensions.md)的一部分\)  
  
 基於可讀性目的，您可能需要限制內容相關性關鍵字做為使用者定義符號的使用。  
  
## [!INCLUDE[wrt](../atl/reference/includes/wrt_md.md)]  
 **備註**  
  
 \(沒有這項功能的平台特定備註。\)  
  
### 需求  
 編譯器選項：**\/ZW**  
  
## [!INCLUDE[clr_for_headings](../dotnet/includes/clr_for_headings_md.md)]  
 **備註**  
  
 \(沒有這項功能的平台特定備註。\)  
  
### 需求  
 編譯器選項：**\/clr**  
  
### 範例  
 **範例**  
  
 下列程式碼範例會示範，在適當的內容中，`property` 內容相關性關鍵字可用來定義屬性和變數。  
  
```  
// context_sensitive_keywords.cpp  
// compile with: /clr  
public ref class C {  
   int MyInt;  
public:  
   C() : MyInt(99) {}  
  
   property int Property_Block {   // context-sensitive keyword  
      int get() { return MyInt; }  
   }  
};  
  
int main() {  
   int property = 0;               // variable name  
   C ^ MyC = gcnew C();  
   property = MyC->Property_Block;  
   System::Console::WriteLine(++property);  
}  
```  
  
 **輸出**  
  
  **100**   
## 請參閱  
 [Component Extensions for Runtime Platforms](../windows/component-extensions-for-runtime-platforms.md)