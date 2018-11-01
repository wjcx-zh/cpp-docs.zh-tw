---
title: PgoAutoSweep
ms.date: 03/14/2018
f1_keywords:
- PgoAutoSweep
- PogoAutoSweepA
- PogoAutoSweepW
ms.openlocfilehash: 356504da91a6778b5e873ca218df01944461d59c
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50456637"
---
# <a name="pgoautosweep"></a>PgoAutoSweep

`PgoAutoSweep` 將目前的設定檔計數器資訊儲存至檔案，並再重設計數器。 在訓練，以從執行中的程式中寫入.pgc 檔供稍後使用最佳化組建中的所有設定檔資料的特性指引最佳化期間使用函式。

## <a name="syntax"></a>語法

```cpp
void PgoAutoSweep(const char* name);    // ANSI/MBCS
void PgoAutoSweep(const wchar_t* name); // UNICODE
```

### <a name="parameters"></a>參數

*name*<br/>
已儲存的.pgc 檔識別字串。

## <a name="remarks"></a>備註

您可以呼叫`PgoAutoSweep`從您的應用程式，以儲存並在應用程式執行期間重設的設定檔資料，在任何時間點。 在已檢測的組建中，`PgoAutoSweep`擷取目前的程式碼剖析資料、 將它儲存在檔案中，及重設的設定檔的計數器。 它相當於呼叫[pgosweep](pgosweep.md)命令可執行檔中的特定點。 在最佳化組建中，`PgoAutoSweep`不會執行任何作業。

已儲存的設定檔計數器資料放在名為*base_name*-*名稱*！*值*.pgc，其中*base_name*是可執行檔的主檔名*名稱*參數傳遞至`PgoAutoSweep`，並*值*是唯一的值，通常是單純遞增數字，以防止檔案名稱衝突。

所建立的.pgc 檔案`PgoAutoSweep`必須合併的.pgd 檔，用來建立最佳化的可執行檔。 您可以使用[pgomgr](pgomgr.md)命令來進行合併。

您可以傳遞合併的.pgd 檔的名稱給連結器最佳化在建置期間使用**PGD =**_filename_引數[/USEPROFILE](useprofile.md)連結器選項，或使用已被取代 **/PGD**連結器選項。 如果您合併的.pgc 檔案檔案名*base_name*.pgd，您不需要在命令列上指定檔名，因為依預設，連結器會挑選出這個檔案名稱。

`PgoAutoSweep`函式可讓您維護的執行緒安全的設定建立時指定的已檢測的組建。 如果您使用預設設定，或指定**NOEXACT**引數[/GENPROFILE 或 /FASTGENPROFILE]()連結器選項，呼叫`PgoAutoSweep`不具備執行緒安全。 **精確**引數會建立執行緒安全且更精確，但速度較慢、 已檢測的可執行檔。

## <a name="requirements"></a>需求

|常式傳回的值|必要的標頭|
|-------------|---------------------|
|`PgoAutoSweep`|\<pgobootrun.h>|

可執行檔必須包含 pgobootrun.lib 檔中連結的程式庫。 此檔案包含在您的 Visual Studio 安裝，每個支援的架構的 VC 程式庫目錄中。

## <a name="example"></a>範例

以下範例使用`PgoAutoSweep`建立兩個。在執行期間不同時間點的 PGC 檔案。 第一個包含描述執行階段行為，直到資料`count`等於 3，而第二個包含之前終止應用程式的這個時間點之後所收集的資料。

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

在開發人員命令提示字元中，編譯物件檔案的程式碼使用下列命令：

`cl /c /GL /W4 /EHsc /O2 pgoautosweep.cpp`

使用此命令，然後產生經過檢的組建進行訓練：

`link /LTCG /genprofile pgobootrun.lib pgoautosweep.obj`

執行已檢測的可執行檔擷取定型資料。 若要呼叫的資料輸出`PgoAutoSweep`會儲存在檔名為 pgoautosweep func1 ！ 1.pgc 和 pgoautosweep func2 ！ 1.pgc。 執行程式的輸出應該看起來像這樣：

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

此命令的輸出看起來像這樣：

```Output
Microsoft (R) Profile Guided Optimization Manager 14.13.26128.0
Copyright (C) Microsoft Corporation. All rights reserved.

Merging pgoautosweep-func1!1.pgc
pgoautosweep-func1!1.pgc: Used  3.8% (22304 / 589824) of total space reserved.  0.0% of the counts were dropped due to overflow.
Merging pgoautosweep-func2!1.pgc
pgoautosweep-func2!1.pgc: Used  3.8% (22424 / 589824) of total space reserved.  0.0% of the counts were dropped due to overflow.
```

現在您可以使用這項訓練資料來產生最佳化的組建。 若要建置最佳化的可執行檔中使用下列命令：

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
