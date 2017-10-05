---
title: "例外狀況處理的時機： 摘要 |Microsoft 文件"
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
- sequence
- sequence, of handlers
- exception handling, timing
- SETJMPEX.H
- termination handlers, timing
- SETJMP.H
- handlers, order of exception
- structured exception handling, timing
ms.assetid: 5d1da546-73fd-4673-aa1a-7ac0f776c420
caps.latest.revision: 6
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
ms.openlocfilehash: 0ba1075095381229667c7164aa7de7f3e4537486
ms.contentlocale: zh-tw
ms.lasthandoff: 09/25/2017

---
# <a name="timing-of-exception-handling-a-summary"></a>例外狀況處理的時機：摘要
無論 `__try` 陳述式區塊以何種方式終止，都會執行終止處理常式。 原因包括跳出 `__try` 區塊、`longjmp` 陳述式將控制權傳輸到區塊外部，以及因為進行例外狀況處理而回溯堆疊。  
  
> [!NOTE]
>  Visual C++ 支援兩種形式的 `setjmp` 和 `longjmp` 陳述式。 快速版本會略過終止處理，但是會更有效率。 若要使用這個版本，請包含檔案 SETJMP.H。 另一個版本支援終止處理，如先前段落中所述。 若要使用這個版本，請包含檔案 SETJMPEX.H。 快速版本的效能提升取決於硬體組態。  
  
 作業系統會先依適當的順序執行所有終止處理常式，型執行其他程式碼，包括例外狀況處理常式的主體。  
  
 當導致中斷的原因是來自例外狀況時，系統必須先執行一個或多個例外狀況處理常式的篩選條件部分，再決定要終止哪個部分。 事件的順序為：  
  
1.  引發例外狀況。  
  
2.  系統會查看作用中例外狀況處理常式的階層架構，並執行具有最高優先順序之處理常式的篩選條件，依照區塊和函式呼叫，這會是最近安裝且位於巢狀最深處的例外狀況處理常式。  
  
3.  如果這個篩選條件會傳遞控制權 (傳回 0)，處理序會繼續執行，直到找到不會傳遞控制權的篩選條件。  
  
4.  如果這個篩選條件會傳回-1，則執行會持續引發例外狀況，而不會終止。  
  
5.  如果篩選條件傳回 1，則會發生下列事件：  
  
    -   系統會回溯堆疊、清除目前執行之程式碼 (即引發例外狀況的位置) 的所有堆疊框架，而包含例外狀況處理常式的堆疊框架會取得控制權。  
  
    -   回溯堆疊時，會執行堆疊上的每個終止處理常式。  
  
    -   例外狀況處理常式本身會執行。  
  
    -   控制權會傳遞給這個例外狀況處理常式結尾後方的程式碼。  
  
## <a name="see-also"></a>另請參閱  
 [撰寫終止處理常式](../cpp/writing-a-termination-handler.md)   
 [結構化例外狀況處理 (C/C++)](../cpp/structured-exception-handling-c-cpp.md)
