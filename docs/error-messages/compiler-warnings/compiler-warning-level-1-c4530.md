---
title: 編譯器警告（層級1） C4530
ms.date: 11/04/2016
f1_keywords:
- C4530
helpviewer_keywords:
- C4530
ms.assetid: a04dcdb2-84db-459d-9e5e-4e743887465f
ms.openlocfilehash: 3139d321bca64b9938badebdabccd3ca1eb96d11
ms.sourcegitcommit: e5192a25c084eda9eabfa37626f3274507e026b3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/12/2019
ms.locfileid: "73966267"
---
# <a name="compiler-warning-level-1-c4530"></a>編譯器警告（層級1） C4530

C++使用了例外狀況處理常式，但未啟用回溯語義。 指定/EHsc

C++已使用例外狀況處理，但未選取[/ehsc](../../build/reference/eh-exception-handling-model.md) 。

當/EHsc 選項尚未啟用時，在框架中具有自動儲存的物件會在執行擲回的函式與攔截擲回的函數之間，將不會終結。 不過，在**try**或**catch**區塊中建立了自動儲存的物件將會遭到終結。

下列範例會產生 C4530：

```cpp
// C4530.cpp
// compile with: /W1
int main() {
   try{} catch(int*) {}   // C4530
}
```

使用/EHsc 編譯範例以解決警告。