---
title: "編譯時期封裝的 Pimpl (現代 C++) | Microsoft Docs"
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
ms.assetid: c3e8a90a-b328-4990-82bb-e1b147f76e07
caps.latest.revision: 11
caps.handback.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 編譯時期封裝的 Pimpl (現代 C++)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

*pimpl 慣用語* 是隱藏實作，最小化耦合和分隔介面的現代 C\+\+ 技術。  Pimpl 為 \< 實作的指標是簡短」。您可能已經熟悉這個概念，但像徹斯特貓或編譯器防火牆慣用語中其他的了解。  
  
## 為何要使用 pimpl?  
 這 pimpl 慣用語如何改善軟體開發生命週期:  
  
-   編輯相依性的最小化。  
  
-   介面和實作分開。  
  
-   可攜性。  
  
## Pimpl 標題  
  
```cpp  
  
// my_class.h  
class my_class {  
   //  ... all public and protected stuff goes here ...  
private:  
   class impl; unique_ptr<impl> pimpl; // opaque type here  
};  
  
```  
  
 pimpl 慣用語避免重建串聯和易損壞的物件配置。  它為 \(傳遞\) 常見型別是適合。  
  
## Pimpl 實作  
 定義在 .cpp 檔中的 `impl` 類別。  
  
```cpp  
  
// my_class.cpp  
class my_class::impl {  // defined privately here  
  // ... all private data and functions: all of these  
  //     can now change without recompiling callers ...  
};  
my_class::my_class(): pimpl( new impl )  
{  
  // ... set impl values ...   
}  
```  
  
## 最佳作法  
 考慮是否將支援非擲回的交換特製化。  
  
## 請參閱  
 [歡迎回到 C\+\+](../cpp/welcome-back-to-cpp-modern-cpp.md)   
 [C\+\+ 語言參考](../cpp/cpp-language-reference.md)   
 [C\+\+ Standard Library](../standard-library/cpp-standard-library-reference.md)