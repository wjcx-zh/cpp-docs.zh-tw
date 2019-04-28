---
title: 過時呼叫慣例
ms.date: 11/04/2016
f1_keywords:
- __fortran
- __pascal
- __syscall
helpviewer_keywords:
- WINAPI [C++]
- __syscall keyword [C++]
- __pascal keyword [C++]
- __fortran keyword [C++]
- calling conventions, obsolete
ms.assetid: a91fc665-034a-48ce-b6bd-d27125f308a7
ms.openlocfilehash: 86c75c779158d9f191dd015410cf16c9ce25690d
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62245016"
---
# <a name="obsolete-calling-conventions"></a>過時呼叫慣例

## <a name="microsoft-specific"></a>Microsoft 特定的

**__Pascal**， **__fortran**，並 **__syscall**呼叫慣例已不再支援。 您可以使用其中一種支援的呼叫慣例和適當的連結器選項模擬其功能。

\<windows.h > 現在支援 WINAPI 巨集，這會轉譯成適當的呼叫慣例的目標。 使用先前使用 pascal 命名法的 WINAPI 或 **__far \__pascal**。

**結束 Microsoft 專屬**

## <a name="see-also"></a>另請參閱

[引數傳遞和命名慣例](../cpp/argument-passing-and-naming-conventions.md)