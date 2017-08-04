---
title: "函式概觀 | Microsoft Docs"
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
- functions [C++]
- control flow, function calls
ms.assetid: b6f4637f-02b9-49d8-8601-1f886bd2cfb9
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
ms.openlocfilehash: 16612a32a0e5cb2294f4b74f46c14c206c1cbcbc
ms.contentlocale: zh-tw
ms.lasthandoff: 05/18/2017

---
# <a name="overview-of-functions"></a>函式概觀
函式必須具有定義，而且應該具有宣告，不過，如果宣告在呼叫函式之前出現，則定義可以做為宣告。 函式定義包括函式主體，也就是呼叫函式時執行的程式碼。  
  
 函式宣告會為程式中其他位置定義的函式建立名稱、傳回類型和屬性。 函式宣告必須在函式呼叫之前。 這就是為什麼包含執行階段函式宣告的標頭檔會包括在您的程式碼中，並且位於執行階段函式呼叫之前。 如果宣告包含有關參數類型和數目的資訊，則宣告為原型。 如需詳細資訊，請參閱[函式原型](../c-language/function-prototypes.md)。  
  
 編譯器會使用原型比較後續函式呼叫中的引數類型與函式的參數，並且在必要時將引數類型轉換成參數的類型。  
  
 函式呼叫會將執行控制項從發出呼叫的函式傳遞至所呼叫的函式。 引數 (如果有的話) 會以傳值的方式傳遞至所呼叫的函式。 在所呼叫函式中執行 `return` 陳述式會將控制項傳回發出呼叫的函式，而且可能包含值。  
  
## <a name="see-also"></a>另請參閱  
 [函式](../c-language/functions-c.md)
