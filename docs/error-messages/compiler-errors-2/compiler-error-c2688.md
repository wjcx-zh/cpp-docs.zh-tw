---
title: 編譯器錯誤 C2688
ms.date: 11/04/2016
f1_keywords:
- C2688
helpviewer_keywords:
- C2688
ms.assetid: 168c9e9d-8f65-4664-af86-db71d3e6ee46
ms.openlocfilehash: 5355abc603726eb1bacb7a22fa1095bf2d81c538
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62266279"
---
# <a name="compiler-error-c2688"></a>編譯器錯誤 C2688

'C2::fgrv': covariant 應傳回具有多個或不支援 varargs 函式的虛擬繼承

在視覺效果不支援 covariant 傳回型別C++函式時包含變數引數。

若要解決這個錯誤，請定義您的函式，使它們不使用變數引數或讓傳回的值相同的所有虛擬函式。

下列範例會產生 C2688:

```
// C2688.cpp
struct G1 {};
struct G2 {};
struct G3 : G1, G2 {};
struct G4 {};
struct G5 {};
struct G6 : G4, G5 {};
struct G7 : G3, G6 {};

struct C1 {
   virtual G4& fgrv(int,...);
};

struct C2 : C1 {
   virtual G7& fgrv(int,...);   // C2688, does not return G4&
};
```