---
title: "exit 函式 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: Exit
dev_langs: C++
helpviewer_keywords: exit function
ms.assetid: 26ce439f-81e2-431c-9ff8-a09a96f32127
caps.latest.revision: "6"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: e4a1ee1a533309dfedce139efc7c6db1f41653a6
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/24/2017
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