---
title: "函式原型 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- function prototypes
- function return types, function prototypes
- data types [C], function return types
- functions [C], return types
- prototypes [C++], function
ms.assetid: d152f8e6-971e-432c-93ca-5a91400653c2
caps.latest.revision: 9
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
ms.translationtype: Human Translation
ms.sourcegitcommit: d6eb43b2e77b11f4c85f6cf7e563fe743d2a7093
ms.openlocfilehash: a9f005b9a48cc3c09f1fce1803988dbfe9eaaf72
ms.contentlocale: zh-tw
ms.lasthandoff: 05/18/2017

---
# <a name="function-prototypes"></a>函式原型
函式宣告在函式定義之前，並且會指定函式的名稱、傳回型別、儲存類別和其他屬性。 函式宣告也必須建立函式引數的類型和識別項，才能成為原型。  
  
## <a name="syntax"></a>語法  
 `declaration`：  
 *declaration-specifiers attribute-seq* opt*init-declarator-list* opt**;**  
  
 /\* *attribute-seq* opt 是 Microsoft 特定的 */  
  
 *declaration-specifiers*：  
 *storage-class-specifier declaration-specifiers* opt  
  
 *type-specifier declaration-specifiers* opt  
  
 *type-qualifier declaration-specifiers* opt  
  
 *init-declarator-list*：  
 *init-declarator*  
  
 *init-declarator-list*  **,**  *init-declarator*  
  
 *init-declarator*：  
 *declarator*  
  
 *declarator = initializer*  
  
 `declarator`：  
 *pointer* opt*direct-declarator*  
  
 *direct-declarator*: /\* 函式宣告子 \*/  
 *direct-declarator*  **(**  *parameter-type-list*  **)**  /* 新樣式的宣告子 \*/  
  
 *direct-declarator*  **(**  *identifier-list* opt**)** /* 過時樣式宣告子 \*/  
  
 原型的形式與函式定義的相同，但右括號後面加上分號即可終止原型，因此沒有主體。 在任何情況下，傳回類型必須與在函式定義中指定的傳回類型一致。  
  
 函式原型有下列重要用途：  
  
-   它們會建立傳回 `int` 以外之類型的函式的傳回類型。 雖然傳回 `int` 值的函式不需要原型，仍建議使用原型。  
  
-   如果沒有完整的原型，就會執行標準轉換，但不會嘗試根據參數數目檢查引數的類型或數目。  
  
-   原型用於在定義這些函式之前初始化函式指標。  
  
-   參數清單用於根據函式定義中的參數檢查函式呼叫中的引數對應。  
  
 每個參數的轉換類型決定函式呼叫置於堆疊之引數的解譯方式。 引數和參數之間的類型不符，可能會造成堆疊上的引數解譯不正確。 例如，在 16 位元電腦上，如果將 16 位元指標當成引數傳遞，然後宣告為 **long** 參數，則堆疊的前 32 個位元會被解譯為 **long** 參數。 這個錯誤不只會造成 **long** 參數出現問題，也會使該參數之後的參數出現問題。 您可以為所有函式宣告完整的函式原型，來偵測這種錯誤。  
  
 原型會建立函式的屬性，以便針對其定義之前 (或發生在其他原始檔案中) 的函式呼叫，檢查引數類型和傳回型別不符的情形。 例如，若在原型中指定 **static** 儲存類別指定名稱，則必須同時在函式定義中指定 **static** 儲存類別。  
  
 完整的參數宣告 (`int a`) 可以和同一個宣告中的抽象宣告子 (`int`) 混用。 例如，下列宣告是合法的：  
  
```  
int add( int a, int );  
```  
  
 原型可以包含以引數傳遞之每個運算式的類型和識別項。 不過，此類識別項的範圍只到宣告結尾為止。 原型也可以反映引數數目可變或未傳遞任何引數這項事實。 若沒有這種清單，就不會顯示不符，因此編譯器無法產生相關的診斷訊息。 如需類型檢查的詳細資訊，請參閱[引數](../c-language/arguments.md)。  
  
 現在當使用 /Za 編譯器選項進行編譯時，Microsoft C 編譯器中的原型範圍符合 ANSI 標準。 這表示如果您在原型中宣告 `struct` 或 **union** 標記，則會在該範圍中輸入該標記，而不是在全域範圍中輸入。 例如，為遵循 ANSI 標準而使用 /Za 編譯時，若呼叫此函式，一定會出現類型不符錯誤：  
  
```  
void func1( struct S * );  
```  
  
 若要修正程式碼，請在函式原型之前於全域範圍定義或宣告 `struct` 或 **union**：  
  
```  
struct S;  
void func1( struct S * );  
```  
  
 在 /Ze 下，仍然會在全域範圍輸入該標記。  
  
## <a name="see-also"></a>另請參閱  
 [函式](../c-language/functions-c.md)
