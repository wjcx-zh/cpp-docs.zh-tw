---
title: 編譯器錯誤 C2755
ms.date: 11/04/2016
f1_keywords:
- C2755
helpviewer_keywords:
- C2755
ms.assetid: 8ee4eeb6-4757-4efe-9100-38ff4a96f1de
ms.openlocfilehash: fcd4bb5d49f6f6e807ad240c377debb220138c93
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/03/2019
ms.locfileid: "74759551"
---
# <a name="compiler-error-c2755"></a>編譯器錯誤 C2755

' param '：部分特製化的非類型參數必須是簡單的識別碼

非型別參數必須是簡單的識別碼，編譯器在編譯時期可以解析成單一識別碼或常數值的東西。

下列範例會產生 C2755：

```cpp
// C2755.cpp
template<int I, int J>
struct A {};

template<int I>
struct A<I,I*5> {};   // C2755
// try the following line instead
// struct A<I,5> {};
```
