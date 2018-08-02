---
title: 終止處理常式的限制 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- termination handlers [C++], limitations
- restrictions, termination handlers
- try-catch keyword [C++], termination handlers
ms.assetid: 8b1cb481-303f-4e79-b409-57a002a9fa9e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 3ae16363956afc7cca853307ef2888846a02864d
ms.sourcegitcommit: 51f804005b8d921468775a0316de52ad39b77c3e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/02/2018
ms.locfileid: "39461766"
---
# <a name="restrictions-on-termination-handlers"></a>終止處理常式的限制
您無法使用**goto**陳述式跳入 **__try**陳述式區塊或 **__finally**陳述式區塊。 您必須改為透過一般控制流程進入陳述式區塊。 (您可以不過，跳出 **__try**陳述式區塊。)此外，您無法巢狀處理的例外狀況處理常式或終止處理常式內 **__finally**區塊。  
  
 此外，終止處理常式中允許的某些類型程式碼會產生可疑的結果，因此使用這類程式碼時應特別小心 (如果一定要的話)。 其中一個是**goto**陳述式會跳出 **__finally**陳述式區塊。 如果區塊在正常終止的過程中執行，則不會發生異常狀況。 但是，如果系統回溯堆疊，則該回溯會停止，而且目前函式會取得控制項，就如同從未發生異常終止一般。  
  
 A**會傳回**內的陳述式 **__finally**陳述式區塊大致上會呈現相同的情況。 控制項會返回包含終止處理常式之函式的立即呼叫者。 如果系統回溯堆疊，這個處理序就會停止，而且程式會繼續執行，就如同從未引發例外狀況一般。  
  
## <a name="see-also"></a>另請參閱  
 [撰寫終止處理常式](../cpp/writing-a-termination-handler.md)   
 [結構化例外狀況處理 (C/C++)](../cpp/structured-exception-handling-c-cpp.md)