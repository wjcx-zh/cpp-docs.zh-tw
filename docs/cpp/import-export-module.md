---
title: 模組、匯入、匯出
ms.date: 12/12/2019
f1_keywords:
- module_cpp
- import_cpp
- export_cpp
helpviewer_keywords:
- modules [C++]
- modules [C++], import
- modules [C++], export
description: 使用匯入和匯出宣告來存取和，以發行指定模組中所定義的類型和函數。
ms.openlocfilehash: ae28bce8e06840cafa5c92521f6e9a62aa5bfde6
ms.sourcegitcommit: a5fa9c6f4f0c239ac23be7de116066a978511de7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/20/2019
ms.locfileid: "75301453"
---
# <a name="module-import-export"></a>模組、匯入、匯出

**模組**、匯**入**和**匯出**宣告可在 c + + 20 中使用，而且需要[/experimental： module](../build/reference/experimental-module.md)編譯器參數和[/std： C + + 最新版本](../build/reference/std-specify-language-standard-version.md)。 如需詳細資訊，請參閱[中C++的模組總覽](modules-cpp.md)。

## <a name="module"></a>name

將**模組**宣告放在模組執行檔案的開頭，以指定檔案內容屬於命名模組。

```cpp
module ModuleA;
```

## <a name="export"></a>匯出

針對模組的主要介面檔案使用**匯出模組**宣告，其副檔名必須是**ixx**：

```cpp
export module ModuleA;
```

在介面檔案中，針對要做為公用介面一部分的名稱使用**export**修飾詞：

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

匯入模組的程式碼看不到非匯出的名稱：

```cpp
//MyProgram.cpp

import module ModuleA;

void main() {
  Bar::f(); // OK
  Bar::d(); // OK
  Bar::internal_f(); // Ill-formed: error C2065: 'internal_f': undeclared identifier
}
```

**Export**關鍵字可能不會出現在模組執行檔案中。 當**匯出**套用至命名空間名稱時，會匯出命名空間中的所有名稱。

## <a name="import"></a>匯入

使用匯**入**宣告，讓模組的名稱可在您的程式中顯示。 匯入宣告必須出現在模組宣告之後，以及任何 #include 指示詞之後，但在檔案中的任何宣告之前。

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

## <a name="remarks"></a>備註

匯**入**和**模組**只有在邏輯行開頭出現時，才會被視為關鍵字：

```cpp

// OK:
module ;
module module-name
import :
import <
import "
import module-name
export module ;
export module module-name
export import :
export import <
export import "
export import module-name

// Error:
int i; module ;
```

**Microsoft 特定的**

在 Microsoft C++中，權杖匯**入**和**模組**一律是識別碼，而絕不會使用關鍵字做為宏的引數。

### <a name="example"></a>範例

```cpp
#define foo(…) __VA_ARGS__
foo(
import // Always an identifier, never a keyword
)
```

**結束 Microsoft 專有**

## <a name="see-also"></a>請參閱

[中的模組總覽C++](modules-cpp.md)
