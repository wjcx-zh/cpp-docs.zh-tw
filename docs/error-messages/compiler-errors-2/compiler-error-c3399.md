---
title: 編譯器錯誤 C3399
ms.date: 11/04/2016
f1_keywords:
- C3399
helpviewer_keywords:
- C3399
ms.assetid: 306ad199-d150-4f6c-bcf1-24a7948b93be
ms.openlocfilehash: d05a861a2baedb86482503b6860098f12c41bd78
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59776453"
---
# <a name="compiler-error-c3399"></a>編譯器錯誤 C3399

'type': 建立泛型參數的執行個體時無法提供引數

當您指定 `gcnew()` 條件約束時，即指定了無參數建構函式的條件約束類型。 因此，它是嘗試具現化該類型並傳遞參數的錯誤。

請參閱[泛型類型參數的條件約束 (C++/CLI)](../../extensions/constraints-on-generic-type-parameters-cpp-cli.md)如需詳細資訊。

## <a name="example"></a>範例

下列範例會產生 C3399。

```
// C3399.cpp
// compile with: /clr /c
generic <class T>
where T : gcnew()
void f() {
   T t = gcnew T(1);   // C3399
   T t2 = gcnew T();   // OK
}
```