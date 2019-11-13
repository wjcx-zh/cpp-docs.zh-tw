---
title: 編譯器警告（層級2） C4244
ms.date: 11/04/2016
f1_keywords:
- C4244
helpviewer_keywords:
- C4244
ms.assetid: 2c19d157-21d1-42c2-a6c0-3f30f2ce3813
ms.openlocfilehash: 43d8a992801d556ce85577f5f9da1bec584cb173
ms.sourcegitcommit: 458dcc794e3841919c01a3a5ff6b9a3767f8861b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/13/2019
ms.locfileid: "74052121"
---
# <a name="compiler-warning-level-2-c4244"></a>編譯器警告（層級2） C4244

' argument '：從 ' type1 ' 轉換成 ' type2 '，資料可能遺失

浮點類型已轉換成整數類型。  資料可能會遺失。

如果出現 C4244，您應變更程式以使用相容的類型，或在您的程式碼中加入某些邏輯，以確保可能值的範圍一定會與您所使用的類型相容。

C4244 也可以在層級3和4引發。如需詳細資訊，請參閱[編譯器警告（層級3和4） C4244](../../error-messages/compiler-warnings/compiler-warning-levels-3-and-4-c4244.md) 。

## <a name="example"></a>範例

下列範例會產生 C4244：

```cpp
// C4244_level2.cpp
// compile with: /W2

int f(int x){ return 0; }
int main() {
   double x = 10.1;
   int i = 10;
   return (f(x));   // C4244
   // try the following line instead
   // return (f(i));
}
```