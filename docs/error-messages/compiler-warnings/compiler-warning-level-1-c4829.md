---
title: 編譯器警告 (層級 1) C4829
ms.date: 11/04/2016
f1_keywords:
- C4829
helpviewer_keywords:
- C4829
ms.assetid: 4ffabe2b-2ddc-4c52-8564-d1355c93cfa6
ms.openlocfilehash: 1afb29b10352150cac2969849979fb5b5e2b8719
ms.sourcegitcommit: afd6fac7c519dbc47a4befaece14a919d4e0a8a2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/10/2018
ms.locfileid: "51522554"
---
# <a name="compiler-warning-level-1-c4829"></a>編譯器警告 (層級 1) C4829

函式 main 的參數可能不正確。 請考慮 ' intmain (platform:: array\<platform:: string ^ > ^ argv)'

特定函數 (例如 main) 無法取得參考型別參數。 繼續編譯時，產生的映像可能不會執行。

下列範例會產生 C4829：

```
// C4829.cpp
// compile by using: cl /EHsc /ZW /W4 /c C4829.cpp
int main(Platform::String ^ s) {}   // C4829
```