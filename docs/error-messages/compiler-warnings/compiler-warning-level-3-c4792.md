---
title: 編譯器警告 (層級 3) C4792
ms.date: 11/04/2016
f1_keywords:
- C4792
helpviewer_keywords:
- C4792
ms.assetid: c047ce69-a622-44e1-9425-d41aa9261c61
ms.openlocfilehash: 84a8a8bbb08ac97fe87d63d1ea44587790f87d92
ms.sourcegitcommit: 217fac22604639ebd62d366a69e6071ad5b724ac
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/19/2019
ms.locfileid: "74189333"
---
# <a name="compiler-warning-level-3-c4792"></a>編譯器警告 (層級 3) C4792

使用 sysimport 宣告並從機器碼參考的函式 'function'; 匯入程式庫需要連結

已從 Unmanaged 函式呼叫使用 DllImport 匯入至程式的原生函式。 因此，您必須連結至 DLL 的匯入程式庫。

透過程式碼，或變更編譯方式，並無法解決這個警告。 請使用 [warning](../../preprocessor/warning.md) pragma 來停用這個警告。

下列範例會產生 C4792：

```cpp
// C4792.cpp
// compile with: /clr /W3
// C4792 expected
using namespace System::Runtime::InteropServices;
[DllImport("msvcrt")]
extern "C" int __cdecl puts(const char *);
int main() {}

// Uncomment the following line to resolve.
// #pragma warning(disable : 4792)
#pragma unmanaged
void func(void){
   puts("test");
}
```