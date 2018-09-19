---
title: 編譯器錯誤 C3675 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3675
dev_langs:
- C++
helpviewer_keywords:
- C3675
ms.assetid: 87461613-6633-430b-b95d-c7cb1bb63776
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: c4b6656753ab4a611dcb80d1473e0b44bf47a270
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46094776"
---
# <a name="compiler-error-c3675"></a>編譯器錯誤 C3675

'function': 已保留，因為 'property' 定義

當您宣告簡單的屬性時，則編譯器會產生 get 和 set 存取子方法，以及名稱會出現在您的程式範圍。  編譯器產生的名稱是前面加上 get_ 和 set_ 屬性名稱形成。  因此，您無法宣告具有編譯器產生的存取子的相同名稱的函式。

如需詳細資訊，請參閱 [property](../../windows/property-cpp-component-extensions.md) 。

## <a name="example"></a>範例

下列範例會產生 C3675。

```
// C3675.cpp
// compile with: /clr /c
ref struct C {
public:
   property int Size;
   int get_Size() { return 0; }   // C3675
};
```