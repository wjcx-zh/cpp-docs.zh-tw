---
title: PgoAutoSweep
ms.date: 07/02/2019
f1_keywords:
- PgoAutoSweep
- PogoAutoSweepA
- PogoAutoSweepW
ms.openlocfilehash: 57bcd1b2e9f0a3312867c4373fd1e50bcf91576e
ms.sourcegitcommit: 9b904e490b1e262293a602bd1291a8f3045e755b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/03/2019
ms.locfileid: "67552249"
---
# <a name="pgoautosweep"></a>PgoAutoSweep

`PgoAutoSweep`將目前的設定檔計數器資訊儲存至檔案，然後重設計數器。 在特性指引優化訓練期間使用函式，以將執行中程式`.pgc`的所有設定檔資料寫入檔案，以供稍後在優化組建中使用。

## <a name="syntax"></a>語法

```cpp
void PgoAutoSweep(const char* name);    // ANSI/MBCS
void PgoAutoSweep(const wchar_t* name); // UNICODE
```

### <a name="parameters"></a>參數

*name*<br/>
已儲存`.pgc`盤案的識別字串。

## <a name="remarks"></a>備註

您可以從`PgoAutoSweep`應用程式呼叫，以在應用程式執行期間的任何時間點儲存和重設設定檔資料。 在檢測的組建中`PgoAutoSweep` ，會捕捉目前的分析資料、將它儲存在檔案中，然後重設設定檔計數器。 這相當於在您的可執行檔中的特定點呼叫[pgosweep](pgosweep.md)命令。 在優化的組建中`PgoAutoSweep` ，是一個無 op。

儲存的設定檔計數器資料會放在名為*base_name*-*名稱*的檔案中！*值*.pgc，其中*base_name*是可執行檔的基底名稱， *name*是傳遞至`PgoAutoSweep`的參數，而*value*是唯一值，通常是單純遞增的數位，以避免檔案名衝突。

所`.pgc`建立的檔案`PgoAutoSweep`必須合併到`.pgd`檔案中，以用來建立優化的可執行檔。 您可以使用[pgomgr](pgomgr.md)命令來執行合併。

您可以使用[/USEPROFILE](reference/useprofile.md)連結器選項的`.pgd` **PGD =**_filename_引數，或使用已被取代的 **/PGD**連結器選項，在優化組建期間將合併的檔案名稱傳遞至連結器。 如果您將檔案`.pgc`合併到名為*base_name*.pgd 的檔案中，則不需要在命令列上指定檔案名，因為連結器預設會挑選此檔案名。

`PgoAutoSweep`函式會維護已建立檢測的組建時所指定的執行緒安全性設定。 如果您使用預設設定，或指定[/GENPROFILE 或/FASTGENPROFILE](reference/genprofile-fastgenprofile-generate-profiling-instrumented-build.md)連結器選項的`PgoAutoSweep` **NOEXACT**引數，則對的呼叫不是安全線程。 **確切**的引數會建立安全線程、更精確但較緩慢的已檢測可執行檔。

## <a name="requirements"></a>需求

|常式傳回的值|必要的標頭|
|-------------|---------------------|
|`PgoAutoSweep`|\<pgobootrun. h>|

可執行檔必須在程式庫中包含 pgobootrun。 此檔案包含在您的 Visual Studio 安裝中，在每個支援的架構的 VC 程式庫目錄中。

## <a name="example"></a>範例

下列範例會使用`PgoAutoSweep` ，在執行`.pgc`期間于不同的點建立兩個檔案。 第一個包含描述執行時間行為的資料， `count`直到等於3為止，而第二個包含在此時間點之後所收集的資料，直到應用程式終止之前為止。

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

在開發人員命令提示字元中，使用下列命令將程式碼編譯成物件檔案：

`cl /c /GL /W4 /EHsc /O2 pgoautosweep.cpp`

然後，使用下列命令產生定型的已檢測組建：

`link /LTCG /genprofile pgobootrun.lib pgoautosweep.obj`

執行已檢測的可執行檔來捕獲定型資料。 呼叫所輸出的資料`PgoAutoSweep`會儲存在名為 pgoautosweep-func1！ 1. .pgc 和 pgoautosweep-func2！1的檔案中。 程式的輸出看起來應該像這樣：

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

藉由執行**pgomgr**命令，將儲存的資料合併到設定檔訓練資料庫中：

`pgoautosweep-func1!1.pgc pgoautosweep-func2!1.pgc`

此命令的輸出看起來會像這樣：

```Output
Microsoft (R) Profile Guided Optimization Manager 14.13.26128.0
Copyright (C) Microsoft Corporation. All rights reserved.

Merging pgoautosweep-func1!1.pgc
pgoautosweep-func1!1.pgc: Used  3.8% (22304 / 589824) of total space reserved.  0.0% of the counts were dropped due to overflow.
Merging pgoautosweep-func2!1.pgc
pgoautosweep-func2!1.pgc: Used  3.8% (22424 / 589824) of total space reserved.  0.0% of the counts were dropped due to overflow.
```

現在您可以使用這種訓練資料來產生優化的組建。 使用此命令來建立優化的可執行檔：

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

## <a name="see-also"></a>請參閱

[特性指引最佳化](profile-guided-optimizations.md)<br/>
[pgosweep](pgosweep.md)<br/>
