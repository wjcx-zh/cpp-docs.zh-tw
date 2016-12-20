---
title: "__restrict | Microsoft Docs"
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
  - "__restrict"
  - "__restrict_cpp"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "__restrict 關鍵字 [C++]"
ms.assetid: 2d151b4d-f930-49df-bd16-d8757ec7fa83
caps.latest.revision: 13
caps.handback.revision: 13
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# __restrict
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

就如同 **\_\_declspec \( [restrict](../cpp/restrict.md) \)** 修飾詞一樣，`__restrict` 關鍵字會指出符號在目前範圍中沒有別名。  `__restrict` 關鍵字與 `__declspec ( restrict )` 修飾詞具有下列差異：  
  
-   `__restrict` 關鍵字只對變數有效，而 `__declspec ( restrict )` 只對函式宣告和定義有效。  
  
-   `__restrict` 類似於 C99 規格中的 `restrict`，不過 `__restrict` 可以在 C\+\+ 或 C 程式中使用。  
  
-   使用 `__restrict` 時，編譯器將不會傳播變數的無別名屬性。  也就是說，如果您將 `__restrict` 變數指派至非 `__restrict` 變數，編譯器還是會允許非 \_\_restrict 變數具有別名。  這種行為與 C99 規格中 `restrict` 關鍵字的行為不同。  
  
 一般而言，如果您要影響整個函式的行為，使用 `__declspec ( restrict )` 的效果會比使用關鍵字更好。  
  
 在 Visual Studio 2015 和更新版本中，`__restrict` 可以用於 C\+\+ 參考中。  
  
> [!NOTE]
>  若是在同時擁有 [volatile](../cpp/volatile-cpp.md) 關鍵字的變數上使用，則 `volatile` 的優先順序較高。  
  
## 範例  
  
```  
// __restrict_keyword.c  
// compile with: /LD  
// In the following function, declare a and b as disjoint arrays  
// but do not have same assurance for c and d.  
void sum2(int n, int * __restrict a, int * __restrict b,   
          int * c, int * d) {  
   int i;  
   for (i = 0; i < n; i++) {  
      a[i] = b[i] + c[i];  
      c[i] = b[i] + d[i];  
    }  
}  
  
// By marking union members as __restrict, tell compiler that  
// only z.x or z.y will be accessed in any given scope.  
union z {  
   int * __restrict x;  
   double * __restrict y;  
};  
```  
  
## 請參閱  
 [C\+\+ 關鍵字](../cpp/keywords-cpp.md)