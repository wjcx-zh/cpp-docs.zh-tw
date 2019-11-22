---
title: ABI 界限的可攜性
description: 將C++介面壓平合併為二進位介面界限的 C 呼叫慣例。
ms.date: 11/19/2019
ms.topic: conceptual
ms.assetid: abbd405e-3038-427c-8c24-e00598f0936a
ms.openlocfilehash: b3b2b217739ff5900c8ef0329ff3e8909a3fe036
ms.sourcegitcommit: 069e3833bd821e7d64f5c98d0ea41fc0c5d22e53
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2019
ms.locfileid: "74303323"
---
# <a name="portability-at-abi-boundaries"></a>ABI 界限的可攜性

在二進位介面界限使用充分的可攜性類型和慣例。 「可移植類型」是一種 C 內建類型，或僅包含 C 內建類型的結構。 只有當呼叫端和被呼叫端同意版面配置、呼叫慣例等時，才可以使用類別類型。只有當使用相同的編譯器和編譯器設定來編譯時，才有可能發生這種情況。

## <a name="how-to-flatten-a-class-for-c-portability"></a>如何簡化 C 可攜性的類別

當呼叫端可以使用另一個編譯器/語言進行編譯時，請使用特定的呼叫慣例將「簡維」為**extern "C"** API：

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

[歡迎回到C++](../cpp/welcome-back-to-cpp-modern-cpp.md)<br/>
[C++ 語言參考](../cpp/cpp-language-reference.md)<br/>
[C++ 標準程式庫](../standard-library/cpp-standard-library-reference.md)
