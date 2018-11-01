---
title: 編譯器錯誤 C2953
ms.date: 11/04/2016
f1_keywords:
- C2953
helpviewer_keywords:
- C2953
ms.assetid: 8dbcfa24-8296-4e40-bdc4-5526c07d8892
ms.openlocfilehash: 8fa0e533b23f735f948fdad0ecf11beb3766f452
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50591034"
---
# <a name="compiler-error-c2953"></a>編譯器錯誤 C2953

'identifier': 類別樣板已經定義過了

請檢查原始程式碼檔並包含其他定義的檔案。

下列範例會產生 C2953：

```
// C2953.cpp
// compile with: /c
template <class T>  class A {};
template <class T>  class A {};   // C2953
template <class T>  class B {};   // OK
```