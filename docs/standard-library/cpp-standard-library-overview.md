---
title: C++ 標準程式庫概觀
ms.date: 11/04/2016
helpviewer_keywords:
- headers, C++ library
- C++ Standard Library
- libraries, Standard C++
- C++ Standard Library, headers
ms.assetid: 7acb83a4-da73-4ad3-bc30-a71289db7f60
ms.openlocfilehash: 7b1e5226db751605d5352b1c5195759c34d080f5
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/24/2019
ms.locfileid: "68452443"
---
# <a name="c-standard-library-overview"></a>C++ 標準程式庫概觀

所有 C++ 程式庫實體都會在一或多個標準標頭中宣告或定義。 此實作為\< C++標準不需要的兩個額外\<標頭: hash_map > 和 hash_set >。 如需此實作支援的完整標頭清單，請參閱[標頭檔參考資料](../standard-library/cpp-standard-library-header-files.md)。

C++ 程式庫的獨立式實作僅提供這些標頭的子集：

|||
|-|-|
|[\<cstddef>](../standard-library/cstddef.md)|[\<cstdlib>](../standard-library/cstdlib.md) (至少宣告 `abort`、`atexit` 和 `exit` 函式)|
|[\<exception>](../standard-library/exception.md)|[\<limits>](../standard-library/limits.md)|
|[\<new>](../standard-library/new.md)|[\<cstdarg>](../standard-library/cstdarg.md)|

C++ 程式庫標頭有兩個更廣泛的細分：

- [iostreams](../standard-library/iostreams-conventions.md) 慣例。

- [C++ 標準程式庫參考資料](../standard-library/cpp-standard-library-reference.md)慣例。

本節包含下列小節：

- [使用 C++ 程式庫標頭](../standard-library/using-cpp-library-headers.md)

- [C++ 程式庫慣例](../standard-library/cpp-library-conventions.md)

- [iostreams 慣例](../standard-library/iostreams-conventions.md)

- [C++ 程式啟動和終止](../standard-library/cpp-program-startup-and-termination.md)

- [安全程式庫：C++ 標準程式庫](../standard-library/safe-libraries-cpp-standard-library.md)

- [Checked Iterators](../standard-library/checked-iterators.md)

- [Debug Iterator Support](../standard-library/debug-iterator-support.md)

- [C++ 標準程式庫參考資料](../standard-library/cpp-standard-library-reference.md)

- [C++ 標準程式庫中的執行緒安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)

- [stdext 命名空間](../standard-library/stdext-namespace.md)

- [規則運算式 (C++)](../standard-library/regular-expressions-cpp.md)

如需 Visual C++ 執行階段程式庫的詳細資訊，請參閱 [CRT 程式庫功能](../c-runtime-library/crt-library-features.md)。

## <a name="see-also"></a>另請參閱

[C++ 標準程式庫](../standard-library/cpp-standard-library-reference.md)
