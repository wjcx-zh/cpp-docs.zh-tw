---
title: "noexcept (C++) | Microsoft Docs"
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
  - "noexcept_cpp"
dev_langs: 
  - "C++"
ms.assetid: df24edb9-c6a6-4e37-9914-fd5c0c3716a8
caps.latest.revision: 5
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# noexcept (C++)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**C\+\+11：**指定函式是否可能擲回例外狀況。  
  
## 語法  
  
```vb  
ReturnType FunctionName(params) noexcept;  
ReturnType FunctionName(params) noexcept(noexcept(expression);  
```  
  
#### 參數  
 運算式  
 評估結果是 True 或 False 的常數運算式。  無條件的版本相當於 noexcept\(true\)。  
  
## 備註  
 `noexcept` \(及其同義字 `noecept(true)`\) 指定函式永遠不會擲回例外狀況或允許從其他任何直接或間接叫用的函式散佈例外狀況。  更具體來說，`noexcept` 表示函式要成為 `noexcept` 的情況，唯有函式所呼叫的所有函式也都是 noexcept 或 const 時，而且沒有可能評估的動態轉換 \(cast\) 需要執行階段檢查、typeid 運算式套用至類型為多型類別類型的 glvalue 運算式，或擲回運算式。  不過，編譯器不必針對可能出現至 `noexcept` 函式的例外狀況，檢查每一個程式碼路徑。  如果例外狀況確實達到標示為 `noexcept` 的函式，則會立即叫用 [std::terminate](../Topic/terminate%20\(%3Cexception%3E\).md)，且不保證會叫用任何範圍中物件的解構函式。  
  
 使用評估為 noexcept\(false\) 之條件式 noexcept 所宣告的函式，會指定其允許散佈例外狀況。  例如，在所複製物件是一般舊資料類型 \(POD\) 的情況下，複製引數的函式可能會宣告為 noexcept。  這類函式可以宣告如下：  
  
```  
#include <type_traits>  
  
template <typename T>  
T copy_object(T& obj) noexcept(std::is_pod<T>)  
{  
 //. . .   
}  
  
```  
  
 使用 `noexcept` 而不使用例外狀況規範 `throw`，後者在 C\+\+11 和更新版本中已取代。  建議您在確定永遠不允許順著呼叫堆疊散佈例外狀況時，對函式套用 `noexcept`。  使用 `noexcept` 宣告的函式可讓編譯器產生在數種不同內容中更有效率的程式碼。  
  
## 請參閱  
 [C\+\+ 例外狀況處理](../cpp/cpp-exception-handling.md)