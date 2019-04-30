---
title: 編譯器錯誤 C3824
ms.date: 11/04/2016
f1_keywords:
- C3824
helpviewer_keywords:
- C3824
ms.assetid: b6c6adf1-0a29-401c-a06e-616fd50d4c37
ms.openlocfilehash: d7c55ede285d027b1a65b33adbf6407df243f068
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62390603"
---
# <a name="compiler-error-c3824"></a>編譯器錯誤 C3824

'member': 此類型不能出現在此內容 （函式參數、 傳回型別或靜態成員）

Pin 指標不可以是函式參數、 傳回型別，或宣告`static`。

## <a name="example"></a>範例

下列範例會產生 C3824:

```
// C3824a.cpp
// compile with: /clr /c
void func() {
   static pin_ptr<int> a; // C3824
   pin_ptr<int> b; // OK
}
```
