---
title: 過時呼叫慣例 |Microsoft Docs
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
ms.openlocfilehash: 922103e808541e2829350749a04d6004ba36577f
ms.sourcegitcommit: 2b9e8af9b7138f502ffcba64e2721f7ef52af23b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/01/2018
ms.locfileid: "39403416"
---
# <a name="obsolete-calling-conventions"></a>過時呼叫慣例
## <a name="microsoft-specific"></a>Microsoft 特定的  
 **__Pascal**， **__fortran**，並 **__syscall**呼叫慣例已不再支援。 您可以使用其中一種支援的呼叫慣例和適當的連結器選項模擬其功能。  
  
 \<windows.h > 現在支援 WINAPI 巨集，這會轉譯成適當的呼叫慣例的目標。 使用先前使用 pascal 命名法的 WINAPI 或 **__far \__pascal**。  
  
**結束 Microsoft 專屬**  
  
## <a name="see-also"></a>另請參閱  
 [引數傳遞和命名慣例](../cpp/argument-passing-and-naming-conventions.md)