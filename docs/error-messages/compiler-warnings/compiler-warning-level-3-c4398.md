---
title: 編譯器警告 (層級 3) C4398
ms.date: 11/04/2016
f1_keywords:
- C4398
helpviewer_keywords:
- C4398
ms.assetid: b6221432-9fed-4272-a547-a73f587904e6
ms.openlocfilehash: 041bf9f6bfce17b16f301604bb8706be30095c13
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80198662"
---
# <a name="compiler-warning-level-3-c4398"></a>編譯器警告 (層級 3) C4398

> 「*變數*」：每個進程的全域物件可能無法搭配多個 appdomain 正常運作;考慮使用 __declspec （appdomain）

## <a name="remarks"></a>備註

在原生類型中具有[__clrcall](../../cpp/clrcall.md)呼叫慣例的虛擬函式，會導致每個應用程式網域 vtable 的建立。 使用於多個應用程式域時，這類變數可能無法正確更正。

您可以藉由明確地將變數標示 `__declspec(appdomain)`來解決這個警告。 在 Visual Studio 2017 之前的 Visual Studio 版本中，您可以藉由使用 **/clr： pure**進行編譯來解決這個警告，預設會使每個 appdomain 的全域變數。 **/Clr： pure**編譯器選項在 Visual Studio 2015 中已被取代，在 Visual Studio 2017 中不支援。

如需詳細資訊，請參閱[appdomain](../../cpp/appdomain.md)和[應用程式C++域和視覺效果](../../dotnet/application-domains-and-visual-cpp.md)。

## <a name="example"></a>範例

下列範例會產生 C4398。

```cpp
// C4398.cpp
// compile with: /clr /W3 /c
struct S {
   virtual void f( System::String ^ );   // String^ parameter makes function __clrcall
};

S glob_s;   // C4398
__declspec(appdomain) S glob_s2;   // OK
```
