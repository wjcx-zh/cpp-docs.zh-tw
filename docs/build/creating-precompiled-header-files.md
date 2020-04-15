---
title: 先行編譯標頭檔
ms.date: 10/24/2019
helpviewer_keywords:
- precompiled header files, creating
- PCH files, creating
- cl.exe compiler, precompiling code
- .pch files, creating
ms.assetid: e2cdb404-a517-4189-9771-c869c660cb1b
ms.openlocfilehash: 158301ec3caacced1663892071b17ef2b8f8e741
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81328663"
---
# <a name="precompiled-header-files"></a>先行編譯標頭檔

從 Visual Studio 建立新項目時,將加入名為*pch.h* *的預寫標頭檔*。 (在 Visual Studio 2017 和更早版本中,該檔稱為*stdafx.h*.)該檔的目的是加快生成過程。 任何穩定的標頭檔(例如標準庫標頭(如`<vector>`)都應在此處包含。 僅當預編譯標頭或其包含的任何檔被修改時,才會編譯它。 如果僅在專案原始程式碼中進行更改,則生成將跳過預編譯標頭的編譯。

預寫標頭的編譯器選項為[/Y](reference/y-precompiled-headers.md)。 在項目屬性頁中,選項位於**設定屬性> C/C++>预编译标头**。 您可以選擇不使用預編譯的標頭,也可以指定標頭檔名以及輸出檔的名稱和路徑。

## <a name="custom-precompiled-code"></a>自訂預編譯碼

對於需要大量時間構建的大型專案,您可能需要考慮創建自訂預編譯檔。 Microsoft C 和 C++ 編譯器提供對任何 C 或 C++ 程式碼進行先行編譯的選項，包括內嵌程式碼。 您可以使用這項效能功能來編譯穩定的程式碼主體，並將程式碼的編譯狀態儲存在檔案中，然後在後續編譯期間，將先行編譯的程式碼與仍在開發中的程式碼結合。 由於穩定的程式碼不需要重新編譯，因此每個後續編譯的速度會更快。

## <a name="when-to-precompile-source-code"></a>先行編譯原始程式碼的時機

預編譯代碼在開發週期中非常有用,用於縮短編譯時間,尤其是在以下情況:

- 您始終使用不常更改的大量代碼。

- 您的程式包含多個模組,所有這些模組都使用一組標準的包含檔和相同的編譯選項。 在這種情況下,所有包含檔都可以預編譯為一個預編譯標頭。

第一個編譯(創建預編譯標頭 (PCH) 檔)比後續編譯長一點。 通過包括預編譯的代碼,後續編譯可以更快地進行。

您可以預編譯 C 和C++程式。 在C++程式設計中,通常的做法是將類介面資訊分離到頭檔中。 這些標頭檔以後可以包含在使用類的程式中。 通過預編譯這些標頭,可以減少程式編譯所需的時間。

> [!NOTE]
> 儘管每個源檔只能使用一個預編譯的標頭 (.pch) 檔,但可以在專案中使用多個 .pch 檔。

## <a name="two-choices-for-precompiling-code"></a>先行編譯程式碼的兩個選擇

您可以預編譯任何 C 或C++代碼;您不限於僅預編譯標頭檔。

預編譯需要規劃,但如果預編譯簡單標頭檔以外的原始程式碼,則預編譯速度會明顯加快。

當您知道原始碼使用常用的標頭檔集,但不按相同的順序包括它們,或者當您希望在預編譯中包括原始碼時,請預編譯代碼。

預編譯標頭選項為[/Yc(創建預編譯的標頭檔)](reference/yc-create-precompiled-header-file.md)和[/Yu(使用預編譯的標頭檔)。](reference/yu-use-precompiled-header-file.md) 使用 **/Yc**創建預編譯標頭。 當與可選的[hdrstop](../preprocessor/hdrstop.md)實用素一起使用時 **,/Yc**允許您預編譯標頭檔和原始程式碼。 選擇 **/Yu**以在現有編譯中使用現有的預編譯標頭。 您還可以使用 **/Fp**與 **/Yc**和 **/Yu**選項一起為預編譯標頭提供替代名稱。

**/Yu**和 **/Yc**的編譯器選項參考主題討論如何在開發環境中存取此功能。

## <a name="precompiled-header-consistency-rules"></a>先行編譯標頭的一致性規則

由於 PCH 檔包含有關電腦環境的資訊以及有關該程式的記憶體位址資訊,因此應僅在創建該程式的電腦上使用 PCH 檔。

## <a name="consistency-rules-for-per-file-use-of-precompiled-headers"></a>針對每個檔案使用的先行編譯標頭的一致性規則

[/Yu](reference/yu-use-precompiled-header-file.md)編譯器選項允許您指定要使用的 PCH 檔。

使用 PCH 檔時,編譯器將假定在創建 PCH 檔時有效的編譯環境(使用一致的編譯器選項、雜注等)有效,除非您另有說明。 如果編譯器檢測到不一致,它會發出警告,並儘可能識別不一致。 此類警告不一定表示 PCH 檔有問題;因此,這些警告並不一定表示 PCH 檔存在問題。他們只是警告你潛在的衝突。 PCH檔的一致性要求如下所述。

### <a name="compiler-option-consistency"></a>編譯器選項一致性

使用 PCH 檔時,以下編譯器選項可能會觸發不一致警告:

- 使用預處理器 (/D) 選項創建的巨集在創建 PCH 檔和當前編譯的編譯之間必須相同。 未檢查已定義的常量的狀態,但如果更改這些常量,則可能會出現不可預知的結果。

- PCH 檔案不適用於 /E 和 /EP 選項。

- 在使用 PCH 檔的後續編譯可以使用這些選項之前,必須使用生成瀏覽資訊 (/FR) 選項或排除局部變數 (/Fr) 選項創建 PCH 檔。

### <a name="c-70-compatible-z7"></a>C 7.0 相容 (/Z7)

如果此選項在創建 PCH 檔時有效,則使用 PCH 檔的後續編譯可以使用調試資訊。

如果在創建 PCH 檔時 C 7.0 相容 (/Z7) 選項無效,則使用 PCH 檔和 /Z7 的後續編譯將觸發警告。 除錯資訊放置在目前的 .obj 檔中,並且在 PCH 檔中定義的本地符號對除錯器不可用。

### <a name="include-path-consistency"></a>包括路徑一致性

PCH 檔不包含有關建立時有效的包含路徑的資訊。 使用 PCH 檔時,編譯器始終使用當前編譯中指定的包含路徑。

### <a name="source-file-consistency"></a>來源檔案一致性

指定「使用預編譯標頭檔 (/Yu)」選項時,編譯器將忽略將預編譯的原始程式碼中顯示的所有預處理器指令(包括雜註)。 此類預處理器指令指定的編譯必須與創建預編譯標頭檔 (/Yc) 選項的編譯相同。

### <a name="pragma-consistency"></a>實用一致性

在創建 PCH 檔期間處理的實用主義通常會影響隨後使用 PCH 檔的檔。 和`comment``message`雜注不會影響編譯的其餘部分。

這些雜注僅影響 PCH 檔中的代碼;它們不會影響隨後使用 PCH 檔案的代碼:

||||
|-|-|-|
|`comment`|`page`|`subtitle`|
|`linesize`|`pagesize`|`title`|
|`message`|`skip`||

這些雜注作為預編譯標頭的一部分保留,並影響使用預編譯標頭的編譯的其餘部分:

||||
|-|-|-|
|`alloc_text`|`include_alias`|`pack`|
|`auto_inline`|`init_seg`|`pointers_to_members`|
|`check_stack`|`inline_depth`|`setlocale`|
|`code_seg`|`inline_recursion`|`vtordisp`|
|`data_seg`|`intrinsic`|`warning`|
|`function`|`optimize`||

## <a name="consistency-rules-for-yc-and-yu"></a>/Yc 和 /Yu 的一致性規則

使用使用 /Yc 或 /Yu 創建的預編譯標頭時,編譯器會將當前編譯環境與創建 PCH 檔時存在的編譯環境進行比較。 請確保為當前編譯指定與前一個環境一致的環境(使用一致的編譯器選項、雜注等)。 如果編譯器檢測到不一致,它會發出警告,並儘可能識別不一致。 此類警告不一定表示 PCH 檔有問題;因此,這些警告並不一定表示 PCH 檔存在問題。他們只是警告你潛在的衝突。 以下各節解釋預編譯標頭的一致性要求。

### <a name="compiler-option-consistency"></a>編譯器選項一致性

此表列出了在使用預編譯標頭時可能引發不一致警告的編譯器選項:

|選項|名稱|規則|
|------------|----------|----------|
|/D|定義常量和巨集|創建預編譯標頭的編譯和當前編譯之間必須相同。 未檢查已定義的常量的狀態,但如果文件依賴於更改的常量的值,則可能會出現不可預知的結果。|
|/E 或 /EP|將預處理器輸出複製到標準輸出|預編譯標頭不適用於 /E 或 /EP 選項。|
|/Fr 或 /FR|產生微軟源瀏覽器資訊|對於 /Fr 和 /FR 選項在 /Yu 選項中有效,它們也必須在創建預編譯標頭時有效。 使用預編譯標頭的後續編譯也會生成源瀏覽器資訊。 瀏覽器資訊放置在單個 .sbr 檔中,其他檔以與 CodeView 資訊相同的方式引用這些資訊。 您不能覆蓋源瀏覽器資訊的位置。|
|/GA、/GD、/GE、/Gw 或 /GW|Windows 協定選項|創建預編譯標頭的編譯和當前編譯之間必須相同。 如果這些選項不同,則會生成警告消息。|
|/ZI|產生完整的除錯資訊|如果此選項在創建預編譯標頭時有效,則使用預編譯的後續編譯可以使用該調試資訊。 如果在創建預編譯標頭時 /Zi 無效,則使用預編譯和 /Zi 選項的後續編譯將觸發警告。 除錯資訊放置在目前的物件檔中,並且在預編譯標頭中定義的本機號對除錯器不可用。|

> [!NOTE]
> 預編譯標頭工具僅用於 C 和 C++源檔。

## <a name="using-precompiled-headers-in-a-project"></a>在專案中使用先行編譯的標頭

前面的各節概述了預編譯標頭:/Yc 和 /Yu、/Fp 選項和[hdrstop](../preprocessor/hdrstop.md)雜注。 本節介紹在專案中使用手動預編譯標頭選項的方法;它以一個範例 makefile 及其管理的代碼結束。

對於在專案中使用手動預編譯標頭選項的另一種方法,請研究在 Visual Studio 的預設設定期間創建的 MFC_SRC 目錄中的一個 makefile。 這些 makefile 採用與本節中介紹的方法類似的方法,但更多地利用了 Microsoft 程式維護實用程式 (NMAKE) 宏,並更好地控制了生成過程。

## <a name="pch-files-in-the-build-process"></a>建置程序中的 PCH 檔

軟體項目的代碼庫通常包含在多個 C 或 C++源檔、物件檔、庫和標頭檔中。 通常,makefile 將這些元素組合為可執行檔。 下圖顯示了使用預編譯標頭檔的 makefile 的結構。 此關係圖中的 NMAKE 宏名和檔名與[PCH 範例 Makefile](#sample-makefile-for-pch)和[PCH 範例代碼](#example-code-for-pch)中的範例代碼中的那些名稱一致。

該圖使用三個圖表設備來顯示生成過程的流。 命名矩形表示每個檔或宏;三個宏表示一個或多個檔。 已對區域表示每個編譯或連結操作。 箭號顯示在編譯或連結過程中組合的文件和宏。

![使用預編譯標頭檔的 makefile 的結構](media/vc30ow1.gif "使用預編譯標頭檔的 makefile 的結構") <br/>
使用預編譯標頭檔案的 Makefile 的結構

從關係圖的頂部開始,STABLEHDRS 和 BOUNDRY 都是 NMAKE 宏,其中列出了不需要重新編譯的檔。 這些檔案由命令字串編譯

`CL /c /W3 /Yc$(BOUNDRY) applib.cpp myapp.cpp`

僅當預編譯的標頭檔 (STABLE.pch) 不存在或對兩個巨集中列出的檔進行更改時。 在這兩種情況下,預編譯的標頭檔將僅包含來自 STABLEHDRS 宏中列出的檔的代碼。 列出要在 BOUNDRY 宏中預編譯的最後一個檔。

在這些宏中列出的檔可以是標頭檔或 C 或 C++原始檔。 (單個 PCH 檔不能同時用於 C 和 C++ 模組。請注意,您可以使用**hdrstop**宏在 BOUNDRY 檔中的某個點停止預編譯。 有關詳細資訊,請參閱[hdrstop。](../preprocessor/hdrstop.md)

APPLIB.obj 繼續向下表示最終應用程式中使用的支援代碼。 它創建自 APPLIB.cpp,UNSTABLEHDRS 宏中列出的檔,並從預編譯標頭中預編譯代碼。

MYAPP.obj 代表您的最終申請。 它創建於 MYAPP.cpp,即 UNSTABLEHDRS 宏中列出的檔,並從預編譯標頭中預編譯代碼。

最後,可執行檔(MYAPP)。EXE)是通過連結 OBJS 宏(APPLIB.obj 和 MYAPP.obj)中列出的文件創建的。

## <a name="sample-makefile-for-pch"></a>PCH 的 Makefile 範例

以下 makefile 使用巨集與 !如果!還!ENDIF 控制流命令結構,以簡化其對項目的適應。

```NMAKE
# Makefile : Illustrates the effective use of precompiled
#            headers in a project
# Usage:     NMAKE option
# option:    DEBUG=[0|1]
#            (DEBUG not defined is equivalent to DEBUG=0)
#
OBJS = myapp.obj applib.obj
# List all stable header files in the STABLEHDRS macro.
STABLEHDRS = stable.h another.h
# List the final header file to be precompiled here:
BOUNDRY = stable.h
# List header files under development here:
UNSTABLEHDRS = unstable.h
# List all compiler options common to both debug and final
# versions of your code here:
CLFLAGS = /c /W3
# List all linker options common to both debug and final
# versions of your code here:
LINKFLAGS = /nologo
!IF "$(DEBUG)" == "1"
CLFLAGS   = /D_DEBUG $(CLFLAGS) /Od /Zi
LINKFLAGS = $(LINKFLAGS) /COD
LIBS      = slibce
!ELSE
CLFLAGS   = $(CLFLAGS) /Oselg /Gs
LINKFLAGS = $(LINKFLAGS)
LIBS      = slibce
!ENDIF
myapp.exe: $(OBJS)
    link $(LINKFLAGS) @<<
$(OBJS), myapp, NUL, $(LIBS), NUL;
<<
# Compile myapp
myapp.obj  : myapp.cpp $(UNSTABLEHDRS)  stable.pch
    $(CPP) $(CLFLAGS) /Yu$(BOUNDRY)    myapp.cpp
# Compile applib
applib.obj : applib.cpp $(UNSTABLEHDRS) stable.pch
    $(CPP) $(CLFLAGS) /Yu$(BOUNDRY)    applib.cpp
# Compile headers
stable.pch : $(STABLEHDRS)
    $(CPP) $(CLFLAGS) /Yc$(BOUNDRY)    applib.cpp myapp.cpp
```

除了[生成過程中 PCH 檔中](#pch-files-in-the-build-process)的「使用預編譯的標頭檔的 Makefile 的結構」中所示的 STABLEHDRS、BOUNDRY 和 UNSTABLEHDRS 宏外,此 makefile 提供了 CLFLAGS 宏和 LINKFLAGS 宏。 您必須使用這些宏來列出編譯器和連結器選項,這些選項適用於生成應用程式的可執行檔的調試版本還是最終版本。 還有一個 LIBS 宏,您可以在其中列出專案所需的庫。

makefile 也使用 。如果!還!ENDIF 用於偵測您是否在 NMAKE 命令列上定義 DEBUG 符號:

```NMAKE
NMAKE DEBUG=[1|0]
```

此功能使您能夠在開發和程式的最終版本中使用相同的 makefile - 將 DEBUG_0 用於最終版本。 以下命令列等效:

```NMAKE
NMAKE
NMAKE DEBUG=0
```

有關製作檔案的詳細資訊,請參閱[NMAKE 參考](reference/nmake-reference.md)。 另請參考[MSVC 編譯器選項](reference/compiler-options.md)與[MSVC 連結器選項](reference/linker-options.md)。

## <a name="example-code-for-pch"></a>PCH 範例程式碼

以下來源檔用於[生成過程中 PCH 檔中](#pch-files-in-the-build-process)描述的 makefile 和[PCH 的「範例使檔案](#sample-makefile-for-pch)」。 請注意,註釋包含重要資訊。

```cpp
// ANOTHER.H : Contains the interface to code that is not
//             likely to change.
//
#ifndef __ANOTHER_H
#define __ANOTHER_H
#include<iostream>
void savemoretime( void );
#endif // __ANOTHER_H
```

```cpp
// STABLE.H : Contains the interface to code that is not likely
//            to change. List code that is likely to change
//            in the makefile's STABLEHDRS macro.
//
#ifndef __STABLE_H
#define __STABLE_H
#include<iostream>
void savetime( void );
#endif // __STABLE_H
```

```cpp
// UNSTABLE.H : Contains the interface to code that is
//              likely to change. As the code in a header
//              file becomes stable, remove the header file
//              from the makefile's UNSTABLEHDR macro and list
//              it in the STABLEHDRS macro.
//
#ifndef __UNSTABLE_H
#define __UNSTABLE_H
#include<iostream>
void notstable( void );
#endif // __UNSTABLE_H
```

```cpp
// APPLIB.CPP : This file contains the code that implements
//              the interface code declared in the header
//              files STABLE.H, ANOTHER.H, and UNSTABLE.H.
//
#include"another.h"
#include"stable.h"
#include"unstable.h"
using namespace std;
// The following code represents code that is deemed stable and
// not likely to change. The associated interface code is
// precompiled. In this example, the header files STABLE.H and
// ANOTHER.H are precompiled.
void savetime( void )
    { cout << "Why recompile stable code?\n"; }
void savemoretime( void )
    { cout << "Why, indeed?\n\n"; }
// The following code represents code that is still under
// development. The associated header file is not precompiled.
void notstable( void )
    { cout << "Unstable code requires"
            << " frequent recompilation.\n";
    }
```

```cpp
// MYAPP.CPP : Sample application
//             All precompiled code other than the file listed
//             in the makefile's BOUNDRY macro (stable.h in
//             this example) must be included before the file
//             listed in the BOUNDRY macro. Unstable code must
//             be included after the precompiled code.
//
#include"another.h"
#include"stable.h"
#include"unstable.h"
int main( void )
{
    savetime();
    savemoretime();
    notstable();
}
```

## <a name="see-also"></a>另請參閱

[C/C++ 建置參考](reference/c-cpp-building-reference.md)<br/>
[MSVC 編譯器選項](reference/compiler-options.md)
