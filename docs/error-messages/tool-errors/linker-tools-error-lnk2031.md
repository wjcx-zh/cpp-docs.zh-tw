---
title: 連結器工具錯誤 LNK2031
ms.date: 11/04/2016
f1_keywords:
- LNK2031
helpviewer_keywords:
- LNK2031
ms.assetid: 18ed4b6e-3e75-443c-bbd8-2f6030dc89ee
ms.openlocfilehash: 096ccb7ff443d24e0d53e73a5950faa1e85aeae6
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80194560"
---
# <a name="linker-tools-error-lnk2031"></a>連結器工具錯誤 LNK2031

> 無法產生 "*function_declaration*" 的 p/invoke *decorated_name*;中繼資料中遺漏呼叫慣例

## <a name="remarks"></a>備註

嘗試將原生函式匯入純映射時，請記住，在原生和純編譯之間的隱含呼叫慣例不同。 如需純圖像的詳細資訊，請參閱[單純和可C++驗證的程式碼（/cli）](../../dotnet/pure-and-verifiable-code-cpp-cli.md)。

**/Clr： pure**編譯器選項在 Visual Studio 2015 中已被取代，在 Visual Studio 2017 中不支援。

## <a name="example"></a>範例

這個程式碼範例會產生一個元件，其中包含已匯出的原生函數，其呼叫慣例會隱含[__cdecl](../../cpp/cdecl.md)。

```cpp
// LNK2031.cpp
// compile with: /LD
extern "C" {
   __declspec(dllexport) int func() { return 3; }
};
```

## <a name="example"></a>範例

下列範例會建立使用原生函式的單純用戶端。 不過，在 **/clr： pure**下的呼叫慣例是[__clrcall](../../cpp/clrcall.md)。 下列範例會產生 LNK2031。

```cpp
// LNK2031_b.cpp
// compile with: /clr:pure LNK2031.lib
// LNK2031 expected
extern "C" int func();

int main() {
   return func();
}
```

## <a name="example"></a>範例

下列範例示範如何從純映射取用原生函式。 請注意明確 **__cdecl**呼叫慣例規範。

```cpp
// LNK2031_c.cpp
// compile with: /clr:pure LNK2031.lib
extern "C" int __cdecl func();

int main() {
   return func();
}
```
