---
title: 編譯器錯誤 C2415
ms.date: 11/04/2016
f1_keywords:
- C2415
helpviewer_keywords:
- C2415
ms.assetid: f225c913-2bea-46b1-b096-3d358ac94a15
ms.openlocfilehash: a0cdd528eca8ea267c62e6d44752d29ae16830c4
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80205617"
---
# <a name="compiler-error-c2415"></a>編譯器錯誤 C2415

不正確的運算元類型

Opcode 不會使用此類型的運算元。

### <a name="to-fix-by-checking-the-following-possible-causes"></a>透過檢查下列可能原因進行修正

1. Opcode 不支援使用的運算元數目。 檢查元件語言參考手冊，以判斷正確的運算元數目。

1. 較新的處理器支援具有其他類型的指令。 調整 [ [/arch （最小 CPU 架構）](../../build/reference/arch-minimum-cpu-architecture.md) ] 選項，以使用較新的處理器。
