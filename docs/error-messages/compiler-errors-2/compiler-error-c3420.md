---
title: 編譯器錯誤 C3420
ms.date: 11/04/2016
f1_keywords:
- C3420
helpviewer_keywords:
- C3420
ms.assetid: 99b53c77-f36b-4574-9199-b53111becccb
ms.openlocfilehash: 5e165a0c181bc27adebe75111050f49130305693
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/03/2019
ms.locfileid: "74756249"
---
# <a name="compiler-error-c3420"></a>編譯器錯誤 C3420

'finalizer'：完成項不可為虛擬

完成項不可為虛擬，否則無法從它的封入類型進行呼叫。 因此，宣告虛擬完成項會造成錯誤。

如需詳細資訊，請參閱[如何：定義和使用類別和結構（C++/cli）中的析構函數和完成項](../../dotnet/how-to-define-and-consume-classes-and-structs-cpp-cli.md#BKMK_Destructors_and_finalizers)。

## <a name="example"></a>範例

下列範例會產生 C3420：

```cpp
// C3420.cpp
// compile with: /clr /c
ref class R {
   virtual !R() {}   // C3420
};
```
