---
title: 連結器工具錯誤 LNK2028 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- LNK2028
dev_langs:
- C++
helpviewer_keywords:
- LNK2028
ms.assetid: e2b03293-6066-464d-a050-ce747bcf7f0e
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: e9c8eaa03927f51acd3c3d84731e9ef2b282b7c6
ms.sourcegitcommit: a4454b91d556a3dc43d8755cdcdeabcc9285a20e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2018
ms.locfileid: "34704150"
---
# <a name="linker-tools-error-lnk2028"></a>連結器工具錯誤 LNK2028

「*exported_function*」 (*decorated_name*) 函式中參考 」*function_containing_function_call*」 (*decorated_name*)

## <a name="remarks"></a>備註

當嘗試以原生函式匯入純映像，請記住，隱含的呼叫慣例，原生或純編譯之間不同而有所不同。

**/Clr: pure**編譯器選項已被取代 Visual Studio 2015 中，在 Visual Studio 2017 中支援。

## <a name="example"></a>範例

此程式碼範例會產生含匯出、 原生函式的呼叫慣例是隱含的元件[__cdecl](../../cpp/cdecl.md)。

```cpp
// LNK2028.cpp
// compile with: /LD
__declspec(dllexport) int func() {
   return 3;
}
```

## <a name="example"></a>範例

下列範例會建立使用原生函式的純用戶端。 不過，下方的呼叫慣例 **/clr: pure**是[__clrcall](../../cpp/clrcall.md)。 下列範例會產生 LNK2028。

```cpp
// LNK2028_b.cpp
// compile with: /clr:pure lnk2028.lib
// LNK2028 expected
int func();

int main() {
   return func();
}
```