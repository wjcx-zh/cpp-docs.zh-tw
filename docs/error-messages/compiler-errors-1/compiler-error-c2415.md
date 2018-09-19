---
title: 編譯器錯誤 C2415 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2415
dev_langs:
- C++
helpviewer_keywords:
- C2415
ms.assetid: f225c913-2bea-46b1-b096-3d358ac94a15
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: bd889880997828396521ddba638bb606552e7d92
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46112573"
---
# <a name="compiler-error-c2415"></a>編譯器錯誤 C2415

不適當的運算元類型

Opcode 不會使用此類型的運算元。

### <a name="to-fix-by-checking-the-following-possible-causes"></a>透過檢查下列可能原因進行修正

1. Opcode 不支援使用的運算元數目。 請檢查組件語言參考手冊，以判斷正確的運算元數目。

1. 較新的處理器支援其他類型的指示。 調整[/arch （最小 CPU 架構）](../../build/reference/arch-minimum-cpu-architecture.md)選項可使用較新的處理器。