---
title: 編譯器錯誤 C2768
ms.date: 11/04/2016
f1_keywords:
- C2768
helpviewer_keywords:
- C2768
ms.assetid: a7f6047a-6a80-4737-ad5c-c12868639fb5
ms.openlocfilehash: 9c0fb8fb0a98830aaf061ba980e7bdd7903f25e1
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62257610"
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