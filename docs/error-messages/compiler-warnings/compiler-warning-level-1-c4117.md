---
title: 編譯器警告 (層級 1) C4117
ms.date: 11/04/2016
f1_keywords:
- C4117
helpviewer_keywords:
- C4117
ms.assetid: c45aa281-4cc1-4dfd-bd32-bd7a60ddd577
ms.openlocfilehash: 2474645a555748b559b1661a2b5327ca1b83e534
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80176374"
---
# <a name="compiler-warning-level-1-c4117"></a>編譯器警告 (層級 1) C4117

巨集名稱 'name' 為保留字; 忽略 'Command'

### <a name="to-fix-by-checking-the-following-possible-causes"></a>透過檢查下列可能原因進行修正

1. 嘗試定義或取消定義預先定義的巨集。

1. 嘗試定義或取消定義前置處理器運算子 **defined**。

下列範例會產生 C4117：

```cpp
// C4117.cpp
// compile with: /W1
#define __FILE__ test         // C4117. __FILE__ is a predefined macro
#define ValidMacroName test   // ok

int main() {
}
```
