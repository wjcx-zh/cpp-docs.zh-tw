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
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 093400e5d98b0b5e0336c2f640ed0937bdb157b9
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="overview-of-functions"></a>函式概觀
函式必須具有定義，而且應該具有宣告，不過，如果宣告在呼叫函式之前出現，則定義可以做為宣告。 函式定義包括函式主體，也就是呼叫函式時執行的程式碼。  
  
 函式宣告會為程式中其他位置定義的函式建立名稱、傳回類型和屬性。 函式宣告必須在函式呼叫之前。 這就是為什麼包含執行階段函式宣告的標頭檔會包括在您的程式碼中，並且位於執行階段函式呼叫之前。 如果宣告包含有關參數類型和數目的資訊，則宣告為原型。 如需詳細資訊，請參閱[函式原型](../c-language/function-prototypes.md)。  
  
 編譯器會使用原型比較後續函式呼叫中的引數類型與函式的參數，並且在必要時將引數類型轉換成參數的類型。  
  
 函式呼叫會將執行控制項從發出呼叫的函式傳遞至所呼叫的函式。 引數 (如果有的話) 會以傳值的方式傳遞至所呼叫的函式。 在所呼叫函式中執行 `return` 陳述式會將控制項傳回發出呼叫的函式，而且可能包含值。  
  
## <a name="see-also"></a>請參閱  
 [函式](../c-language/functions-c.md)