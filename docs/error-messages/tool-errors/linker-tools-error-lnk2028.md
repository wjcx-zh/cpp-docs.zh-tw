---
title: 連結器工具錯誤 LNK2028
ms.date: 11/04/2016
f1_keywords:
- LNK2028
helpviewer_keywords:
- LNK2028
ms.assetid: e2b03293-6066-464d-a050-ce747bcf7f0e
ms.openlocfilehash: 29aaed167f750186d956589e9daa0d21c441149e
ms.sourcegitcommit: c1fd917a8c06c6504f66f66315ff352d0c046700
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/16/2020
ms.locfileid: "90684193"
---
# <a name="linker-tools-error-lnk2028"></a>連結器工具錯誤 LNK2028

"*exported_function*" (函數 "*Function_containing_function_call*" 中參考的*decorated_name*)  (*decorated_name) *

## <a name="remarks"></a>備註

當您嘗試將原生函式匯入純映射時，請記住，原生與純編譯之間的隱含呼叫慣例不同。

**/Clr： pure**編譯器選項在 Visual Studio 2015 中已被取代，Visual Studio 2017 中不支援。

## <a name="examples"></a>範例

這個程式碼範例會產生一個元件，其具有已匯出的原生函式，其呼叫慣例會隱含地 [__cdecl](../../cpp/cdecl.md)。

```cpp
// LNK2028.cpp
// compile with: /LD
__declspec(dllexport) int func() {
   return 3;
}
```

下列範例會建立使用原生函式的純用戶端。 不過， **/clr： pure** 下的呼叫慣例是 [__clrcall](../../cpp/clrcall.md)。 下列範例會產生 LNK2028。

```cpp
// LNK2028_b.cpp
// compile with: /clr:pure lnk2028.lib
// LNK2028 expected
int func();

int main() {
   return func();
}
```
