---
title: 編譯器錯誤 C2414
ms.date: 11/04/2016
f1_keywords:
- C2414
helpviewer_keywords:
- C2414
ms.assetid: bbe94e03-862e-4990-b15e-544ae464727d
ms.openlocfilehash: fbe627a57e5defc499a4bc5d463e0bf33494acba
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80205656"
---
# <a name="compiler-error-c2414"></a>編譯器錯誤 C2414

不合法的運算元數目

### <a name="to-fix-by-checking-the-following-possible-causes"></a>透過檢查下列可能原因進行修正

1. Opcode 不支援使用的運算元數目。 檢查元件語言參考手冊，以判斷正確的運算元數目。

1. 較新的處理器支援具有不同運算元數目的指令。 調整 [ [/arch （最小 CPU 架構）](../../build/reference/arch-minimum-cpu-architecture.md) ] 選項，以使用較新的處理器。
