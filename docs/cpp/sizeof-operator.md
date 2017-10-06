---
title: "sizeof 運算子 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- sizeof_cpp
dev_langs:
- C++
helpviewer_keywords:
- sizeof operator
ms.assetid: 8bc3b6fb-54a1-4eb7-ada0-05f8c5efc532
caps.latest.revision: 7
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
ms.openlocfilehash: 67b699a93880a89e634ac024699ac79a9ea8d3ba
ms.contentlocale: zh-tw
ms.lasthandoff: 09/25/2017

---
# <a name="sizeof-operator"></a>sizeof 運算子
就類型 `char` 的大小而言，會產生其運算元的大小。  
  
> [!NOTE]
>  如需有關資訊`sizeof ...`運算子，請參閱[省略符號和 Variadic 樣板](../cpp/ellipses-and-variadic-templates.md)。  
  
## <a name="syntax"></a>語法  
  
```  
sizeof unary-expression  
sizeof  ( type-name )  
```  
  
## <a name="remarks"></a>備註  
 `sizeof` 運算子的結果是 `size_t` 類型，這是 Include 檔 STDDEF.H 中定義的整數類資料類型。 這個運算子可以避免在您的程式中指定與電腦相關的資料大小。  
  
 `sizeof` 的運算元可以是下列其中一項：  
  
-   類型名稱。 若要以類型名稱來使用 `sizeof`，該名稱必須以括號括住。  
  
-   一個運算式。 與運算式搭配使用時，是否用括號來指定 `sizeof` 都可以。 並不會評估運算式。  
  
 將 `sizeof` 運算子套用至 `char` 類型的物件時，會產生 1。 將 `sizeof` 運算子套用至陣列時，會產生該陣列中的位元組總數，而不是陣列識別項所表示的指標大小。 若要取得陣列識別項所表示的指標大小，請將它當作參數傳遞至使用 `sizeof` 的函式。 例如:   
  
## <a name="example"></a>範例  
  
```  
#include <iostream>  
using namespace std;  
  
size_t getPtrSize( char *ptr )  
{  
   return sizeof( ptr );  
}  
  
int main()  
{  
   char szHello[] = "Hello, world!";  
  
   cout  << "The size of a char is: "  
         << sizeof( char )  
         << "\nThe length of " << szHello << " is: "  
         << sizeof szHello  
         << "\nThe size of the pointer is "  
         << getPtrSize( szHello ) << endl;  
}  
```  
  
## <a name="sample-output"></a>範例輸出  
  
```  
The size of a char is: 1  
The length of Hello, world! is: 14  
The size of the pointer is 4  
```  
  
 將 `sizeof` 運算子套用至 `class`、`struct` 或 `union` 類型時，結果是該類型物件中的位元組數，加上為了讓成員對齊字邊界而加入的任何填補位元組。 在加上個別成員的儲存需求之後，其結果不一定會對應計算的大小。 [/Zp](../build/reference/zp-struct-member-alignment.md)編譯器選項和[套件](../preprocessor/pack.md)pragma 會影響成員的對齊界限。  
  
 `sizeof` 運算子絕不會產生 0，即使用於空類別也一樣。  
  
 `sizeof` 運算子不能與下列運算元搭配使用：  
  
-   函式。 (不過，`sizeof` 可套用於函式的指標。)  
  
-   位元欄位。  
  
-   未定義的類別。  
  
-   `void` 類型。  
  
-   以動態方式配置的陣列。  
  
-   外部陣列。  
  
-   不完整的類型。  
  
-   以括號括住的不完整類型名稱。  
  
 將 `sizeof` 運算子套用至參考時，結果相同，就像 `sizeof` 套用至物件本身一樣。  
  
 如果可變大小的陣列是結構的最後一個項目，`sizeof` 運算子會傳回不含陣列的結構大小。  
  
 `sizeof` 運算子經常用來計算陣列中的元素數目，所使用的運算式格式如下：  
  
```  
sizeof array / sizeof array[0]  
```  
  
## <a name="see-also"></a>另請參閱  
 [具有一元運算子的運算式](../cpp/expressions-with-unary-operators.md)   
 [關鍵字](../cpp/keywords-cpp.md)
