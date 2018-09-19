---
title: 編譯器錯誤 C2847 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2847
dev_langs:
- C++
helpviewer_keywords:
- C2847
ms.assetid: 9ad9a0e0-8b16-49d9-a5be-f8eda2372aa9
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 41e3b49c509240fd0d782aacaa9fae836b62702a
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46054437"
---
# <a name="compiler-error-c2847"></a>編譯器錯誤 C2847

無法將 sizeof 套用於 Managed 或 WinRT 型別 'class'

[Sizeof](../../cpp/sizeof-operator.md)運算子在編譯時期取得物件值。 Managed 或 WinRT 型別、介面或實值型別的大小是動態的，因此無法在編譯時間得知。

例如，下列範例會產生 C2847：

```
// C2847.cpp
// compile with: /clr
ref class A {};

int main() {
   A ^ xA = gcnew A;
   sizeof(*xA);   // C2847 cannot use sizeof on managed object
}
```
