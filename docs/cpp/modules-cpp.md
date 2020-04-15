---
title: C++ 中的模組概觀
ms.date: 12/13/2019
helpviewer_keywords:
- modules [C++]
- modules [C++], overview
description: C++20 中的模組提供了標頭檔的現代替代方法。
ms.openlocfilehash: cd45be1dee888c8caeb65b7ff002ac8fee1ecbe1
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81370764"
---
# <a name="overview-of-modules-in-c"></a>C++ 中的模組概觀

C++20 引入了*模組*,這是C++庫和程式元件化的現代解決方案。 模組是一組原始程式碼檔,它們獨立於導入它們的[翻譯單元](https://wikipedia.org/wiki/Translation_unit_(programming))進行編譯。 模組消除或大大減少了與使用標頭文件相關的許多問題,還可能減少編譯時間。 模組中聲明的宏、預處理器指令和非匯出名稱不可見,因此對導入模組的翻譯單元的編譯沒有影響。 您可以按任意順序導入模組,而無需考慮宏重新定義。 匯入翻譯單元中的聲明不參與導入模組中的重載解析或名稱尋找。 編譯一次模組后,結果將存儲在描述所有匯出類型、函數和範本的二進位檔中。 該檔的處理速度可以比標頭檔快得多,並且編譯器可以在專案中導入模組的每個位置重用該檔。

模組可以並排使用,與頭檔一起使用。 C++源檔可以導入模組,也可以#include頭檔。 在某些情況下,頭檔可以作為模組導入,而不是由預處理器以文本#included。 我們建議新專案盡可能使用模組而不是頭檔。 對於正在積極開發的大型現有專案,我們建議您嘗試將舊標頭轉換為模組,以查看是否有效減少了編譯時間。

## <a name="enable-modules-in-the-microsoft-c-compiler"></a>開啟 Microsoft C++編譯器中的模組

自 Visual Studio 2019 版本 16.2 起,模組未在 Microsoft C++編譯器中完全實現。 您可以使用模組功能創建單分區模組並導入 Microsoft 提供的標準庫模組。 要啟用對模組的支援,使用[/實驗:模組](../build/reference/experimental-module.md)和[/std:c_最新](../build/reference/std-specify-language-standard-version.md)編譯。 在視覺化工作室專案中,右鍵按下**解決方案資源管理員**中的專案節點並選擇**屬性**。 將 **「設定**」下拉清單**設定為「所有設定**」,然後選擇**配置屬性** > **C/C++** > **語言** > **啟用C++模組(實驗)。**

模組和使用它的代碼必須使用相同的編譯器選項進行編譯。

## <a name="consume-the-c-standard-library-as-modules"></a>將C++標準函式庫用作模組

儘管 C++20 標準未指定,但 Microsoft 允許將其 C++標準庫的實現作為模組導入。 通過將C++標準庫導入為模組,而不是通過頭檔#including它,您可以根據專案的大小加快編譯時間。 該庫已元件化為以下模組:

- std.regex 提供標\<頭 正規表示式>的內容
- std.filesystem 提供\<標頭 檔案系統的內容>
- std.memory 提供標\<頭 記憶體>
- std.streading 提供標\<頭 原子\<\<>、condition_variable>、 未來>、\<互斥>、shared_mutex>\<和\<線程>
- std.core 提供C++標準庫中的其他所有內容

要使用這些模組,只需將導入聲明添加到原始程式碼檔的頂部即可。 例如：

```cpp
import std.core;
import std.regex;
```

要使用 Microsoft 標準庫模組,請使用[/EHsc](../build/reference/eh-exception-handling-model.md)和[/MD](../build/reference/md-mt-ld-use-run-time-library.md)選項編譯程式。

## <a name="basic-example"></a>基本範例

下面的範例顯示了名為**Foo.ixx**的源檔中的簡單模組定義。 Visual Studio 中的模組介面檔需要 **.ixx**擴展名。 在此範例中,介面檔包含函數定義以及聲明。 但是,定義也可以放置在一個或多個單獨的檔中(如後面的示例所示)。 **匯出模組 Foo**語句指示此檔`Foo`是稱為 模組的主介面。 `f()`上的**匯出**修改器指示當由其他程式或模組導`Foo`入時 ,此函數將可見。 請注意,模組參考命名空間`Bar`。

```cpp
export module Foo;

#define ANSWER 42

namespace Bar
{
   int f_internal() {
        return ANSWER;
      }

   export int f() {
      return f_internal();
   }
}
```

檔**MyProgram.cpp**使用**匯入**聲明訪問由`Foo`匯出的名稱。 請注意,該名稱`Bar`在此處可見,但不是其所有成員。 另請注意,宏`ANSWER`不可見。

```cpp

import Foo;
import std.core;

using namespace std;

int main()
{
   cout << "The result of f() is " << Bar::f() << endl; // 42
   // int i = Bar::f_internal(); // C2039
   // int j = ANSWER; //C2065
}

```

導入聲明只能出現在全域作用域中。

## <a name="implementing-modules"></a>實現模組

您可以創建一個包含單個介面檔 (.ixx) 的模組,該檔匯出名稱,並包含所有函數和類型的實現。 您還可以將實現放在一個或多個單獨的實現檔中,類似於 .h 和 .cpp 檔案的使用方式。 **匯出**關鍵字僅在介面檔中使用。 實現檔可以**匯入**另一個模組,但不能**匯出**任何名稱。 可以使用任何副檔名命名實現檔。 介面檔和支援它的實現檔集被視為一種稱為*模組單元*的特殊類型的翻譯單元。 在任何實現檔中聲明的名稱在同一模組單元中的所有其他文件中自動可見。

對於較大的模組,您可以將模組拆分為多個模組單元,稱為*分區*。 每個分區由一個或多個實現文件支援的介面文件組成。 (截至 Visual Studio 2019 版本 16.2,分區尚未完全實現。

## <a name="modules-namespaces-and-argument-dependent-lookup"></a>模組、命名空間與與參數相關的尋找

模組中的命名空間規則與任何其他代碼的規則相同。 如果匯出命名空間中的聲明,則封閉命名空間(不包括非匯出成員)也將隱式匯出。 如果顯式匯出命名空間,則匯出該命名空間定義中的所有聲明。

在導入轉換單元中執行與參數相關的查找重載解析時,編譯器將在同一轉換單元(包括模組介面)中聲明的函數視為定義函數參數類型的函數。

### <a name="module-partitions"></a>模組分割區

> [!NOTE]
> 此部分是完整性的提供。 分區尚未在 Microsoft C++編譯器中實現。

模組可以元件化為分區,每個*分區*由介面檔和零個或多個實現文件組成。 模組分區類似於模組,只不過它共用整個模組中所有聲明的擁有權。 分區介面文件匯出的所有名稱都由主介面檔導入和重新匯出。 分區的名稱必須以模組名稱後跟冒號開頭。 任何分區中的聲明在整個模組中可見。 無需採取特殊預防措施即可避免單定義規則 (ODR) 錯誤。 您可以在一個分區中聲明名稱(函數、類等),並在另一個分區中定義它。 分割區實現檔案開始如下所示:

```cpp
module Foo:part1
```

分割區介面檔開始如下所示:

```cpp
export module Foo:part1
```

要造訪另一個分區中的聲明,分區必須匯入它,但它只能使用分區名稱,而不能使用模組名稱:

```cpp
module Foo:part2;
import :part1;
```

主介面單元必須匯入和重新匯出模組的所有介面分區檔,如下所示:

```cpp
export import :part1
export import :part2
...
```

主介面單元可以導入分區實現檔,但不能匯出這些文件,因為不允許匯出任何名稱。 這使模組能夠將實現詳細資訊保留到模組的內部。

## <a name="modules-and-header-files"></a>模組和標頭檔案

透過指令放在模組聲明之前,`#include`可以在模組源檔中包含標頭檔。 這些文件被認為是在*全域模組片段*中。 模組只能看到它顯式包含的標頭中的*全域模組片段*中的名稱。 全域模組片段僅包含實際使用的符號。

```cpp
// MyModuleA.cpp

#include "customlib.h"
#include "anotherlib.h"

import std.core;
import MyModuleB;

//... rest of file
```

您可以使用傳統的標頭檔案來控制匯入的模組:

```cpp
// MyProgram.h
import std.core;
#ifdef DEBUG_LOGGING
import std.filesystem;
#endif
```

### <a name="imported-header-files"></a>匯入的標頭檔

> [!NOTE]
> 本節僅供參考。 舊導入尚未在 Microsoft C++編譯器中實現。

某些標頭足夠自包含,允許使用**import**關鍵字引入它們。 導入的標頭和導入模組之間的主要區別是,標頭中的任何預處理器定義在導入語句后立即在導入程式中可見。 ( 這個標頭包含的檔案中預先定義*not*。

```cpp
import <vector>
import "myheader.h"
```

## <a name="see-also"></a>另請參閱

[模組、匯入、匯出](import-export-module.md)
