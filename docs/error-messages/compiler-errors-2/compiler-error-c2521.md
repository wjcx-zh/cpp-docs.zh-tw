---
title: 編譯器錯誤 C2521
ms.date: 11/04/2016
f1_keywords:
- C2521
helpviewer_keywords:
- C2521
ms.assetid: 6042821b-e345-4a54-a7e9-a2c9019ea016
ms.openlocfilehash: cabd13b3292995d2baa8c5c66e9bc9ee85118c44
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/03/2019
ms.locfileid: "74746444"
---
# <a name="compiler-error-c2521"></a>編譯器錯誤 C2521

函數不接受任何引數

您嘗試使用具有析構函數或完成項的引數。

如需詳細資訊，請參閱[析構函數和](../../dotnet/how-to-define-and-consume-classes-and-structs-cpp-cli.md#BKMK_Destructors_and_finalizers)完成項。

## <a name="example"></a>範例

下列範例會產生 C2521。

```cpp
// C2521.cpp
// compile with: /clr
ref class R {
protected:
   !R() {}

public:
   void CleanUp() {
      this->!R(4);   // C2521
      this->!R();   // OK
   }
};

int main() {
   R^ r = gcnew R();
   r->CleanUp();
}
```
