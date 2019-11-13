---
title: 編譯器警告 (層級 1) C4674
ms.date: 11/04/2016
f1_keywords:
- C4674
helpviewer_keywords:
- C4674
ms.assetid: 638dae0b-b82c-4865-9599-72630827ca09
ms.openlocfilehash: b9428a593ff59cbdfa6d8eb369413a560b4a5ad2
ms.sourcegitcommit: 458dcc794e3841919c01a3a5ff6b9a3767f8861b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/13/2019
ms.locfileid: "74052547"
---
# <a name="compiler-warning-level-1-c4674"></a>編譯器警告 (層級 1) C4674

'method' 必須宣告為 'static'，而且只能有一個參數

轉換運算子的簽章不正確。 此方法不會視為使用者定義的轉換。 如需定義運算子的詳細資訊，請參閱[使用者定義的C++運算子（/Cli）](../../dotnet/user-defined-operators-cpp-cli.md)和[使用者定義的C++轉換（/cli）](../../dotnet/user-defined-conversions-cpp-cli.md)。

## <a name="example"></a>範例

下列範例會產生 C4674。

```cpp
// C4674.cpp
// compile with: /clr /WX /W1 /LD
ref class G {
   int op_Implicit(int i) {   // C4674
      return 0;
   }
};
```
