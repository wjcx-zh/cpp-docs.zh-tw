---
title: 編譯器錯誤 C2768 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2768
dev_langs:
- C++
helpviewer_keywords:
- C2768
ms.assetid: a7f6047a-6a80-4737-ad5c-c12868639fb5
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 4c76173f99dbc2fb415b60212109242845501694
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46109102"
---
# <a name="compiler-error-c2768"></a>編譯器錯誤 C2768

'function': 明確範本引數的使用不正確

編譯器無法判斷是否應函式定義的函式樣板的明確特製化，或者函式定義原本應該用於新的函式。

一部分的編譯器一致性增強功能，Visual Studio.NET 2003年中引進這個錯誤。

下列範例會產生 C2768:

```
// C2768.cpp
template<typename T>
void f(T) {}

void f<int>(int) {}   // C2768

// an explicit specialization
template<>
void f<int>(int) {}

// global nontemplate function overload
void f(int) {}
```