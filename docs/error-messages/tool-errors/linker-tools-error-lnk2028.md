---
title: 連結器工具錯誤 LNK2028
ms.date: 11/04/2016
f1_keywords:
- LNK2028
helpviewer_keywords:
- LNK2028
ms.assetid: e2b03293-6066-464d-a050-ce747bcf7f0e
ms.openlocfilehash: ef9e3eae655a4fbee1c3da74f6036e5fb22434b1
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80194612"
---
# <a name="linker-tools-error-lnk2028"></a>連結器工具錯誤 LNK2028

函數 "*function_containing_function_call*" （*decorated_name*）中參考的 "*exported_function*" （*decorated_name*）

## <a name="remarks"></a>備註

嘗試將原生函式匯入純映射時，請記住，在原生和純編譯之間的隱含呼叫慣例不同。

**/Clr： pure**編譯器選項在 Visual Studio 2015 中已被取代，在 Visual Studio 2017 中不支援。

## <a name="example"></a>範例

這個程式碼範例會產生一個元件，其中包含已匯出的原生函數，其呼叫慣例會隱含[__cdecl](../../cpp/cdecl.md)。

```cpp
// LNK2028.cpp
// compile with: /LD
__declspec(dllexport) int func() {
   return 3;
}
```

## <a name="example"></a>範例

下列範例會建立使用原生函式的單純用戶端。 不過，在 **/clr： pure**下的呼叫慣例是[__clrcall](../../cpp/clrcall.md)。 下列範例會產生 LNK2028。

```cpp
// LNK2028_b.cpp
// compile with: /clr:pure lnk2028.lib
// LNK2028 expected
int func();

int main() {
   return func();
}
```
