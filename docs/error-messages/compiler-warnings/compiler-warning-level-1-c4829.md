---
title: 編譯器警告（層級1） C4829
ms.date: 11/04/2016
f1_keywords:
- C4829
helpviewer_keywords:
- C4829
ms.assetid: 4ffabe2b-2ddc-4c52-8564-d1355c93cfa6
ms.openlocfilehash: e8765f206d099f808ab261fbbde19273e46b5c90
ms.sourcegitcommit: 458dcc794e3841919c01a3a5ff6b9a3767f8861b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/13/2019
ms.locfileid: "74051247"
---
# <a name="compiler-warning-level-1-c4829"></a>編譯器警告（層級1） C4829

函式 main 的參數可能不正確。 請考慮 ' intmain （Platform：： Array\<Platform：： String ^ > ^ argv） '

特定函數 (例如 main) 無法取得參考型別參數。 繼續編譯時，產生的映像可能不會執行。

下列範例會產生 C4829：

```cpp
// C4829.cpp
// compile by using: cl /EHsc /ZW /W4 /c C4829.cpp
int main(Platform::String ^ s) {}   // C4829
```