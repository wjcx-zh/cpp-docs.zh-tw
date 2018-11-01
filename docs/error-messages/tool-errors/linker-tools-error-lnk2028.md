---
title: 連結器工具錯誤 LNK2028
ms.date: 11/04/2016
f1_keywords:
- LNK2028
helpviewer_keywords:
- LNK2028
ms.assetid: e2b03293-6066-464d-a050-ce747bcf7f0e
ms.openlocfilehash: ed2dc1a95d4dd7c447b360da21b5046e20f79083
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50643673"
---
# <a name="linker-tools-error-lnk2028"></a>連結器工具錯誤 LNK2028

「*exported_function*」 (*decorated_name*) 函式中參考 「*function_containing_function_call*」 (*decorated_name*)

## <a name="remarks"></a>備註

當嘗試將純映像匯入原生函式，請記住，隱含的呼叫慣例，不同於原生和單純的編譯。

**/Clr: pure**編譯器選項是在 Visual Studio 2015 中已被取代，不支援的 Visual Studio 2017 中。

## <a name="example"></a>範例

此程式碼範例會產生具有其呼叫慣例是隱含的匯出、 原生函式的元件[__cdecl](../../cpp/cdecl.md)。

```cpp
// LNK2028.cpp
// compile with: /LD
__declspec(dllexport) int func() {
   return 3;
}
```

## <a name="example"></a>範例

下列範例會建立單純的用戶端使用原生函式。 不過，底下的呼叫慣例 **/clr: pure**是[__clrcall](../../cpp/clrcall.md)。 下列範例會產生 LNK2028。

```cpp
// LNK2028_b.cpp
// compile with: /clr:pure lnk2028.lib
// LNK2028 expected
int func();

int main() {
   return func();
}
```