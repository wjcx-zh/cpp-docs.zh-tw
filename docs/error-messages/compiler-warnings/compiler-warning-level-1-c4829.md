---
title: 編譯器警告 (層級 1) C4829
ms.date: 11/04/2016
f1_keywords:
- C4829
helpviewer_keywords:
- C4829
ms.assetid: 4ffabe2b-2ddc-4c52-8564-d1355c93cfa6
ms.openlocfilehash: a5c7cd062f22e9888e484f6d254fcf173cf83d1a
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80199377"
---
# <a name="compiler-warning-level-1-c4829"></a>編譯器警告 (層級 1) C4829

函式 main 的參數可能不正確。 請考慮 ' intmain （Platform：： Array\<Platform：： String ^ > ^ argv） '

特定函數 (例如 main) 無法取得參考型別參數。 繼續編譯時，產生的映像可能不會執行。

下列範例會產生 C4829：

```cpp
// C4829.cpp
// compile by using: cl /EHsc /ZW /W4 /c C4829.cpp
int main(Platform::String ^ s) {}   // C4829
```
