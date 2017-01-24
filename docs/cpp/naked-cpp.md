---
title: "naked (C++) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "naked_cpp"
  - "naked"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "__declspec 關鍵字 [C++]，naked"
  - "naked __declspec 關鍵字"
ms.assetid: 69723241-05e1-439b-868e-20a83a16ab6d
caps.latest.revision: 12
caps.handback.revision: 12
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# naked (C++)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**Microsoft 專有的**  
  
 對於帶有 `naked` 屬性而宣告的函式，編譯器會產生沒有初構（prolog）和終解（epilog）的程式碼。  藉由使用內嵌組譯程式碼，您可以使用這個特色撰寫自己的初構和終解程式碼。  Naked 函式特別適用於文字虛擬裝置驅動程式方面。請注意 `naked` 屬性只在 x86 和 ARM 上可以使用，並且無法在 [!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)] 上使用。  
  
## 語法  
  
```  
__declspec(naked) declarator  
```  
  
## 備註  
 因為 `naked` 屬性只與函式定義有關係，並且不是型別修飾詞，所以 Naked 函式必須使用擴充屬性語法和 [\_\_declspec](../cpp/declspec.md) 關鍵字。  
  
 編譯器無法為標記有 Naked 屬性的函式產生內嵌函式，即使函式也標記有 [\_\_forceinline](../misc/inline-inline-forceinline.md) 關鍵字。  
  
 如果 `naked` 屬性套用至任何非成員方法的定義之外的東西，編譯器會發出錯誤。  
  
## 範例  
 這個程式碼會定義一個有 `naked` 屬性的函式：  
  
```  
__declspec( naked ) int func( formal_parameters ) {}  
```  
  
 或者，可能是：  
  
```  
#define Naked __declspec( naked )  
Naked int func( formal_parameters ) {}  
```  
  
 `naked` 屬性只會影響編譯器為函式的初構和終解序列產生程式碼作業的設定。  它不會影響為了呼叫這類函式所產生的程式碼。  因此， `naked` 屬性不會被視為函式型別的一部分，並且函式指標不能有 `naked` 屬性。  此外， `naked` 屬性無法套用到資料定義。  例如，此程式碼範例會產生錯誤：  
  
```  
__declspec( naked ) int i;       // Error--naked attribute not  
                                 // permitted on data declarations.  
```  
  
 `naked` 屬性只與函式定義相關，而且無法在函式的原型中指定。  例如，下列宣告會產生編譯器錯誤：  
  
```  
__declspec( naked ) int func();  // Error--naked attribute not   
                                 // permitted on function declarations  
```  
  
 **END Microsoft 專有**  
  
## 請參閱  
 [\_\_declspec](../cpp/declspec.md)   
 [C\+\+ 關鍵字](../cpp/keywords-cpp.md)   
 [Naked 函式呼叫](../cpp/naked-function-calls.md)