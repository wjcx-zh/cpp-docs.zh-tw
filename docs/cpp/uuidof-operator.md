---
title: __uuidof 運算子 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- __LIBID_cpp
- __uuidof_cpp
dev_langs:
- C++
helpviewer_keywords:
- __uuidof keyword [C++]
- __LIBID_ keyword [C++]
ms.assetid: badfe709-809b-4b66-ad48-ee35039d25c6
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 84fd779d50fb481cffc97b61a65f255c6c8f52a1
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46056727"
---
# <a name="uuidof-operator"></a>__uuidof 運算子

**Microsoft 專屬**

擷取附加至運算式的 GUID。

## <a name="syntax"></a>語法

```
__uuidof (expression)
```

## <a name="remarks"></a>備註

*運算式*可能型別名稱、 指標、 參考或該型別的陣列，這些類型或這些類型的變數上的特製化樣板。 只要編譯器可以用它來尋找附加的 GUID，則引數有效。

此內建函式的特殊案例是當任一**0**或做為引數提供了 NULL。 在此情況下， **__uuidof**會傳回零組成的 GUID。

使用這個關鍵字擷取附加至下列項目的 GUID：

- 物件的[uuid](../cpp/uuid-cpp.md)擴充的屬性。

- 使用建立程式庫區塊[模組](../windows/module-cpp.md)屬性。

> [!NOTE]
>  在偵錯組建中， **__uuidof**一律會初始化物件以動態方式 （在執行階段）。 在發行組建，而 **__uuidof**可以靜態 （在編譯時期） 初始化物件。

## <a name="example"></a>範例

下列程式碼 (以 ole32.lib 編譯) 會顯示以模組屬性所建立之程式庫區塊的 uuid：

```cpp
// expre_uuidof.cpp
// compile with: ole32.lib
#include "stdio.h"
#include "windows.h"

[emitidl];
[module(name="MyLib")];
[export]
struct stuff {
   int i;
};

int main() {
   LPOLESTR lpolestr;
   StringFromCLSID(__uuidof(MyLib), &lpolestr);
   wprintf_s(L"%s", lpolestr);
   CoTaskMemFree(lpolestr);
}
```

## <a name="comments"></a>註解

在範圍中不再是程式庫名稱的情況下，您可以使用`__LIBID_`而非 **__uuidof**。 例如: 

```cpp
StringFromCLSID(__LIBID_, &lpolestr);
```

**結束 Microsoft 專屬**

## <a name="see-also"></a>另請參閱

[具有一元運算子的運算式](../cpp/expressions-with-unary-operators.md)<br/>
[關鍵字](../cpp/keywords-cpp.md)