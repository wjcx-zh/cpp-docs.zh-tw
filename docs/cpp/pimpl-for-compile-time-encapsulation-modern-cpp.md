---
title: （現代 c + +） 的編譯時間封裝的 Pimpl |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: c3e8a90a-b328-4990-82bb-e1b147f76e07
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 83b01a58745185499ac02a254a207fac2779be26
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46059000"
---
# <a name="pimpl-for-compile-time-encapsulation-modern-c"></a>編譯時間封裝的 Pimpl (現代 C++)

*Pimpl 慣用語*是現代化的 c + + 技術來隱藏實作，為了減少結合，並將介面。 Pimpl 會簡稱為 「 指標來實作。 」 您可能已經熟悉這個概念，但知道以其他名稱，例如 Cheshire Cat 或編譯器防火牆的慣用語。

## <a name="why-use-pimpl"></a>為何要使用 pimpl？

以下是如何 pimpl 慣用語可以改善軟體開發生命週期：

- 編譯相依性的最小化。

- 關注點分離介面和實作。

- 可攜性。

## <a name="pimpl-header"></a>Pimpl 標頭

```cpp
// my_class.h
class my_class {
   //  ... all public and protected stuff goes here ...
private:
   class impl; unique_ptr<impl> pimpl; // opaque type here
};
```

Pimpl 慣用語可避免重建串聯，聯集並不可靠的物件配置。 它被專為 （間接） 的受歡迎的類型。

## <a name="pimpl-implementation"></a>Pimpl 實作

定義`impl`在.cpp 檔案中的類別。

```cpp
// my_class.cpp
class my_class::impl {  // defined privately here
  // ... all private data and functions: all of these
  //     can now change without recompiling callers ...
};
my_class::my_class(): pimpl( new impl )
{
  // ... set impl values ...
}
```

## <a name="best-practices"></a>最佳做法

請考慮是否要加入非擲回交換特製化的支援。

## <a name="see-also"></a>另請參閱

[歡迎回到 C++](../cpp/welcome-back-to-cpp-modern-cpp.md)<br/>
[C++ 語言參考](../cpp/cpp-language-reference.md)<br/>
[C++ 標準程式庫](../standard-library/cpp-standard-library-reference.md)