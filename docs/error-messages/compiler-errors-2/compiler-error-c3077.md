---
title: 編譯器錯誤 C3077
ms.date: 11/04/2016
f1_keywords:
- C3077
helpviewer_keywords:
- C3077
ms.assetid: d9f3c619-d1e2-4656-81a5-a35a9586a7d4
ms.openlocfilehash: b2dfe4c17ee122baa8f648669f9080b28584a66f
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/03/2019
ms.locfileid: "74756730"
---
# <a name="compiler-error-c3077"></a>編譯器錯誤 C3077

'finalizer' : 完成項必須是參考類型的成員

您無法在原生或實值類型宣告完成項。

如需詳細資訊，請參閱[如何：定義和使用類別和結構（C++/cli）中的析構函數和完成項](../../dotnet/how-to-define-and-consume-classes-and-structs-cpp-cli.md#BKMK_Destructors_and_finalizers)。

## <a name="example"></a>範例

下列範例會產生 C3077。

```cpp
// C3077.cpp
// compile with: /clr /c
value struct vs {
   !vs(){}   // C3077
};

ref struct rs {
protected:
   !rs(){}   // OK
};
```
