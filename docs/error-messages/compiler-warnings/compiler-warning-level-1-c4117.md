---
title: 編譯器警告 (層級 1) C4117
ms.date: 11/04/2016
f1_keywords:
- C4117
helpviewer_keywords:
- C4117
ms.assetid: c45aa281-4cc1-4dfd-bd32-bd7a60ddd577
ms.openlocfilehash: 97fd5703a744448db87634e313678cf4e824df7f
ms.sourcegitcommit: 0cfc43f90a6cc8b97b24c42efcf5fb9c18762a42
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/05/2019
ms.locfileid: "73626279"
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