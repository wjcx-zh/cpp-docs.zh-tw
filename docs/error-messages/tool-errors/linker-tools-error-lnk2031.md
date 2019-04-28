---
title: 連結器工具錯誤 LNK2031
ms.date: 11/04/2016
f1_keywords:
- LNK2031
helpviewer_keywords:
- LNK2031
ms.assetid: 18ed4b6e-3e75-443c-bbd8-2f6030dc89ee
ms.openlocfilehash: 003b9a58bfb08130f034530f59e2de27efa2ae8d
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62298915"
---
# <a name="linker-tools-error-lnk2031"></a>連結器工具錯誤 LNK2031

> 無法產生 p/invoke，如 「*function_declaration*" *decorated_name*; 中繼資料中遺漏呼叫慣例

## <a name="remarks"></a>備註

當嘗試將純映像匯入原生函式，請記住，隱含的呼叫慣例，不同於原生和單純的編譯。 如需純映像的詳細資訊，請參閱[純粹的和可驗證程式碼 (C++/CLI)](../../dotnet/pure-and-verifiable-code-cpp-cli.md)。

**/Clr: pure**編譯器選項是在 Visual Studio 2015 中已被取代，不支援的 Visual Studio 2017 中。

## <a name="example"></a>範例

此程式碼範例會產生具有其呼叫慣例是隱含的匯出、 原生函式的元件[__cdecl](../../cpp/cdecl.md)。

```cpp
// LNK2031.cpp
// compile with: /LD
extern "C" {
   __declspec(dllexport) int func() { return 3; }
};
```

## <a name="example"></a>範例

下列範例會建立單純的用戶端使用原生函式。 不過，底下的呼叫慣例 **/clr: pure**是[__clrcall](../../cpp/clrcall.md)。 下列範例會產生 LNK2031。

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

下列範例示範如何使用原生函式，從純映像。 請注意明確 **__cdecl**呼叫慣例的規範。

```cpp
// LNK2031_c.cpp
// compile with: /clr:pure LNK2031.lib
extern "C" int __cdecl func();

int main() {
   return func();
}
```