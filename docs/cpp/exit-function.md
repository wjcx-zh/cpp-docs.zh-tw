---
title: "exit 函式 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- Exit
dev_langs:
- C++
helpviewer_keywords:
- exit function
ms.assetid: 26ce439f-81e2-431c-9ff8-a09a96f32127
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
ms.openlocfilehash: 240636bf7b6f10421c5d4ebd202a5fb3473a819d
ms.contentlocale: zh-tw
ms.lasthandoff: 09/25/2017

---
# <a name="exit-function"></a>exit 函式
**結束**函式，在標準 include 檔 STDLIB 中宣告。H，會終止 c + + 程式。  
  
 做為引數所提供的值**結束**傳回作業系統做為程式的傳回碼或結束代碼。 依照慣例，傳回碼為零，表示程式順利完成。  
  
> [!NOTE]
>  您可以使用 STDLIB.H 中定義的常數 `EXIT_FAILURE` 和 `EXIT_SUCCESS`，表示程式成功或失敗。  
  
 發出`return`陳述式從**主要**函式相當於呼叫**結束**函式傳回的值做為其引數。  
  
 如需詳細資訊，請參閱[結束](../c-runtime-library/reference/exit-exit-exit.md)中*執行階段程式庫參考*。  
  
## <a name="see-also"></a>另請參閱  
 [程式終止](../cpp/program-termination.md)
