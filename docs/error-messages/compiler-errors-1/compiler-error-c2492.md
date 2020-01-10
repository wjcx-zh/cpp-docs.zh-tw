---
title: 編譯器錯誤 C2492
ms.date: 11/04/2016
f1_keywords:
- C2492
helpviewer_keywords:
- C2492
ms.assetid: 8c44c9bb-c366-4fe5-a0ab-882e38608aaa
ms.openlocfilehash: fd52b434f86bdc93124c6005bbf7fadad3cb56b2
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/03/2019
ms.locfileid: "74757055"
---
# <a name="compiler-error-c2492"></a>編譯器錯誤 C2492

'*variable*'：具有線程儲存期的資料可能沒有 dll 介面

變數是以[thread](../../cpp/thread.md)屬性和 DLL 介面來宣告。 在執行時間之前，不會知道 `thread` 變數的位址，因此無法將它連結至 DLL 匯入或匯出。

下列範例會產生 C2492：

```cpp
// C2492.cpp
// compile with: /c
class C {
public:
   char   ch;
};

__declspec(dllexport) __declspec(thread) C c_1;   // C2492
__declspec(thread) C c_1;   // OK
```
