---
title: 編譯器錯誤 C2415
ms.date: 11/04/2016
f1_keywords:
- C2415
helpviewer_keywords:
- C2415
ms.assetid: f225c913-2bea-46b1-b096-3d358ac94a15
ms.openlocfilehash: 81e2da31b39b323919132ae86cd365d9c119be32
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62402953"
---
# <a name="compiler-error-c2415"></a>編譯器錯誤 C2415

不適當的運算元類型

Opcode 不會使用此類型的運算元。

### <a name="to-fix-by-checking-the-following-possible-causes"></a>透過檢查下列可能原因進行修正

1. Opcode 不支援使用的運算元數目。 請檢查組件語言參考手冊，以判斷正確的運算元數目。

1. 較新的處理器支援其他類型的指示。 調整[/arch （最小 CPU 架構）](../../build/reference/arch-minimum-cpu-architecture.md)選項可使用較新的處理器。