---
title: "值的類別： Lvalues 和 Rvalues （Visual c + +） |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- R-values [C++]
- L-values [C++]
ms.assetid: a8843344-cccc-40be-b701-b71f7b5cdcaf
caps.latest.revision: 14
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: HT
ms.sourcegitcommit: 6ffef5f51e57cf36d5984bfc43d023abc8bc5c62
ms.openlocfilehash: a3d230d3374a7be5aa57d965a451235d40cbee12
ms.contentlocale: zh-tw
ms.lasthandoff: 09/25/2017

---
# <a name="lvalues-and-rvalues-visual-c"></a>Lvalues 和 Rvalues （Visual c + +）
每個 c + + 運算式具有類型，並屬於*值類別*。 值類別是當建立、 複製和移動在運算式評估期間的暫存物件時，編譯器必須遵循的規則的基礎。 

 C + + 17 標準會定義運算式值的類別，如下所示：

- A *glvalue*是的運算式的評估判斷物件、 位元欄位或函式的識別。 
- A *prvalue*是的運算式的評估初始化物件或位元欄位，或計算運算子的運算元的值，請在它出現內容所指定。 
- *Xvalue*是 glvalue 代表物件或位元欄位 （通常是因為它是其存留期結尾附近），可以重複使用的資源。 [範例： 特定種類的運算式涉及右值參考 (8.3.2) 產生 xvalues，例如傳回型別是右值參考的函式呼叫或轉型為右值參考類型。 ] 
- *左值*是不是 xvalue glvalue。 
- *右值*prvalue 或 xvalue。 

下圖說明兩個類別之間的關聯性：

 ![C + + 運算式值分類](media/value_categories.png "c + + 運算式值類別")  
 
 左值會有您的程式可以存取的位址。 左值運算式的範例包括變數名稱，包括`const`變數陣列元素中，函式會傳回左值參考，位元欄位、 等位和類別成員的呼叫。 
 
 Prvalue 運算式有沒有可存取您的程式的位址。 Prvalue 運算式的範例包括常值、 函式呼叫傳回非參考類型，並只能由編譯器建立運算式評估期間，但可存取的暫存物件。 

 Xvalue 運算式沒有位址，但是可以用來初始化為右值參考，可讓您存取運算式。 範例包括傳回右值參考，陣列註標、 成員和指標成員運算式的陣列或物件是右值參考的函式呼叫。 
 
 下列範例將示範數種正確和不正確的左值和右值用法：  
  
```  
// lvalues_and_rvalues2.cpp  
int main()  
{  
   int i, j, *p;  
  
   // Correct usage: the variable i is an lvalue and the literal 7 is a prvalue.  
   i = 7;  
  
   // Incorrect usage: The left operand must be an lvalue (C2106).  `j * 4` is a prvalue.
   7 = i; // C2106  
   j * 4 = 7; // C2106  
  
   // Correct usage: the dereferenced pointer is an lvalue.  
   *p = i;   
  
   const int ci = 7;  
   // Incorrect usage: the variable is a non-modifiable lvalue (C3892).  
   ci = 9; // C3892  
  
   // Correct usage: the conditional operator returns an lvalue.  
   ((i < 3) ? i : j) = 7;  
}  
```  
  
> [!NOTE]
>  本主題中的範例將說明運算子未多載時的正確和不正確用法。 藉由多載運算子，您就可以讓像是 `j * 4` 這樣的運算式變成左值。  

  
 條款*左值*和*右值*經常參考的物件參考時。 多個參考的詳細資訊，請參閱[左值參考宣告子： &](../cpp/lvalue-reference-declarator-amp.md)和[右值參考宣告子: （& s) （& s)](../cpp/rvalue-reference-declarator-amp-amp.md)。  
  
## <a name="see-also"></a>另請參閱  
 [基本概念](../cpp/basic-concepts-cpp.md)   
 [左值參考宣告子： &](../cpp/lvalue-reference-declarator-amp.md)   
 [右值參考宣告子：&&](../cpp/rvalue-reference-declarator-amp-amp.md)
