---
title: "allocate | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "allocate"
  - "allocate_cpp"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "__declspec 關鍵字 [C++], allocate"
  - "allocate __declspec 關鍵字"
ms.assetid: 67828b31-de60-4c0e-b0a6-ef3aab22641d
caps.latest.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 6
---
# allocate
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**Microsoft 特定的**  
  
 **allocate** 宣告指定名稱會為將配置之資料項目的資料區段命名。  
  
## 語法  
  
```  
  
__declspec(allocate("  
segname  
")) declarator  
```  
  
## 備註  
 名稱 *segname* 必須使用下列其中一種 pragmas 進行宣告：  
  
-   [code\_seg](../preprocessor/code-seg.md)  
  
-   [const\_seg](../preprocessor/const-seg.md)  
  
-   [data\_seg](../preprocessor/data-seg.md)  
  
-   [init\_seg](../preprocessor/init-seg.md)  
  
-   [section](../preprocessor/section.md)  
  
## 範例  
  
```  
// allocate.cpp  
#pragma section("mycode", read)  
__declspec(allocate("mycode"))  int i = 0;  
  
int main() {  
}  
```  
  
 **END Microsoft 特定的**  
  
## 請參閱  
 [\_\_declspec](../cpp/declspec.md)   
 [C\+\+ 關鍵字](../cpp/keywords-cpp.md)