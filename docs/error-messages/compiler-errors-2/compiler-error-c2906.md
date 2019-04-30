---
title: 編譯器錯誤 C2906
ms.date: 11/04/2016
f1_keywords:
- C2906
helpviewer_keywords:
- C2906
ms.assetid: 30f652f1-6af6-4a2f-a69e-a1a4876cc8c6
ms.openlocfilehash: 621b31cf362c1dcc740390cf9e405b7da3f05da8
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62378514"
---
# <a name="compiler-error-c2906"></a>編譯器錯誤 C2906

'specialization': 明確特製化必須有 'template<>'

您必須使用新語法的樣板的明確特製化。

下列範例會產生 C2906:

```
// C2906.cpp
// compile with: /c
template<class T> class X{};   // primary template
class X<int> { }   // C2906
template<> class X<int> { };   // new syntax
```