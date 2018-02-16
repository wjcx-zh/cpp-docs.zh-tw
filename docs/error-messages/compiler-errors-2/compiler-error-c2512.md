---
title: "編譯器錯誤 C2512 |Microsoft 文件"
ms.custom: 
ms.date: 02/09/2018
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C2512
dev_langs:
- C++
helpviewer_keywords:
- C2512
ms.assetid: 15206da9-1164-451a-b869-280e00711aad
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 57dbb542eee7e893253e6c3bdd3410c605a8d2db
ms.sourcegitcommit: 8ae12a602244a5853e941e5e8806e3545d876844
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/15/2018
---
# <a name="compiler-error-c2512"></a>編譯器錯誤 C2512

> '*識別碼*': 沒有適當的預設建構函式使用  

A*預設建構函式*，需要任何引數的建構函式不適用於指定的類別、 結構或等位。 只有當沒有使用者定義建構函式所提供，則編譯器會提供預設建構函式。

如果您提供的建構函式採用非 void 參數，而且您想要允許您要建立不含任何參數 （例如，做為陣列的項目） 的類別，您也必須提供預設建構函式。 預設建構函式可為具備所有參數之預設值的建構函式。

## <a name="example"></a>範例

錯誤 C2512 的常見原因是當您定義的類別或結構建構函式引數，然後嘗試宣告類別或結構沒有任何引數的執行個體。 例如，`struct B`下面會宣告建構函式需要`char *`引數，但並不採用任何引數。 在`main`，宣告 B 的執行個體，但沒有提供任何引數。 編譯器會產生 C2512，因為它找不到預設的建構函式 b。

```cpp
// C2512.cpp
// Compile with: cl /W4 c2512.cpp
// C2512 expected
struct B {
   B (char *) {}
   // Uncomment the following line to fix.
   // B() {}
};

int main() {
   B b;   // C2512 - This requires a default constructor
}
```

您可以修正此問題，例如定義您的結構或類別的預設建構函式`B() {}`，或建構函式，其中的所有引數具有預設值，例如`B (char * = nullptr) {}`。
