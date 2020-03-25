---
title: 編譯器警告 (層級 2) C4302
ms.date: 11/04/2016
f1_keywords:
- C4302
helpviewer_keywords:
- C4302
ms.assetid: f5e1c939-e134-4cca-ba1e-9b15a81549ae
ms.openlocfilehash: 98a489e92633af5cb8e125bfd7bafc4d872baebd
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80161941"
---
# <a name="compiler-warning-level-2-c4302"></a>編譯器警告 (層級 2) C4302

' 轉換 '：從 ' type 1 ' 截斷至 ' type 2 '

編譯器偵測到從較大的類型轉換成較小的類型。 資訊可能會遺失。

此警告預設為關閉。 如需詳細資訊，請參閱 [預設為關閉的編譯器警告](../../preprocessor/compiler-warnings-that-are-off-by-default.md) 。

下列範例會產生 C4302：

```cpp
// C4302.cpp
// compile with: /W2
#pragma warning(default : 4302)
int main() {
   int i;
   char c = (char) &i;     // C4302
   short s = (short) &i;   // C4302
}
```
