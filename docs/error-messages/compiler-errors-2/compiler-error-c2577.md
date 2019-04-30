---
title: 編譯器錯誤 C2577
ms.date: 11/04/2016
f1_keywords:
- C2577
helpviewer_keywords:
- C2577
ms.assetid: fc79ef83-8362-40a2-9257-8037c3195ce4
ms.openlocfilehash: 4406aa90b26bc517308132ae9cccd003d44a9aad
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62408455"
---
# <a name="compiler-error-c2577"></a>編譯器錯誤 C2577

'member': 解構函式/完成項不能有傳回型別

解構函式或完成項無法傳回值為`void`或任何其他類型。 移除`return`解構函式定義中的陳述式。

## <a name="example"></a>範例

下列範例會產生 C2577。

```
// C2577.cpp
// compile with: /c
class A {
public:
   A() {}
   ~A(){
      return 0;   // C2577
   }
};
```