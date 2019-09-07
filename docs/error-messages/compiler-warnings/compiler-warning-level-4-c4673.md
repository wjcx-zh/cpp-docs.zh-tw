---
title: 編譯器警告 (層級 4) C4673
ms.date: 11/04/2016
f1_keywords:
- C4673
helpviewer_keywords:
- C4673
ms.assetid: 95626ec6-f05b-43c7-8b9a-a60a6f98dd30
ms.openlocfilehash: ceaa5cd647dfb527713613b9ce3b5cd81a780fd7
ms.sourcegitcommit: 180f63704f6ddd07a4172a93b179cf0733fd952d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/06/2019
ms.locfileid: "70741380"
---
# <a name="compiler-warning-level-4-c4673"></a>編譯器警告 (層級 4) C4673

擲回 ' identifier '，將不會在 catch 網站上考慮下列類型

無法在**catch**區塊中處理 throw 物件。 每個無法處理的類型都會在包含此警告的行之後的錯誤輸出中列出。 每個未處理的型別都有自己的警告。 如需詳細資訊，請參閱每個特定類型的警告。

下列範例會產生 C4673：

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