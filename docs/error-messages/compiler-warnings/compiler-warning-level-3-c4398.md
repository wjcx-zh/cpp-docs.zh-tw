---
title: 編譯器警告 (層級 3) C4398
ms.date: 11/04/2016
f1_keywords:
- C4398
helpviewer_keywords:
- C4398
ms.assetid: b6221432-9fed-4272-a547-a73f587904e6
ms.openlocfilehash: 4126a1267b41cdf9c0161c7e85a9057b2a301d77
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50578460"
---
# <a name="compiler-warning-level-3-c4398"></a>編譯器警告 (層級 3) C4398

> '*變數*': 處理序專屬全域物件可能無法使用多個 appdomain 正確運作，請考慮使用 __declspec(appdomain)

## <a name="remarks"></a>備註

使用虛擬函式[__clrcall](../../cpp/clrcall.md)原生類型中呼叫慣例會導致建立每個應用程式網域 vtable。 使用多個應用程式定義域中時，這類變數可能無法正確地修正。

您可以明確地標示變數來解決這個警告`__declspec(appdomain)`。 在 Visual Studio 2017 之前的 Visual Studio 版本中，您可以與編譯來解決這個警告 **/clr: pure**，因此依預設每個 appdomain 全域變數。 **/Clr: pure**編譯器選項是在 Visual Studio 2015 中已被取代，不支援的 Visual Studio 2017 中。

如需詳細資訊，請參閱 < [appdomain](../../cpp/appdomain.md)並[應用程式定義域和 Visual c + +](../../dotnet/application-domains-and-visual-cpp.md)。

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