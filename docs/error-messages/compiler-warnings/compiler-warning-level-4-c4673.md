---
title: 編譯器警告 (層級 4) C4673
ms.date: 11/04/2016
f1_keywords:
- C4673
helpviewer_keywords:
- C4673
ms.assetid: 95626ec6-f05b-43c7-8b9a-a60a6f98dd30
ms.openlocfilehash: ceaa5cd647dfb527713613b9ce3b5cd81a780fd7
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50657726"
---
# <a name="compiler-warning-level-4-c4673"></a>編譯器警告 (層級 4) C4673

下列類型時擲回 'identifier' 不會考慮使用時，接收站台

擲回物件無法處理中**攔截**區塊。 無法處理每個類型會列在錯誤輸出，其中包含這個警告的那一行後面。 每個未處理的類型都有自己的警告。 閱讀每個特定的類型，如需詳細資訊的警告。

下列範例會產生 C4673:

```
// C4673.cpp
// compile with: /EHsc /W4
class Base {
private:
   char * m_chr;
public:
   Base() {
      m_chr = 0;
   }

   ~Base() {
      if(m_chr)
         delete m_chr;
   }
};

class Derv : private Base {
public:
   Derv() {}
   ~Derv() {}
};

int main() {
   try {
      Derv D1;
      // delete previous line, uncomment the next line to resolve
      // Base D1;
      throw D1;   // C4673
   }

   catch(...) {}
}
```