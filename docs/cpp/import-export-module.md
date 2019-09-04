---
title: 模組、匯入、匯出
ms.date: 07/15/2019
f1_keywords:
- module_cpp
- import_cpp
- export_cpp
helpviewer_keywords:
- modules [C++]
- modules [C++], import
- modules [C++], export
description: 使用 import 語句來存取指定模組中所定義的類型和函數。
ms.openlocfilehash: ee1d50a76a3304359c0771aa0174968439f5faa4
ms.sourcegitcommit: fd0f8839da5c6a3663798a47c6b0bb6e63b518bd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/04/2019
ms.locfileid: "70273630"
---
# <a name="module-import-export"></a>模組、匯入、匯出

**模組**、匯**入**和**匯出**關鍵字可在 c + + 20 中使用, 而且需要[/experimental: module](../build/reference/experimental-module.md)編譯器參數和[/std: C + + 最新版本](../build/reference/std-specify-language-standard-version.md)。 如需詳細資訊, 請參閱[中C++的模組總覽](modules-cpp.md)。

## <a name="module"></a>name

在模組執行檔案的開頭使用**module**語句, 以指定檔案內容屬於命名模組。 

```cpp
module ModuleA;
```

## <a name="export"></a>匯出

針對模組的主要介面檔案使用**export module**語句, 其副檔名必須是**ixx**:

```cpp
export module ModuleA;
```

在介面檔案中, 針對要做為公用介面一部分的名稱使用**export**修飾詞:

```cpp
// ModuleA.ixx

export module ModuleA;

namespace Bar
{
   export int f();
   export double d();
   double internal_f(); // not exported
}
```

匯入模組的程式碼看不到非匯出的名稱:

```cpp
//MyProgram.cpp

import module ModuleA;

void main() {
  Bar::f(); // OK
  Bar::d(); // OK
  Bar::internal_f(); // Ill-formed: error C2065: 'internal_f': undeclared identifier
}
```

**Export**關鍵字可能不會出現在模組執行檔案中。 當**export**修飾詞套用至命名空間名稱時, 就會匯出命名空間中的所有名稱。

## <a name="import"></a>import

使用**import**語句, 讓模組的名稱可在您的程式中顯示。 Import 語句必須出現在 module 語句之後, 以及任何 #include 指示詞之後, 但在檔案中的任何宣告之前。

```cpp
module ModuleA;

#include "custom-lib.h"
import std.core;
import std.regex;
import ModuleB;

// begin declarations here:
template <class T>
class Baz
{...};
```

## <a name="see-also"></a>另請參閱

[中的模組總覽C++](modules-cpp.md)
