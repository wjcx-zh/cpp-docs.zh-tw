---
title: "範圍和可視性 | Microsoft Docs"
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
- scope, levels
- visibility
- file scope [C++]
ms.assetid: a019eb7c-66ed-46a7-bc9f-89a963930a56
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
ms.translationtype: Human Translation
ms.sourcegitcommit: d6eb43b2e77b11f4c85f6cf7e563fe743d2a7093
ms.openlocfilehash: a9492fc16cb189d74e6f13a4bd02067638939868
ms.contentlocale: zh-tw
ms.lasthandoff: 05/18/2017

---
# <a name="scope-and-visibility"></a>範圍和可視性
識別項的「可視性」會判斷程式中可以參考的部分 (其「範圍」)。 識別項只有位在程式中其「範圍」所涵蓋的部分才顯示 (也就是可以使用)，該範圍可能限於該識別項出現的檔案、函式、區塊或函式原型 (依照由低到高增加的限制性)。 識別項的範圍是可以使用名稱的程式部分。 這個範圍有時稱為「語彙範圍」。 範圍可分為四種：函式、檔案、區塊和函式原型。  
  
 除了標籤之外，所有識別項的範圍都是由宣告發生所在的層級決定。 下列適用於每一種範圍的規則可管理程式內識別項的可視性：  
  
 檔案範圍  
 具有檔案範圍之識別項的宣告子或類型指定名稱會出現在任何區塊或參數清單之外，並且可在其宣告之後從轉譯單位中的任何位置存取。 具有檔案範圍的識別項名稱通常稱為「全域」或「外部」。 全域識別項的範圍是從其定義或宣告的位置開始，並且於轉譯單位的結尾終止。  
  
 函式範圍  
 標籤是唯一具有函式範圍的識別項類型。 標籤是藉由其在陳述式中的用法隱含宣告。 標籤名稱在函式內必須是唯一的  (如需標籤和標籤名稱的詳細資訊，請參閱 [goto 和標記陳述式](../c-language/goto-and-labeled-statements-c.md))。  
  
 區塊範圍  
 具有區塊範圍之識別項的宣告子或類型指定名稱會出現在區塊內，或是函式定義中的型式參數宣告清單內。 它的可見範圍是從其宣告或定義的位置開始，到包含其宣告或定義的區塊結尾為止。 其範圍僅限於該區塊以及該區塊中的任何巢狀區塊，並且在關閉相關聯區塊的大括號處結束。 這類識別項有時稱為「區域變數」。  
  
 函式原型範圍  
 具有函式原型範圍之識別項的宣告子或類型指定名稱，會出現在函式原型中的參數宣告清單內 (不屬於參數宣告的一部分)。 其範圍會在函式宣告子的結尾終止。  
  
 有關讓變數在其他原始程式檔中可見的適當宣告，將在[儲存類別](../c-language/c-storage-classes.md)中說明。 不過，在外部層級使用 **static** 儲存類別指定名稱宣告的變數和函式，只有在本身定義所在的原始程式碼內才可見。 所有其他函式都是全域可見。  
  
## <a name="see-also"></a>另請參閱  
 [存留期、範圍、可見度和連結](../c-language/lifetime-scope-visibility-and-linkage.md)
