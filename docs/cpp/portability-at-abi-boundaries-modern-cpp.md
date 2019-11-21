---
title: ABI 界限上的可攜性 (現代 C++)
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: abbd405e-3038-427c-8c24-e00598f0936a
ms.openlocfilehash: 379b402354c6f08e003dffb38366d1dce20e0987
ms.sourcegitcommit: 654aecaeb5d3e3fe6bc926bafd6d5ace0d20a80e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/20/2019
ms.locfileid: "74246395"
---
# <a name="portability-at-abi-boundaries-modern-c"></a>ABI 界限上的可攜性 (現代 C++)

Use sufficiently portable types and conventions at binary interface boundaries. 「可攜式類型」是一種 C 內建的類型，或是只包含 C 內建類型的結構。 類別類型只可以在呼叫端和被呼叫端對配置、呼叫慣例等達成協議時才能使用。只有在兩者使用相同的編譯器和編譯器設定進行編譯時，才有可能出現此情形。

## <a name="how-to-flatten-a-class-for-c-portability"></a>如何簡化 C 可攜性的類別

When callers may be compiled with another compiler/language, then “flatten” to an **extern "C"** API with a specific calling convention:

```cpp
// class widget {
//   widget();
//   ~widget();
//   double method( int, gadget& );
// };
extern "C" {        // functions using explicit "this"
   struct widget;   // opaque type (forward declaration only)
   widget* STDCALL widget_create();      // constructor creates new "this"
   void STDCALL widget_destroy(widget*); // destructor consumes "this"
   double STDCALL widget_method(widget*, int, gadget*); // method uses "this"
}
```

## <a name="see-also"></a>請參閱

[Welcome back to C++](../cpp/welcome-back-to-cpp-modern-cpp.md)<br/>
[C++ 語言參考](../cpp/cpp-language-reference.md)<br/>
[C++ 標準程式庫](../standard-library/cpp-standard-library-reference.md)
