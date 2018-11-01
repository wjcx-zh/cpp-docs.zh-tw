---
title: 編譯器錯誤 C3223
ms.date: 11/04/2016
f1_keywords:
- C3223
helpviewer_keywords:
- C3223
ms.assetid: 1f4380b4-0413-40db-a868-62f97babaf78
ms.openlocfilehash: 9c53f7c91cc0e8f4c56d8d780b222b199702310e
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50486446"
---
# <a name="compiler-error-c3223"></a>編譯器錯誤 C3223

'property' : 不可將 'typeid' 套用至屬性

您無法將 [typeid](../../windows/typeid-cpp-component-extensions.md) 套用至屬性。

## <a name="example"></a>範例

下列範例會產生 C3223。

```
// C3223.cpp
// compile with: /clr
ref class R {
public:
   property int myprop;
};

int main() {
   System::Type^ type2 = R::myprop::typeid;   // C3223
}
```