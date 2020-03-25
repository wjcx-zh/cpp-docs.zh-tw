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
ms.openlocfilehash: 156482a395c7dfc8711e273141a09a37ea3e135d
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80188554"
---
# <a name="obsolete-calling-conventions"></a>過時呼叫慣例

**Microsoft 專屬**

不再支援 **__pascal**、 **__fortran**和 **__syscall**呼叫慣例。 您可以使用其中一種支援的呼叫慣例和適當的連結器選項模擬其功能。

\<的 windows .h > 現在支援 WINAPI 宏，它會轉譯為適合目標的呼叫慣例。 使用您先前使用 PASCAL 或 **__far \__pascal**的 WINAPI。

**END Microsoft 特定的**

## <a name="see-also"></a>另請參閱

[引數傳遞和命名慣例](../cpp/argument-passing-and-naming-conventions.md)
