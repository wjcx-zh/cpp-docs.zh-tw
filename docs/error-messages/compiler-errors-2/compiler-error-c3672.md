---
title: 編譯器錯誤 C3672
ms.date: 11/04/2016
f1_keywords:
- C3672
helpviewer_keywords:
- C3672
ms.assetid: da971041-1766-467a-aecf-1d8655c6cb7a
ms.openlocfilehash: 36048f3e4b8cc1be3e766f11b5c131513a3365da
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50436773"
---
# <a name="compiler-error-c3672"></a>編譯器錯誤 C3672

虛擬解構函式運算式只能做為函式呼叫的一部分

未正確地呼叫解構函式。  如需詳細資訊，請參閱 <<c0> [ 解構函式](../../cpp/destructors-cpp.md)。

## <a name="example"></a>範例

下列範例會產生 C3672。

```
// C3672.cpp
template<typename T>
void f(T* pT) {
   &pT->T::~T;   // C3672
   pT->T::~T();   // OK
};

int main() {
   int i;
   f(&i);
}
```