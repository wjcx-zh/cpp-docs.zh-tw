---
title: 編譯器錯誤 C2755
ms.date: 11/04/2016
f1_keywords:
- C2755
helpviewer_keywords:
- C2755
ms.assetid: 8ee4eeb6-4757-4efe-9100-38ff4a96f1de
ms.openlocfilehash: c2238058dc4b7df6bbe33e98d6ccde996f36b782
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50570682"
---
# <a name="compiler-error-c2755"></a>編譯器錯誤 C2755

'param': 部分特製化的非類型參數必須是簡單的識別項

非類型參數必須是簡單的識別項，編譯器可以解決在編譯時期常值，或以單一識別項的項目。

下列範例會產生 C2755:

```
// C2755.cpp
template<int I, int J>
struct A {};

template<int I>
struct A<I,I*5> {};   // C2755
// try the following line instead
// struct A<I,5> {};
```