---
title: 編譯器警告 (層級 4) C4189
ms.date: 11/04/2016
f1_keywords:
- C4189
helpviewer_keywords:
- C4189
ms.assetid: 7ad9242c-228e-4054-8244-5e914b618ef3
ms.openlocfilehash: 6463379529897598d560d6bcc22bd3a278a66477
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62401276"
---
# <a name="compiler-warning-level-4-c4189"></a>編譯器警告 (層級 4) C4189

'identifier' : 已初始化區域變數，但並未參考

變數已宣告並初始化，但未使用。

下列範例會產生 C4189：

```
// C4189.cpp
// compile with: /W4
int main() {
   int a = 1;   // C4189, remove declaration to resolve
}
```