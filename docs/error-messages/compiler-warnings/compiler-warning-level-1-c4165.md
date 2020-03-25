---
title: 編譯器警告（層級1） C4165
ms.date: 11/04/2016
f1_keywords:
- C4165
helpviewer_keywords:
- C4165
ms.assetid: f5bed515-2290-4f88-8dab-b45d95fe26ef
ms.openlocfilehash: bb036f7672a074e859d3e19083e256bd80c93578
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80176091"
---
# <a name="compiler-warning-level-1-c4165"></a>編譯器警告（層級1） C4165

' HRESULT ' 正在轉換成 ' bool ';您確定這是您想要的嗎？

在[if](../../cpp/if-else-statement-cpp.md)語句中使用 hresult 時，除非您明確地將變數測試為 hresult，否則會將 hresult 轉換為[bool](../../cpp/bool-cpp.md) 。 此警告預設為關閉。

## <a name="example"></a>範例

下列範例會產生 C4165

```cpp
// C4165.cpp
// compile with: /W1
#include <windows.h>
#pragma warning(1:4165)

extern HRESULT hr;
int main() {
   if (hr) {
   // try either of the following ...
   // if (FAILED(hr)) { // C4165 expected
   // if (hr != S_OK) {
   }
}
```
