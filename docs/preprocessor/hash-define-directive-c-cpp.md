---
title: "#define 指示詞 (C/C++) | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "#define"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "#define 指示詞"
  - "#define 指示詞, 語法"
  - "define 指示詞 (#define)"
  - "define 指示詞 (#define), 語法"
  - "前置處理器, 指示詞"
ms.assetid: 33cf25c6-b24e-40bf-ab30-9008f0391710
caps.latest.revision: 13
caps.handback.revision: 13
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# #define 指示詞 (C/C++)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

`#define` 會建立「*巨集*」\(Macro\)，這是識別項或參數化識別項與語彙基元字串之間的關聯。  定義巨集之後，編譯器就可以使用語彙基元字串替代原始程式檔中出現的每個識別項。  
  
## 語法  
 `#define` *identifier* *token\-string*opt  
  
 `#define` *identifier*`(` *identifier*opt`,` *...* `,` *identifier*opt `)` *token\-string*opt  
  
## 備註  
 `#define` 指示詞會讓編譯器以 *token\-string* 替代原始程式檔中出現的每個 *identifier*。  *identifier* 則只有在形成語彙基元時才會被取代。  也就是說，如果 *identifier* 出現在註解、字串或較長的識別項中，就不會將它取代。  如需詳細資訊，請參閱 [C\+\+ 語彙基元](../cpp/tokens-cpp.md)。  
  
 *token\-string* 引數包含一連串語彙基元，例如關鍵字、常數或完整陳述式。  *token\-string* 和 *identifier* 之間必須使用一個或多個空白字元分隔。  這個空白不會視為替代文字的一部分，也不是接在上一個文字語彙基元之後的任何空白。  
  
 沒有 *token\-string* 的 `#define` 會從原始程式檔中移除出現的 *identifier*。  *identifier* 會保持已定義狀態，並且可以使用 `#if defined` 和 `#ifdef` 指示詞加以測試。  
  
 第二個語法形式會定義類似函式且具有參數的巨集。  這種形式可接受選擇性參數清單，但必須以括號括住。  定義巨集之後，後續出現的每個 *identifier*\(*identifier*opt, ..., *identifier*opt\) 都會以 *token\-string* 引數的某個版本取代，其中會以實際引數替代型式參數。  
  
 型式參數名稱會出現在 *token\-string* 中，用以標記實際值替代的位置。  每個參數名稱都可以在 *token\-string* 中出現多次，而且名稱能夠以任何順序出現。  呼叫中引數的數目必須與巨集定義中參數的數目相符。  盡量使用括號可確保正確解譯複雜的實際引數。  
  
 清單中的型式參數是以逗號分隔。  清單中的每個名稱都必須是唯一的，而且清單必須以括號括住。  *identifier* 和左括號之間不可有任何空格分隔。  對於佔用多個原始程式行的長指示詞使用行串連，也就是新行字元之前放置一個反斜線 \(`\`\)。  型式參數名稱的範圍會延伸到結束 *token\-string* 的新行。  
  
 如果已在第二種語法形式中定義巨集，則後面接著引數清單的後續文字執行個體會表示巨集呼叫。  原始程式檔中跟在 *identifier* 執行個體後面的實際引數，符合巨集定義中對應的型式參數。  若 *token\-string* 中的每一個型式參數前面沒有加上字串化運算子 \(`#`\)、字元化運算子 \(`#@`\) 或語彙基元帶入的運算子 \(`##`\)，或者後面沒有接著 `##` 運算子，則會以對應的實際引數取代該參數。  實際引數中的所有巨集都會在指示詞取代型式參數之前展開。\(這些運算子將在[前置處理器運算子](../preprocessor/preprocessor-operators.md)中加以說明\)。  
  
 下列具有引數的巨集範例將示範第二種形式的 `#define` 語法：  
  
```  
// Macro to define cursor lines   
#define CURSOR(top, bottom) (((top) << 8) | (bottom))  
  
// Macro to get a random integer with a specified range   
#define getrandom(min, max) \  
    ((rand()%(int)(((max) + 1)-(min)))+ (min))  
```  
  
 具有副作用的引數有時會造成巨集產生未預期的結果。  *token\-string* 中可能會出現多次特定的型式參數。  如果以具有副作用的運算式取代該型式參數，則運算式連同其副作用可能會經過多次求值。\(請參閱[語彙基元帶入的運算子 \(\#\#\)](../preprocessor/token-pasting-operator-hash-hash.md) 下的範例\)。  
  
 `#undef` 指示詞會導致識別碼的前置處理器定義遭到忽略。  如需詳細資訊，請參閱 [\#undef 指示詞](../preprocessor/hash-undef-directive-c-cpp.md)。  
  
 如果所定義的巨集名稱出現在 *token\-string* 中 \(即使是另一個巨集展開的結果\)，則此巨集不會展開。  
  
 除非第二個語彙基元序列與第一個相同，否則同名巨集的第二個 `#define` 會產生警告。  
  
 **Microsoft 特定的**  
  
 如果新定義與原始定義在語法上相同，Microsoft C\/C\+\+ 可讓您重新定義巨集。  換句話說，這兩個定義可以有不同的參數名稱。  這個行為與 [!INCLUDE[vcpransi](../preprocessor/includes/vcpransi_md.md)] C 不同，後者要求這兩個定義在語彙上應完全相同。  
  
 例如，下列兩個巨集除了參數名稱之外完全相同。  [!INCLUDE[vcpransi](../preprocessor/includes/vcpransi_md.md)] C 不允許這類重新定義，但是 Microsoft C\/C\+\+ 會進行編譯而不會產生錯誤。  
  
```  
#define multiply( f1, f2 ) ( f1 * f2 )  
#define multiply( a1, a2 ) ( a1 * a2 )  
```  
  
 另一方面，下列兩個巨集不相同，而且將會在 Microsoft C\/C\+\+ 中產生警告。  
  
```  
#define multiply( f1, f2 ) ( f1 * f2 )  
#define multiply( a1, a2 ) ( b1 * b2 )  
```  
  
 **END Microsoft 特定的**  
  
 這個範例將示範 `#define` 指示詞：  
  
```  
#define WIDTH       80  
#define LENGTH      ( WIDTH + 10 )  
```  
  
 第一個陳述式會將識別項 `WIDTH` 定義為整數常數 80，並根據 `WIDTH` 定義 `LENGTH` 和整數常數 10。  出現的每個 `LENGTH` 都會由 \(`WIDTH + 10`\) 取代。  然後出現的每個 `WIDTH + 10` 都會依序由運算式 \(`80 + 10`\) 取代。  `WIDTH + 10` 前後的括號很重要，因為括號可用於控制陳述式中的解譯方式，如下所示：  
  
```  
var = LENGTH * 20;  
```  
  
 在前置處理階段之後，陳述式會變成：  
  
```  
var = ( 80 + 10 ) * 20;  
```  
  
 該陳述式的判斷值為 1800。  若沒有括號，則結果為：  
  
```  
var = 80 + 10 * 20;  
```  
  
 該陳述式的判斷值為 280。  
  
 **Microsoft 特定的**  
  
 使用 [\/D](../build/reference/d-preprocessor-definitions.md) 編譯器選項定義巨集和常數，與在檔案開頭使用 `#define` 前置處理器指示詞的作用相同。  使用 \/D 選項最多可以定義 30 個巨集。  
  
 **END Microsoft 特定的**  
  
## 請參閱  
 [前置處理器指示詞](../preprocessor/preprocessor-directives.md)