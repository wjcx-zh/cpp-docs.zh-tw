---
title: "一維陣列 | Microsoft Docs"
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
  - "C"
helpviewer_keywords: 
  - "陣列 [C++], 一維"
  - "方括號 [ ]"
  - "方括號 [ ], 陣列"
  - "一維陣列"
  - "方括號 [ ]"
  - "方括號 [ ], 陣列"
  - "註標運算式"
ms.assetid: e28536e5-3b77-46b5-97fd-9b938c771816
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 一維陣列
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

後置運算式 \(postfix expression\) 後面跟著以方括號 \(**\[ \]**\) 括住的運算式，是以註標方式表示陣列物件的元素。  註標運算式 \(subscript expression\) 表示 *expression* 所在位置的位址值，其位置在 *postfix\-expression* 以外，當此運算式表示為以下時：  
  
```  
  
postfix-expression [ expression ]  
```  
  
 通常，*postfix\-expression* 所代表的值是指標值，例如陣列識別項，而 *expression* 則是整數值。  不過，在語法上需要的是其中一個指標類型的運算式，另一個則是整數類型。  因此，整數值可以在 *postfix\-expression* 位置，而指標值可以在 *expression* 的括號中，或是在「subscript,」位置。  例如，以下這個程式碼是合法的：  
  
```  
// one_dimensional_arrays.c  
int sum, *ptr, a[10];  
int main() {  
   ptr = a;  
   sum = 4[ptr];  
}  
```  
  
 註標運算式通常用來參考陣列元素，但是您可以將註標套用到任何指標。  無論值的順序為何，*expression* 都必須以方括號 \(**\[ \]**\) 括住。  
  
 評估註標運算式的方式是在指標值中加入整數值，然後將間接運算子 \(**\***\) 套用到結果 \(如需間接運算子的相關討論，請參閱[間接和傳址運算子](../c-language/indirection-and-address-of-operators.md)\)。實際上，假設 `a` 是指標而 `b` 是整數，下列四個運算式對一維陣列而言是相等的：  
  
```  
a[b]  
*(a + b)  
*(b + a)  
b[a]  
```  
  
 根據加法運算子的轉換規則 \(請參閱[加法類運算子](../c-language/c-additive-operators.md)\)，會藉由將整數值乘以指標定址之類型的長度，將整數值轉換為位址位移。  
  
 例如，假設識別項 `line` 參考 `int` 值的陣列。  下列程序用於評估註標運算式 `line[ i ]`：  
  
1.  整數值 `i` 乘以定義為 `int` 項目長度的位元組數目。  `i` 的轉換值代表 `i` `int` 位置。  
  
2.  將這個轉換值加入到原始指標值 \(`line`\)，以產生從 `line` 位移 `i` `int` 個位置的位址。  
  
3.  將間接運算子套用至新的位址。  結果是在該位置之陣列元素 \(憑直覺是 `line [ i ]`\) 的值。  
  
 註標運算式 `line[0]` 代表該行第一個元素的值，因為從 `line` 代表的位址位移是 0。  同樣地，運算式 \(如 `line[5]`\) 會參考從程式行位移五個位置的元素，或是陣列的第六個元素。  
  
## 請參閱  
 [註標運算子：](../cpp/subscript-operator.md)