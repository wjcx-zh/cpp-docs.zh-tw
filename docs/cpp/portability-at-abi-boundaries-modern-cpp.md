---
title: ABI 界限上的可攜性 (現代 C++)
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: abbd405e-3038-427c-8c24-e00598f0936a
ms.openlocfilehash: 3f72bc32e436c2f7a2f76ed6bbb9553b5e5be6b8
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62267672"
---
# <a name="portability-at-abi-boundaries-modern-c"></a>ABI 界限上的可攜性 (現代 C++)

使用二進位介面邊界的可攜式類型和慣例。 「可攜式類型」是一種 C 內建的類型，或是只包含 C 內建類型的結構。 類別類型僅適用於當呼叫端和被呼叫端同意版面配置，呼叫慣例等。兩者都使用相同的編譯器和編譯器設定編譯時，這樣做才可行。

## <a name="how-to-flatten-a-class-for-c-portability"></a>如何簡化 C 可攜性的類別

當呼叫端可能會與其他編譯器/語言進行編譯，則 「 簡化 」 為**extern"C"** 與特定的呼叫慣例的 API:

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

## <a name="see-also"></a>另請參閱

[歡迎回到 C++ (現代 C++)](../cpp/welcome-back-to-cpp-modern-cpp.md)<br/>
[C++ 語言參考](../cpp/cpp-language-reference.md)<br/>
[C++ 標準程式庫](../standard-library/cpp-standard-library-reference.md)
