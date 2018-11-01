---
title: 編譯器錯誤 C2414
ms.date: 11/04/2016
f1_keywords:
- C2414
helpviewer_keywords:
- C2414
ms.assetid: bbe94e03-862e-4990-b15e-544ae464727d
ms.openlocfilehash: 84fa715c8bd567770f361552e203a37c44ffdde4
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50451047"
---
# <a name="compiler-error-c2414"></a>編譯器錯誤 C2414

不合法的運算元數目

### <a name="to-fix-by-checking-the-following-possible-causes"></a>透過檢查下列可能原因進行修正

1. Opcode 不支援使用的運算元數目。 請檢查組件語言參考手冊，以判斷正確的運算元數目。

1. 較新的處理器支援不同數目的運算元使用指示。 調整[/arch （最小 CPU 架構）](../../build/reference/arch-minimum-cpu-architecture.md)選項可使用較新的處理器。