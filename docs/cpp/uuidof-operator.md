---
title: __uuidof 運算子
ms.date: 10/10/2018
f1_keywords:
- __LIBID_cpp
- __uuidof_cpp
- __uuidof
- _uuidof
helpviewer_keywords:
- __uuidof keyword [C++]
- __LIBID_ keyword [C++]
ms.assetid: badfe709-809b-4b66-ad48-ee35039d25c6
ms.openlocfilehash: 09348d061fde4cb09eb6eb351f146404f355e184
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80187787"
---
# <a name="__uuidof-operator"></a>__uuidof 運算子

**Microsoft 專屬**

擷取附加至運算式的 GUID。

## <a name="syntax"></a>語法

```
__uuidof (expression)
```

## <a name="remarks"></a>備註

*運算式*可以是類型名稱、指標、參考或該類型的陣列、在這些類型上特製化的樣板，或這些類型的變數。 只要編譯器可以用它來尋找附加的 GUID，則引數有效。

這個內建函式的特殊案例是當**0**或 Null 做為引數提供時。 在此情況下， **__uuidof**會傳回由零組成的 GUID。

使用這個關鍵字擷取附加至下列項目的 GUID：

- 由[uuid](../cpp/uuid-cpp.md)擴充屬性所產生的物件。

- 使用[module](../windows/attributes/module-cpp.md)屬性建立的程式庫區塊。

> [!NOTE]
> 在 debug 組建中， **__uuidof**一律會動態初始化物件（在執行時間）。 在發行組建中， **__uuidof**可以靜態方式（在編譯時期）初始化物件。

為了與舊版相容，除非指定了編譯器選項[/za \(停用語言擴充功能）](../build/reference/za-ze-disable-language-extensions.md) ，否則 **_uuidof**是 **__uuidof**的同義字。

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

如果程式庫名稱不再在範圍內，您可以使用 `__LIBID_`，而不是 **__uuidof**。 例如：

```cpp
StringFromCLSID(__LIBID_, &lpolestr);
```

**END Microsoft 特定的**

## <a name="see-also"></a>另請參閱

[具有一元運算子的運算式](../cpp/expressions-with-unary-operators.md)<br/>
[關鍵字](../cpp/keywords-cpp.md)
