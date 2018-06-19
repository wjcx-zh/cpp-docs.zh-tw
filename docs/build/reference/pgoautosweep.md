---
title: PgoAutoSweep |Microsoft 文件
ms.custom: ''
ms.date: 03/14/2018
ms.technology:
- cpp-tools
ms.topic: reference
dev_langs:
- C++
f1_keywords:
- PgoAutoSweep
- PogoAutoSweepA
- PogoAutoSweepW
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 988a73dd8c4ad6929ef04691ad1959df7ea7bdd7
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
ms.locfileid: "32379493"
---
# <a name="pgoautosweep"></a>PgoAutoSweep

`PgoAutoSweep` 將目前的設定檔計數器資訊儲存到檔案，然後再重設計數器。 在訓練，從正在執行的程式中寫入.pgc 檔案供稍後使用，在最佳化組建中的所有設定檔資料的特性指引最佳化期間使用函數。

## <a name="syntax"></a>語法

```cpp
void PgoAutoSweep(const char* name);    // ANSI/MBCS
void PgoAutoSweep(const wchar_t* name); // UNICODE
```

### <a name="parameters"></a>參數

*name*<br/>
已儲存的.pgc 檔案識別字串。

## <a name="remarks"></a>備註

您可以呼叫`PgoAutoSweep`從您的應用程式，以儲存並在應用程式執行期間重設的設定檔資料，在任何時間點。 在檢測建置中，`PgoAutoSweep`擷取目前的程式碼剖析資料、 將它儲存在檔案中，及重設的設定檔的計數器。 它相當於呼叫[pgosweep](pgosweep.md)命令可執行檔中的特定點。 在最佳化組建中，`PgoAutoSweep`沒有任何作業。

儲存的設定檔計數器資料放在名為*base_name*-*名稱*！*值*.pgc，其中*base_name*是基底名稱的可執行檔，*名稱*參數傳遞至`PgoAutoSweep`，和*值*是唯一的值，通常是單純遞增數字，以防止檔案名稱衝突。

所建立的.pgc 檔案`PgoAutoSweep`必須合併至.pgd 檔，以用來建立最佳化的可執行檔。 您可以使用[pgomgr](pgomgr.md)命令來進行合併。

您可以合併的.pgd 檔的名稱給連結器最佳化建置期間使用傳遞**PGD =**_filename_引數[/USEPROFILE](useprofile.md)連結器選項，或由使用已被取代 **/PGD**連結器選項。 如果您合併的.pgc 檔案到名為*base_name*.pgd，您不需要指定檔名，在命令列，因為連結器挑選預設此檔案名稱。

`PgoAutoSweep`函式會維護的執行緒安全的設定建立時指定檢測的建置。 如果您使用預設設定，或指定**NOEXACT**引數[/GENPROFILE 或 /FASTGENPROFILE]()連結器選項，呼叫`PgoAutoSweep`不是安全執行緒。 **精確**引數建立具備執行緒安全，更精確，但速度較慢，已檢測的可執行檔。

## <a name="requirements"></a>需求

|常式|必要的標頭|
|-------------|---------------------|
|`PgoAutoSweep`|\<pgobootrun.h>|

可執行檔必須包含 pgobootrun.lib 檔中連結的程式庫。 這個檔案隨附於 Visual Studio 安裝，每個支援架構的 VC 程式庫目錄中。

## <a name="example"></a>範例

使用下列範例`PgoAutoSweep`來建立兩個。PGC 檔案在執行期間不同時間點。 第一個包含描述執行階段行為，直到資料`count`等於 3，而第二個包含之前終止應用程式在這個點之後所收集的資料。

```cpp
// pgoautosweep.cpp
// Compile by using: cl /c /GL /W4 /EHsc /O2 pgoautosweep.cpp
// Link to instrument: link /LTCG /genprofile pgobootrun.lib pgoautosweep.obj
// Run to generate data: pgoautosweep
// Merge data by using command line pgomgr tool:
// pgomgr /merge pgoautosweep-func1!1.pgc pgoautosweep-func2!1.pgc pgoautosweep.pgd
// Link to optimize: link /LTCG /useprofile pgobootrun.lib pgoautosweep.obj

#include <iostream>
#include <windows.h>
#include <pgobootrun.h>

void func2(int count)
{
    std::cout << "hello from func2 " << count << std::endl;
    Sleep(2000);
}

void func1(int count)
{
    std::cout << "hello from func1 " << count << std::endl;
    Sleep(2000);
}

int main()
{
    int count = 10;
    while (count--)
    {
        if (count < 3)
            func2(count);
        else
        {
            func1(count);
            if (count == 3)
            {
                PgoAutoSweep("func1");
            }
        }
    }
    PgoAutoSweep("func2");
}
```

在開發人員命令提示字元，編譯目的檔的程式碼使用這個命令：

`cl /c /GL /W4 /EHsc /O2 pgoautosweep.cpp`

使用這個命令，然後產生經過檢的組建進行定型：

`link /LTCG /genprofile pgobootrun.lib pgoautosweep.obj`

執行檢測可執行檔擷取定型資料。 所呼叫的資料輸出`PgoAutoSweep`會儲存在檔名為 pgoautosweep func1 ！ 1.pgc 和 pgoautosweep func2 ！ 1.pgc。 在執行程式的輸出應該看起來像這樣：

```Output
hello from func1 9
hello from func1 8
hello from func1 7
hello from func1 6
hello from func1 5
hello from func1 4
hello from func1 3
hello from func2 2
hello from func2 1
hello from func2 0
```

合併設定檔訓練資料庫中的已儲存的資料，藉由執行**pgomgr**命令：

`pgoautosweep-func1!1.pgc pgoautosweep-func2!1.pgc`

這個命令的輸出看起來像這樣：

```Output
Microsoft (R) Profile Guided Optimization Manager 14.13.26128.0
Copyright (C) Microsoft Corporation. All rights reserved.

Merging pgoautosweep-func1!1.pgc
pgoautosweep-func1!1.pgc: Used  3.8% (22304 / 589824) of total space reserved.  0.0% of the counts were dropped due to overflow.
Merging pgoautosweep-func2!1.pgc
pgoautosweep-func2!1.pgc: Used  3.8% (22424 / 589824) of total space reserved.  0.0% of the counts were dropped due to overflow.
```

現在您可以使用此定型資料來產生最佳化的組建。 若要建置最佳化可執行檔中使用此命令：

`link /LTCG /useprofile pgobootrun.lib pgoautosweep.obj`

```Output
Microsoft (R) Incremental Linker Version 14.13.26128.0
Copyright (C) Microsoft Corporation.  All rights reserved.

Merging pgoautosweep!1.pgc
pgoautosweep!1.pgc: Used  3.9% (22904 / 589824) of total space reserved.  0.0% of the counts were dropped due to overflow.
  Reading PGD file 1: pgoautosweep.pgd
Generating code

0 of 0 ( 0.0%) original invalid call sites were matched.
0 new call sites were added.
294 of 294 (100.00%) profiled functions will be compiled for speed
348 of 1239 inline instances were from dead/cold paths
294 of 294 functions (100.0%) were optimized using profile data
16870 of 16870 instructions (100.0%) were optimized using profile data
Finished generating code
```

## <a name="see-also"></a>另請參閱

[特性指引最佳化](profile-guided-optimizations.md)<br/>
[pgosweep](pgosweep.md)<br/>
