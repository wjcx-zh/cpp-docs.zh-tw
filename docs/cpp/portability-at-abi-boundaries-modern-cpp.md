---
title: ABI 界限 （現代 c + +） 的可攜性 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: abbd405e-3038-427c-8c24-e00598f0936a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 891f56d763fc86efd62fb5bae3b21498336a8ccc
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46058404"
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

[歡迎回到 C++](../cpp/welcome-back-to-cpp-modern-cpp.md)<br/>
[C++ 語言參考](../cpp/cpp-language-reference.md)<br/>
[C++ 標準程式庫](../standard-library/cpp-standard-library-reference.md)