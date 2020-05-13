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
description: 使用導入和匯出聲明訪問並發佈指定模組中定義的類型和函數。
ms.openlocfilehash: a765e9a406660d3c945ef3d70754178b0648458c
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81374107"
---
# <a name="module-import-export"></a>模組、匯入、匯出

**模組**、**匯入**與**匯出**宣告在 C++20 中可用,並且需要[/實驗:模組](../build/reference/experimental-module.md)編譯器開關以及[/std:c_最新](../build/reference/std-specify-language-standard-version.md)。 有關詳細資訊,請參閱[C++ 中的模組概述](modules-cpp.md)。

## <a name="module"></a>module

將**模組**聲明放在模組實現檔的開頭,以指定檔案內容屬於命名模組。

```cpp
module ModuleA;
```

## <a name="export"></a>匯出

設定模組的主介面檔使用**匯出模組**聲明,該檔案必須具有延伸**名 .ixx**:

```cpp
export module ModuleA;
```

在介面檔中,對打算成為公共介面一部分的名稱使用**匯出**修改器:

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

匯入模組的代碼看不到非匯出的名稱:

```cpp
//MyProgram.cpp

import module ModuleA;

int main() {
  Bar::f(); // OK
  Bar::d(); // OK
  Bar::internal_f(); // Ill-formed: error C2065: 'internal_f': undeclared identifier
}
```

**匯出**關鍵字可能不會顯示在模組實現檔中。 當**匯出**應用於命名空間名稱時,將匯出命名空間中的所有名稱。

## <a name="import"></a>入口

使用**導入**聲明使模組的名稱在程式中可見。 導入聲明必須出現在模組聲明之後和任何#include指令之後,但在檔中的任何聲明之前。

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

**匯入**與**模組**只在邏輯行的開頭出現時被視為關鍵字:

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

在 Microsoft C++中,**導入**的權杖和**模組**在用作巨集的參數時始終是識別碼,從不為關鍵字。

### <a name="example"></a>範例

```cpp
#define foo(…) __VA_ARGS__
foo(
import // Always an identifier, never a keyword
)
```

**結束 Microsoft 專有**

## <a name="see-also"></a>另請參閱

[C++ 中的模組概觀](modules-cpp.md)
