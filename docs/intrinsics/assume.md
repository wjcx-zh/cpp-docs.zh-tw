---
title: "__assume | Microsoft Docs"
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
  - "__assume"
  - "__assume_cpp"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "__assume 關鍵字 [C++]"
ms.assetid: d8565123-b132-44b1-8235-5a8c8bff85a7
caps.latest.revision: 18
caps.handback.revision: 18
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# __assume
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**Microsoft 特定的**  
  
 傳遞提示給最佳化程式。  
  
## 語法  
  
```  
__assume(    expression )  
```  
  
#### 參數  
 `expression`  
 假設評估為 true 的任何運算式。  
  
## 備註  
 最佳化程式會在關鍵字出現處假設 `expression` 代表的條件為 true，並保持為 true，直到修改 `expression` \(例如，藉由指派給變數\) 為止。  選擇性使用 `__assume` 傳遞給最佳化程式的提示，可以改善最佳化。  
  
 如果 `__assume` 陳述式撰寫成矛盾 \(一律評估為 false 的運算式\)，則它永遠會被視為 `__assume(0)`。  如果您的程式碼未如預期般運作，請確認您定義的 `expression` 有效而且為 true，如先前所述。  如需預期的 `__assume(0)` 行為，請參閱稍後的備註。  
  
> [!WARNING]
>  程式不能在可到達的路徑上包含無效的 `__assume` 陳述式。  如果編譯器可以到達無效的 `__assume` 陳述式，程式可能會導致無法預期且有潛在危險的行為。  
  
 `__assume` 不是真的內建函式。  它不需要宣告為函式，且不能用在 `#pragma intrinsic` 指示詞中。  雖然不會產生程式碼，但最佳化程式所產生的程式碼會受到影響。  
  
 只有當 assert 無法復原時，才在 [ASSERT](../c-runtime-library/reference/assert-asserte-assert-expr-macros.md) 中使用 `__assume`。  請勿在有後續錯誤復原程式碼的 assert 中使用 `__assume`，因為編譯器可能會將錯誤處理程式碼最佳化掉。  
  
 `__assume(0)` 陳述式是特殊的情況。  使用 `__assume(0)`，表示無法到達的程式碼路徑。  下列範例示範如何使用 `__assume(0)`，表示無法到達 switch 陳述式的 default case。  這會示範 `__assume(0)` 最常見的用法。  
  
## 需求  
  
|內建|架構|  
|--------|--------|  
|`__assume`|x86、ARM、[!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|  
  
## 範例  
  
```  
// compiler_intrinsics__assume.cpp  
#ifdef DEBUG  
# define ASSERT(e)    ( ((e) || assert(__FILE__, __LINE__) )  
#else  
# define ASSERT(e)    ( __assume(e) )  
#endif  
  
void func1(int i)  
{  
}  
  
int main(int p)  
{  
   switch(p){  
      case 1:  
         func1(1);  
         break;  
      case 2:  
         func1(-1);  
         break;  
      default:  
         __assume(0);  
            // This tells the optimizer that the default  
            // cannot be reached. As so, it does not have to generate  
            // the extra code to check that 'p' has a value   
            // not represented by a case arm. This makes the switch   
            // run faster.  
   }  
}  
```  
  
 使用 `__assume(0)`，告知最佳化程式無法到達 default case。  此範例示範程式設計人員知道 `p` 將僅能輸入 1 或 2。  如果其他值傳入 `p`，程式就會變成無效，並導致無法預期的行為。  
  
 做為 `__assume(0)` 陳述式的結果，編譯器不會產生程式碼來測試 `p` 是否有不會呈現在 case 陳述式中的值。  若要完成此運作，`__assume(0)` 陳述式必須是 default case 的主體中的第一個陳述式。  
  
 因為編譯器會根據 `__assume` 產生程式碼，如果 `__assume` 陳述式內的運算式在執行階段為 false 時，該程式碼可能無法正確執行。  如果您不確定運算式是否一定會在執行階段為 true，可以使用 `assert` 函式來保護程式碼。  
  
```  
#define ASSERT(e)    ( ((e) || assert(__FILE__, __LINE__)), __assume(e) )  
```  
  
 不幸的是，這種使用 `assert` 防止編譯器執行 default\-case 最佳化，已於本文件稍早所描述。  另一種方法是，可以使用個別的巨集，如下所示。  
  
```  
#ifdef DEBUG  
# define NODEFAULT   ASSERT(0)  
#else  
# define NODEFAULT   __assume(0)  
#endif  
  
   default:  
      NODEFAULT;  
```  
  
## END Microsoft 特定的  
  
## 請參閱  
 [編譯器內建](../intrinsics/compiler-intrinsics.md)   
 [C\+\+ 關鍵字](../cpp/keywords-cpp.md)