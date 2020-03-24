---
title: 編譯器警告 (層級 1) C4237
ms.date: 11/04/2016
f1_keywords:
- C4237
helpviewer_keywords:
- C4237
ms.assetid: f2e86c4b-80d8-460e-9429-83c5f3f5d7ca
ms.openlocfilehash: 31ceb972edf975055f930d4ff70a6663a5760922
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80163254"
---
# <a name="compiler-warning-level-1-c4237"></a>編譯器警告 (層級 1) C4237

尚未支援 ' 關鍵字 ' 關鍵字，但保留供日後使用

C++規格中的關鍵字不會在 Microsoft C++編譯器中執行，但關鍵字無法當做使用者定義的符號使用。

下列範例會產生 C4237：

```cpp
// C4237.cpp
// compile with: /W1 /c
int export;   // C4237
```
