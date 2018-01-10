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
ms.openlocfilehash: 325a9a98ec536eaabedef3a93fbe38ccc2016cd9
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="obsolete-calling-conventions"></a>過時呼叫慣例
## <a name="microsoft-specific"></a>Microsoft 特定的  
 **__Pascal**， **__fortran**，和**__syscall**不再支援的呼叫慣例。 您可以使用其中一種支援的呼叫慣例和適當的連結器選項模擬其功能。  
  
 WINDOWS。H 現在支援**WINAPI**巨集，它會轉譯為適合目標的呼叫慣例。 使用**WINAPI**您先前曾經**PASCAL**或**__far \__pascal**。  
  
**結束 Microsoft 特定的**  
  
## <a name="see-also"></a>請參閱  
 [引數傳遞和命名慣例](../cpp/argument-passing-and-naming-conventions.md)