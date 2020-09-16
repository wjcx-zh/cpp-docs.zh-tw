---
title: 連結器工具錯誤 LNK2031
ms.date: 11/04/2016
f1_keywords:
- LNK2031
helpviewer_keywords:
- LNK2031
ms.assetid: 18ed4b6e-3e75-443c-bbd8-2f6030dc89ee
ms.openlocfilehash: 73ca4a51737d1c073b3164f7e5aaa6deba369a38
ms.sourcegitcommit: c1fd917a8c06c6504f66f66315ff352d0c046700
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/16/2020
ms.locfileid: "90684179"
---
# <a name="linker-tools-error-lnk2031"></a>連結器工具錯誤 LNK2031

> 無法為 "*function_declaration*" 產生 p/invoke *decorated_name*;中繼資料中缺少呼叫慣例

## <a name="remarks"></a>備註

當您嘗試將原生函式匯入純映射時，請記住，原生與純編譯之間的隱含呼叫慣例不同。 如需有關純影像的詳細資訊，請參閱 [單純和可驗證的程式碼 (c + +/cli) ](../../dotnet/pure-and-verifiable-code-cpp-cli.md)。

**/Clr： pure**編譯器選項在 Visual Studio 2015 中已被取代，Visual Studio 2017 中不支援。

## <a name="examples"></a>範例

這個程式碼範例會產生一個元件，其具有已匯出的原生函式，其呼叫慣例會隱含地 [__cdecl](../../cpp/cdecl.md)。

```cpp
// LNK2031.cpp
// compile with: /LD
extern "C" {
   __declspec(dllexport) int func() { return 3; }
};
```

下列範例會建立使用原生函式的純用戶端。 不過， **/clr： pure** 下的呼叫慣例是 [__clrcall](../../cpp/clrcall.md)。 下列範例會產生 LNK2031。

```cpp
// LNK2031_b.cpp
// compile with: /clr:pure LNK2031.lib
// LNK2031 expected
extern "C" int func();

int main() {
   return func();
}
```

下列範例顯示如何從純映射取用原生函式。 請注意明確的 **`__cdecl`** 呼叫慣例規範。

```cpp
// LNK2031_c.cpp
// compile with: /clr:pure LNK2031.lib
extern "C" int __cdecl func();

int main() {
   return func();
}
```
