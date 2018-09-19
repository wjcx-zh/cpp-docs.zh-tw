---
title: 編譯器錯誤 C2480 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2480
dev_langs:
- C++
helpviewer_keywords:
- C2480
ms.assetid: 1a58d1c2-971b-4084-96fa-f94aa51c02f1
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 8b5d8f80293c05b651ad01e725ae501288005dfe
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46102578"
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