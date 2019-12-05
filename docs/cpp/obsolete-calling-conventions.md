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
ms.openlocfilehash: 7f059afe02cbbad77920fd8c4a0e6cb7c958e992
ms.sourcegitcommit: a6d63c07ab9ec251c48bc003ab2933cf01263f19
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/05/2019
ms.locfileid: "74857355"
---
# <a name="obsolete-calling-conventions"></a>過時呼叫慣例

**Microsoft 專屬**

不再支援 **__pascal**、 **__fortran**和 **__syscall**呼叫慣例。 您可以使用其中一種支援的呼叫慣例和適當的連結器選項模擬其功能。

\<的 windows .h > 現在支援 WINAPI 宏，它會轉譯為適合目標的呼叫慣例。 使用您先前使用 PASCAL 或 **__far \__pascal**的 WINAPI。

**結束 Microsoft 專屬**

## <a name="see-also"></a>請參閱

[引數傳遞和命名慣例](../cpp/argument-passing-and-naming-conventions.md)