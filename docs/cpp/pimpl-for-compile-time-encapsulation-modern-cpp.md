---
title: 編譯時期封裝的 Pimpl (現代 C++)
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: c3e8a90a-b328-4990-82bb-e1b147f76e07
ms.openlocfilehash: f1eb06ad3a52be486f085babf699677951b1ee71
ms.sourcegitcommit: 654aecaeb5d3e3fe6bc926bafd6d5ace0d20a80e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/20/2019
ms.locfileid: "74245181"
---
# <a name="pimpl-for-compile-time-encapsulation-modern-c"></a>編譯時期封裝的 Pimpl (現代 C++)

*Pimpl*的方法是用來C++隱藏執行的現代化技術，可將結合性降至最低，以及分隔介面。 Pimpl 是「執行指標」的簡短。 您可能已經熟悉此概念，但可透過其他名稱（例如 Cheshire Cat 或編譯器防火牆）來加以瞭解。

## <a name="why-use-pimpl"></a>為何要使用 pimpl？

以下是 pimpl 的方法可以改善軟體發展生命週期的方式：

- 編譯相依性的小化。

- 區隔介面和實作為區隔。

- 相容.

## <a name="pimpl-header"></a>Pimpl 標頭

```cpp
// my_class.h
class my_class {
   //  ... all public and protected stuff goes here ...
private:
   class impl; unique_ptr<impl> pimpl; // opaque type here
};
```

Pimpl 的用法可避免重建級聯和脆弱物件版面配置。 它非常適合（可轉移）的熱門類型。

## <a name="pimpl-implementation"></a>Pimpl 執行

定義 .cpp 檔案中的 `impl` 類別。

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

## <a name="best-practices"></a>最佳作法

請考慮是否要新增對非擲回交換特製化的支援。

## <a name="see-also"></a>另請參閱

[歡迎回到C++](../cpp/welcome-back-to-cpp-modern-cpp.md)<br/>
[C++ 語言參考](../cpp/cpp-language-reference.md)<br/>
[C++ 標準程式庫](../standard-library/cpp-standard-library-reference.md)
