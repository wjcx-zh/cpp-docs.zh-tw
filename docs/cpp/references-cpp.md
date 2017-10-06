---
title: "參考 （c + +） |Microsoft 文件"
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
- objects [C++], referencing
- references [C++]
- references, to pointers
- declarations, references
- references, declaring
- referencing objects, declarator syntax
ms.assetid: 68156f7f-97a0-4b66-b26d-b25ade5e3bd8
caps.latest.revision: 12
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
ms.openlocfilehash: fb208f61d2da9e7daa7a53ac68fdcdfcdf1acab4
ms.contentlocale: zh-tw
ms.lasthandoff: 09/25/2017

---
# <a name="references-c"></a>參考 (C++)
參考 (例如指標) 會儲存位在記憶體中其他位置之物件的位址。 與指標不同，參考在初始化之後不能參照不同的物件，或設為 null。 有兩種類型的參考： 左值參考參照具名變數，右值參考參照[暫存物件](../cpp/temporary-objects.md)。 & 運算子表示左值參考，而 && 運算子根據內容會表示右值參考或通用參考 (右值或左值)。  
  
 參考可能是使用下列語法來宣告：  
  
```  
[storage-class-specifiers] [cv-qualifiers] type-specifiers   
[ms-modifier] declarator [= expression];  
```  
  
 可能會使用任何有效的宣告子來指定參考。 除非參考是函式或陣列類型的參考，否則便會套用下列簡化的語法：  
  
```  
[storage-class-specifiers] [cv-qualifiers] type-specifiers [& or &&]   
[cv-qualifiers] identifier [= expression];  
```  
  
 參考是使用下列序列宣告：  
  
 1. 宣告指定名稱：  
  
-   選擇性的儲存類別規範。  
  
-   選擇性**const**及/或`volatile`限定詞。  
  
-   類型指定名稱：類型的名稱。  
  
-   2. 宣告子：  
  
-   選擇性的 Microsoft 專有修飾詞。 如需詳細資訊，請參閱[Microsoft 專有的修飾詞](../cpp/microsoft-specific-modifiers.md)。  
  
-   & 運算子或 && 運算子。  
  
-   選擇性**const**及/或`volatile`限定詞。  
  
-   識別碼。  
  
 3. 選擇性的初始設定式。  
  
 更複雜的宣告子形式的指標陣列和函式也適用於參考陣列和函式，請參閱[指標](../cpp/pointers-cpp.md)和[宣告子](http://msdn.microsoft.com/en-us/8a7b9b51-92bd-4ac0-b3fe-0c4abe771838)。  
  
 多個宣告子和初始設定式可能會出現在逗號分隔清單中，後面接著一個宣告指定名稱。 例如:  
  
```  
int &i;   
int &i, &j;   
```  
  
 參考、指標和物件可以同時宣告：  
  
```  
int &ref, *ptr, k;   
```  
  
 參考會保存物件的位址，不過其運作方式與物件相同。  
  
 在下列程式中，請注意物件的名稱 `Today` 和物件的參考 `TodayRef` 在程式中的使用方式是相同的：  
  
## <a name="example"></a>範例  
  
```  
// references.cpp  
#include <stdio.h>  
struct S {  
   short i;  
};  
  
int main() {  
   S  s;   // Declare the object.  
   S& SRef = s;   // Declare the reference.  
   s.i = 3;  
  
   printf_s("%d\n", s.i);  
   printf_s("%d\n", SRef.i);  
  
   SRef.i = 4;  
   printf_s("%d\n", s.i);  
   printf_s("%d\n", SRef.i);  
}  
```  
  
```Output  
3  
3  
4  
4  
```  
  
## <a name="comment"></a>註解  
 本節主題：  
  
-   [參考型別函式引數](../cpp/reference-type-function-arguments.md)  
  
-   [參考型別函式傳回](../cpp/reference-type-function-returns.md)  
  
-   [指標的參考](../cpp/references-to-pointers.md)  
  

