---
title: 編譯器警告 (層級 1) C4674
ms.date: 11/04/2016
f1_keywords:
- C4674
helpviewer_keywords:
- C4674
ms.assetid: 638dae0b-b82c-4865-9599-72630827ca09
ms.openlocfilehash: f7db2f37224a8defffb545b0cfaf018fd4654227
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62374543"
---
# <a name="compiler-warning-level-1-c4674"></a>編譯器警告 (層級 1) C4674

'method' 必須宣告為 'static'，而且只能有一個參數

轉換運算子的簽章不正確。 此方法不會視為使用者定義的轉換。 如需有關如何定義運算子的詳細資訊，請參閱[使用者定義的運算子 (C++/CLI)](../../dotnet/user-defined-operators-cpp-cli.md)並[使用者定義的轉換 (C++/CLI)](../../dotnet/user-defined-conversions-cpp-cli.md)。

## <a name="example"></a>範例

下列範例會產生 C4674。

```
// C4674.cpp
// compile with: /clr /WX /W1 /LD
ref class G {
   int op_Implicit(int i) {   // C4674
      return 0;
   }
};
```
