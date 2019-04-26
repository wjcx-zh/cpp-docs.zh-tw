---
title: 編譯器警告 (層級 1) C4006
ms.date: 11/04/2016
f1_keywords:
- C4006
helpviewer_keywords:
- C4006
ms.assetid: f1a59819-0fd2-4361-8e3a-99e4b514b8e1
ms.openlocfilehash: 97f50bdf4454a284953bd70e83574f5d0a86d1e3
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62187283"
---
# <a name="compiler-warning-level-1-c4006"></a>編譯器警告 (層級 1) C4006

\#undef 必須是識別項

`#undef` 指示詞未指定要取消定義的識別項。 已忽略指示詞。 若要解決這項警告，請務必指定識別項。 下列範例會產生 C4006：

```
// C4006.cpp
// compile with: /W1
#undef   // C4006

// try..
// #undef TEST

int main() {
}
```