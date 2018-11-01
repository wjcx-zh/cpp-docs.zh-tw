---
title: 編譯器錯誤 C2480
ms.date: 11/04/2016
f1_keywords:
- C2480
helpviewer_keywords:
- C2480
ms.assetid: 1a58d1c2-971b-4084-96fa-f94aa51c02f1
ms.openlocfilehash: 90016b65d4ddd58da3fb3c5ab6d81322dc0ef394
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50566721"
---
# <a name="compiler-error-c2480"></a>編譯器錯誤 C2480

'identifier': 'thread' 只是對靜態延伸的資料項目有效

您無法使用`thread`自動變數、 靜態資料成員、 函式參數或函式宣告或定義的屬性。

使用`thread`全域變數、 靜態資料成員和只區域靜態變數的屬性。

下列範例會產生 C2480:

```
// C2480.cpp
// compile with: /c
__declspec( thread ) void func();   // C2480
__declspec( thread ) static int i;   // OK
```