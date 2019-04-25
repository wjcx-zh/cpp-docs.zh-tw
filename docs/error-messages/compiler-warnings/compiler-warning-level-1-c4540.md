---
title: 編譯器警告 (層級 1) C4540
ms.date: 11/04/2016
f1_keywords:
- C4540
helpviewer_keywords:
- C4540
ms.assetid: 8085e748-5f4d-43c2-b06d-eaf794edbf72
ms.openlocfilehash: 86f6cd866f7708277ebba436ba7c076086dc9c8c
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62160701"
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