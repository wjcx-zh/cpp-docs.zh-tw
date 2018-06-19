---
title: 過時呼叫慣例 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- __fortran
- __pascal
- __syscall
dev_langs:
- C++
helpviewer_keywords:
- WINAPI [C++]
- __syscall keyword [C++]
- __pascal keyword [C++]
- __fortran keyword [C++]
- calling conventions, obsolete
ms.assetid: a91fc665-034a-48ce-b6bd-d27125f308a7
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 9d2a6188cf9d8c8283a6c03a2ca6c701e28baf0d
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
ms.locfileid: "32419842"
---
# <a name="obsolete-calling-conventions"></a>過時呼叫慣例
## <a name="microsoft-specific"></a>Microsoft 特定的  
 **__Pascal**， **__fortran**，和 **__syscall**不再支援的呼叫慣例。 您可以使用其中一種支援的呼叫慣例和適當的連結器選項模擬其功能。  
  
 \<windows.h > 現在支援**WINAPI**巨集，它會轉譯為適合目標的呼叫慣例。 使用**WINAPI**您先前曾經**PASCAL**或 **__far \__pascal**。  
  
**結束 Microsoft 特定的**  
  
## <a name="see-also"></a>另請參閱  
 [引數傳遞和命名慣例](../cpp/argument-passing-and-naming-conventions.md)