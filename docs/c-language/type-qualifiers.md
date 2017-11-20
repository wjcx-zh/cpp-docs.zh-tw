---
title: "類型限定詞 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- volatile keyword [C], type qualifier
- type qualifiers
- volatile keyword [C]
- qualifiers for types
- const keyword [C]
- memory, access using volatile
- volatile keyword [C], type specifier
ms.assetid: bb4c6744-1dd7-40a8-b4eb-f5585be30908
caps.latest.revision: "7"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: c4fad93505a5778c23171b413654624a32e825b2
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/24/2017
---
# <a name="type-qualifiers"></a>類型限定詞
類型限定詞會提供兩個屬性的其中一個給識別項。 **const** 類型限定詞會將物件宣告為不可修改。 `volatile` 類型限定詞會宣告一個項目，其值可由超出項目所在程式之控制範圍的項目 (例如同時執行的執行緒) 合法變更。  
  
 這兩個類型限定詞 **const** 和 `volatile` 只能在宣告中出現一次。 類型限定詞可搭配任何類型規範出現，不過不能出現在多重項目宣告中的第一個逗號後面。 例如，下列宣告是合法的：  
  
```  
typedef volatile int VI;  
const int ci;  
```  
  
 下列宣告是不合法的：  
  
```  
typedef int *i, volatile *vi;  
float f, const cf;     
```  
  
 類型限定詞只有在存取做為運算式中左值的識別項時才相關。 如需有關左值和運算式的詳細資訊，請參閱[左值和右值運算式](../c-language/l-value-and-r-value-expressions.md)。  
  
## <a name="syntax"></a>語法  
 *type-qualifier*：  
 **constvolatile**  
  
 以下是合法的 **const** 與 `volatile` 宣告：  
  
```  
int const *p_ci;       /* Pointer to constant int */  
int const (*p_ci);     /* Pointer to constant int */  
int *const cp_i;       /* Constant pointer to int */  
int (*const cp_i);     /* Constant pointer to int */  
int volatile vint;     /* Volatile integer        */  
```  
  
 如果陣列類型的規格包括類型限定詞，則元素為限定，而不是陣列類型。 如果函式類型的規格包含限定詞，則行為會是未定義。 `volatile` 與 **const** 都不會影響物件的值範圍或算術屬性。  
  
 這個清單將描述如何使用 **const** 與 `volatile`。  
  
-   **const**關鍵字可用來修改任何基本或彙總類型，或任何類型物件的指標，或是 `typedef`。 如果項目僅使用 **const** 類型限定詞宣告，其類型將會視為 **const int**。**const** 變數可以初始化，也可以放在儲存區的唯讀區域中。 **const** 關鍵字對於宣告 **const** 的指標很有用，因為它會要求函式不得以任何方式變更指標。  
  
-   編譯器會假設，`volatile` 變數可在程式中的任何一點供使用或修改其值的未知處理序存取。 因此，不論在命令列上指定的最佳化為何，都必須為 `volatile` 變數的每個指派或參考產生程式碼 (即使它並沒有任何作用)。  
  
     如果單獨使用 `volatile`，則會假設為 `int`。 `volatile` 類型指定名稱可以用來提供可靠的特殊記憶體位置存取。 使用 `volatile` 搭配可供訊號處理常式、同時執行的程式或特殊硬體 (例如，記憶體對應的 I/O 控制暫存器) 存取或修改的資料物件。 您可以將變數的存留期宣告為 `volatile`，或是將單一參考轉型為 `volatile`。  
  
-   項目可以同時是 **const** 與 `volatile`，在這種情況下，項目就無法由自己的程式合法修改，但是可以由某個非同步處理序進行修改。  
  
## <a name="see-also"></a>另請參閱  
 [宣告和類型](../c-language/declarations-and-types.md)