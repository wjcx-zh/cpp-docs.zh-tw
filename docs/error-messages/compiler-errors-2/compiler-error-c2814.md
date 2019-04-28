---
title: 編譯器錯誤 C2814
ms.date: 11/04/2016
f1_keywords:
- C2814
helpviewer_keywords:
- C2814
ms.assetid: 7d165136-a08b-4497-a76d-60a21bb19404
ms.openlocfilehash: 6562e8a0968f83a0e7e968b538b4d94dc1047fa5
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62329552"
---
# <a name="compiler-error-c2814"></a>編譯器錯誤 C2814

'member'：原生類型不可以巢狀方式置於 Managed 或 WinRT 類型 'type' 中

## <a name="example"></a>範例

原生類型不可以巢狀方式置於 CLR 或 WinRT 類型中。 下列範例會產生 C2814，並示範如何修正此問題。

```
// C2814.cpp
// compile with: /clr /c
ref class A {
   class B {};   // C2814
   ref class C {};   // OK
};
```
