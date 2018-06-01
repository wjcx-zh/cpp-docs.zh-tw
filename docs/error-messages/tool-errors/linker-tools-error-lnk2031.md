---
title: 連結器工具錯誤 LNK2031 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- LNK2031
dev_langs:
- C++
helpviewer_keywords:
- LNK2031
ms.assetid: 18ed4b6e-3e75-443c-bbd8-2f6030dc89ee
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: d86ea6da8a73d9ba2427e9455c4fca87cd32dd2b
ms.sourcegitcommit: a4454b91d556a3dc43d8755cdcdeabcc9285a20e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/01/2018
ms.locfileid: "34703661"
---
# <a name="linker-tools-error-lnk2031"></a>連結器工具錯誤 LNK2031

> 無法產生 p/invoke，如"*function_declaration*" *decorated_name*; 中繼資料中遺漏呼叫慣例

## <a name="remarks"></a>備註

當嘗試以原生函式匯入純映像，請記住，隱含的呼叫慣例，原生或純編譯之間不同而有所不同。 如需純映像的詳細資訊，請參閱[純粹的和可驗證程式碼 (C + + /CLI)](../../dotnet/pure-and-verifiable-code-cpp-cli.md)。

**/Clr: pure**編譯器選項已被取代 Visual Studio 2015 中，在 Visual Studio 2017 中支援。

## <a name="example"></a>範例

此程式碼範例會產生含匯出、 原生函式的呼叫慣例是隱含的元件[__cdecl](../../cpp/cdecl.md)。

```cpp
// LNK2031.cpp
// compile with: /LD
extern "C" {
   __declspec(dllexport) int func() { return 3; }
};
```

## <a name="example"></a>範例

下列範例會建立使用原生函式的純用戶端。 不過，下方的呼叫慣例 **/clr: pure**是[__clrcall](../../cpp/clrcall.md)。 下列範例會產生 LNK2031。

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

下列範例會示範如何使用純映像的原生函式。 請注意明確 **__cdecl**呼叫慣例的規範。

```cpp
// LNK2031_c.cpp
// compile with: /clr:pure LNK2031.lib
extern "C" int __cdecl func();

int main() {
   return func();
}
```