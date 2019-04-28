---
title: 編譯器錯誤 C2474
ms.date: 11/04/2016
f1_keywords:
- C2474
helpviewer_keywords:
- C2474
ms.assetid: 64e6c61e-6e77-480e-bcf0-b30a2fc482ac
ms.openlocfilehash: c49f38b828a41c72135ba9182d4d0f5eee4df1de
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62350880"
---
# <a name="compiler-error-c2474"></a>編譯器錯誤 C2474

'keyword'：遺漏相鄰的分號，可能是關鍵字或識別項。

編譯器預期找到分號，且無法判定您的意圖。 加入分號以解決此錯誤。

## <a name="example"></a>範例

下列範例會產生 C2474：

```
// C2474.cpp
// compile with: /clr /c

ref class A {
   ref class B {}
   property int i;   // C2474 error
};

// OK
ref class B {
   ref class D {};
   property int i;
};

ref class E {
   ref class F {} property;
   int i;
};
```