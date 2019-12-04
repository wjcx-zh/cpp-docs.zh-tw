---
title: 編譯器錯誤 C2506
ms.date: 11/04/2016
f1_keywords:
- C2506
helpviewer_keywords:
- C2506
ms.assetid: cfed21cd-2404-46f2-985e-d0c2c3820830
ms.openlocfilehash: 593fbbc6b561e6390624aa79af14dc665a552990
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/03/2019
ms.locfileid: "74746834"
---
# <a name="compiler-error-c2506"></a>編譯器錯誤 C2506

' member '： ' __declspec （修飾詞） ' 無法套用至此符號

您不能針對 managed 類別的靜態成員，宣告每個進程或每個 appdomain。

如需詳細資訊，請參閱 [appdomain](../../cpp/appdomain.md) 。

## <a name="example"></a>範例

下列範例會產生 C2506。

```cpp
// C2506.cpp
// compile with: /clr /c
ref struct R {
   __declspec(process) static int n;   // C2506
   int o;   // OK
};
```
