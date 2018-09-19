---
title: 編譯器警告 （層級 1） C4540 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4540
dev_langs:
- C++
helpviewer_keywords:
- C4540
ms.assetid: 8085e748-5f4d-43c2-b06d-eaf794edbf72
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 4e3f553bd1f910c7b17e079dc1f03664c78383e3
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46042763"
---
# <a name="compiler-warning-level-1-c4540"></a>編譯器警告 (層級 1) C4540

用來將轉換成無法存取或模稜兩可的基底; dynamic_cast執行階段測試將會失敗 ('type1' 到 'type2')

您已使用`dynamic_cast`從一種類型之間轉換。 編譯器已判斷轉換一律會失敗 (傳回**NULL**) 因為無法存取基底類別 (`private`、 執行個體) 或模稜兩可 （例如，類別階層架構中出現一次以上）。

以下顯示此警告的範例。 類別**B**衍生自類別**A**。程式會使用`dynamic_cast`轉換自類別**B** （在衍生的類別） 至類別**A**，這會一直失敗，因為類別**B**是`private`，因此無法存取。 變更的存取權**A**要**公用**會解決這個警告。

```
// C4540.cpp
// compile with: /W1

struct A {
   virtual void g() {}
};

struct B : private A {
   virtual void g() {}
};

int main() {
   B b;
   A * ap = dynamic_cast<A*>(&b);   // C4540
}
```