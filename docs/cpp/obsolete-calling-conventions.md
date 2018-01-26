---
title: "過時呼叫慣例 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- __fortran
- __pascal
- __syscall
dev_langs: C++
helpviewer_keywords:
- WINAPI [C++]
- __syscall keyword [C++]
- __pascal keyword [C++]
- __fortran keyword [C++]
- calling conventions, obsolete
ms.assetid: a91fc665-034a-48ce-b6bd-d27125f308a7
caps.latest.revision: "7"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: ad065eb3f35080ff2e5743c0259b20ba72ee6175
ms.sourcegitcommit: 9a0a287d6940591523af959ebdac5affa36220da
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/25/2018
---
# <a name="obsolete-calling-conventions"></a>過時呼叫慣例
## <a name="microsoft-specific"></a>Microsoft 特定的  
 **__Pascal**， **__fortran**，和**__syscall**不再支援的呼叫慣例。 您可以使用其中一種支援的呼叫慣例和適當的連結器選項模擬其功能。  
  
 \<windows.h > 現在支援**WINAPI**巨集，它會轉譯為適合目標的呼叫慣例。 使用**WINAPI**您先前曾經**PASCAL**或**__far \__pascal**。  
  
**結束 Microsoft 特定的**  
  
## <a name="see-also"></a>請參閱  
 [引數傳遞和命名慣例](../cpp/argument-passing-and-naming-conventions.md)