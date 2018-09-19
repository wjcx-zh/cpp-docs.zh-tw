---
title: 編譯器警告 （層級 4） C4289 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4289
dev_langs:
- C++
helpviewer_keywords:
- C4289
ms.assetid: 0dbd2863-4cde-4e16-894b-104a2d5fa724
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 35cb22c767c0ea64a1536bd4d02ad8653bb94250
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46102836"
---
# <a name="compiler-warning-level-4-c4289"></a>編譯器警告 (層級 4) C4289

使用非標準的擴充：'var' : 在 for-loop 範圍外使用 for-loop 中所宣告的迴圈控制變數

進行編譯時[/Ze](../../build/reference/za-ze-disable-language-extensions.md)並 **/zc: forscope-**，在宣告的變數[的](../../cpp/for-statement-cpp.md)之後已使用迴圈**的**-迴圈範圍。

請參閱[/zc: forscope](../../build/reference/zc-forscope-force-conformance-in-for-loop-scope.md)如需如何指定中的標準行為**如**迴圈是以 **/Ze**。

此警告預設為關閉。 如需詳細資訊，請參閱 [預設為關閉的編譯器警告](../../preprocessor/compiler-warnings-that-are-off-by-default.md) 。

下列範例會產生 C4289:

```
// C4289.cpp
// compile with: /W4 /Zc:forScope-
#pragma warning(default:4289)
int main() {
   for (int i = 0 ; ; )   // C4289
      break;
   i++;
}
```