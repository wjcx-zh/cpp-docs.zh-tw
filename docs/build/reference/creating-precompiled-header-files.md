---
title: 建立先行編譯標頭檔
ms.date: 11/19/2018
f1_keywords:
- pch
helpviewer_keywords:
- precompiled header files, creating
- PCH files, creating
- cl.exe compiler, precompiling code
- .pch files, creating
ms.assetid: e2cdb404-a517-4189-9771-c869c660cb1b
ms.openlocfilehash: b570b76328ee9824610aac495d97cede19189cf9
ms.sourcegitcommit: 9e891eb17b73d98f9086d9d4bfe9ca50415d9a37
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/20/2018
ms.locfileid: "52176428"
---
# <a name="creating-precompiled-header-files"></a>建立先行編譯標頭檔

Microsoft C 和 C++ 編譯器提供對任何 C 或 C++ 程式碼進行先行編譯的選項，包括內嵌程式碼。 您可以使用這項效能功能來編譯穩定的程式碼主體，並將程式碼的編譯狀態儲存在檔案中，然後在後續編譯期間，將先行編譯的程式碼與仍在開發中的程式碼結合。 由於穩定的程式碼不需要重新編譯，因此每個後續編譯的速度會更快。

本主題涵蓋下列的先行編譯標頭主題：

- [先行編譯原始程式碼的時機](#when-to-precompile-source-code)

- [先行編譯程式碼的兩個選擇](#two-choices-for-precompiling-code)

- [先行編譯標頭檔的一致性規則](#precompiled-header-consistency-rules)

- [針對每個檔案使用的先行編譯標頭檔的一致性規則](#consistency-rules-for-per-file-use-of-precompiled-headers)

- [/Yc 和 /Yu 的一致性規則](#consistency-rules-for-yc-and-yu)

- [在專案中使用先行編譯標頭檔](#using-precompiled-headers-in-a-project)

- [建置程序中的 PCH 檔](#pch-files-in-the-build-process)

- [PCH 的 Makefile 範例](#sample-makefile-for-pch)

- [PCH 範例程式碼](#example-code-for-pch)

如需與先行編譯標頭相關的編譯器選項的參考資訊，請參閱[/Y （先行編譯標頭）](../../build/reference/y-precompiled-headers.md)。

## <a name="when-to-precompile-source-code"></a>先行編譯原始程式碼的時機

先行編譯的程式碼很有用的開發週期縮短編譯時間，特別是當：

- 您一律使用極為龐大的不常變更的程式碼。

- 您的程式包含多個模組，全部都使用一組標準的 include 檔和相同的編譯選項。 在此情況下，所有包含的檔案可以先行編譯成一個先行編譯標頭。

第一次編譯，建立先行編譯標頭 (PCH) 檔案的一個 — 需要較長的時間比後續的編譯。 後續編譯包含先行編譯的程式碼就可以更快速。

您可以先行編譯 C 和 c + + 程式。 在 c + + 程式設計中很常見的做法，來區隔成標頭檔的類別介面資訊。 稍後可以包含這些標頭檔中使用類別的程式。 先行編譯這些標頭，您可以減少程式編譯所需的時間。

> [!NOTE]
> 雖然您可以使用只有一個先行編譯標頭 (.pch) 檔案，每個來源檔案，您可以使用多個專案中的.pch 檔案。

## <a name="two-choices-for-precompiling-code"></a>先行編譯程式碼的兩個選擇

您可以使用 Visual c + +，先行編譯任何 C 或 c + + 程式碼;您不一定要先行編譯僅標頭檔。

先行編譯需要規劃，但如果先行編譯原始程式碼，簡單的標頭檔以外，它會提供更快的編譯。

當您知道原始程式檔使用的標頭檔的一般設定，但不將它們包含在相同的順序，或您想要包含在您先行編譯的原始程式碼，請先行編譯的程式碼。

先行編譯標頭選項[/Yc （建立先行編譯標頭檔）](../../build/reference/yc-create-precompiled-header-file.md)並[/Yu （使用先行編譯標頭檔）](../../build/reference/yu-use-precompiled-header-file.md)。 使用 **/Yc**建立先行編譯標頭。 當搭配選擇性[hdrstop](../../preprocessor/hdrstop.md) pragma **/Yc**可讓您先行編譯這兩個標頭檔和原始碼。 選取  **/Yu**現有編譯中使用現有的先行編譯標頭。 您也可以使用 **/Fp**具有 **/Yc**並 **/Yu**選項，以提供先行編譯標頭的替代名稱。

編譯器選項參考主題 **/Yu**並 **/Yc**討論如何存取這項功能在開發環境中的。

## <a name="precompiled-header-consistency-rules"></a>先行編譯標頭檔的一致性規則

因為 PCH 檔案包含電腦環境的相關資訊，以及關於此計畫的記憶體位址資訊，您應該只使用 PCH 檔案在電腦上的，建立位置。

## <a name="consistency-rules-for-per-file-use-of-precompiled-headers"></a>針對每個檔案使用的先行編譯標頭檔的一致性規則

[/Yu](../../build/reference/yu-use-precompiled-header-file.md)編譯器選項可讓您指定要使用哪一個 PCH 檔案。

當您使用 PCH 檔案時，編譯器會假設相同的編譯環境，另一個使用一致的編譯器選項、 pragma，等等 —，已在作用中您建立 PCH 檔案時，除非您另外指定。 如果編譯器偵測到不一致的問題，它會發出警告，並盡可能識別不一致的情況。 這類警告不一定表示 PCH 檔案; 發生問題只要可以警告您可能發生的衝突。 下列各節中詳述的 PCH 檔的一致性需求。

### <a name="compiler-option-consistency"></a>編譯器選項一致性

使用 PCH 檔案時，下列編譯器選項可以觸發不一致警告：

- 建立使用前置處理器巨集 (/ D) 選項，必須建立 PCH 檔案的編譯與目前的編譯相同。 定義常數的狀態未核取，但如果這些變更，可能會發生無法預期的結果。

- PCH 檔案不適用於 /E 和 /EP 選項。

- 您必須使用產生瀏覽資訊建立 PCH 檔案 (/ FR) 選項或排除的本機變數 (/ Fr) 選項使用 PCH 檔案的後續編譯才能使用這些選項。

### <a name="c-70-compatible-z7"></a>C 7.0 相容 (/ Z7)

如果建立 PCH 檔案時，這個選項會是作用中，使用 PCH 檔案的後續編譯就可以使用偵錯資訊。

如果 C 7.0 相容 (/ Z7) 選項不是有效建立 PCH 檔案時，使用 PCH 檔案和/z7 的後續編譯會觸發警告。 偵錯的資訊會放在目前的.obj 檔案，並在 PCH 檔案中定義的本機符號不適用於偵錯工具。

### <a name="include-path-consistency"></a>包含路徑的一致性

PCH 檔案並不會包含已在作用中建立時的 include 路徑的相關資訊。 當您使用 PCH 檔案時，編譯器一律會使用目前的編譯過程中所指定的 include 路徑。

### <a name="source-file-consistency"></a>來源檔案的一致性

當您指定 [使用先行編譯標頭檔 (/Yu)] 選項時，編譯器會忽略所有前置處理器指示詞 （包括 pragma） 將先行編譯的原始程式碼中出現。 這類的前置處理器指示詞所指定的編譯必須與用於建立先行編譯標頭檔 (/Yc) 選項編譯相同。

### <a name="pragma-consistency"></a>Pragma 一致性

通常處理期間建立一個 PCH 檔案的 Pragma 會影響與後續使用 PCH 檔案的檔案。 `comment`和`message`pragma 不會影響編譯的其餘部分。

這些 pragma 會影響的 PCH 檔案; 在程式碼它們不會影響後續使用 PCH 檔案的程式碼：

||||
|-|-|-|
|`comment`|`page`|`subtitle`|
|`linesize`|`pagesize`|`title`|
|`message`|`skip`||

這些 pragma 會保留為先行編譯標頭的一部分，而且會影響使用先行編譯標頭之編譯的其餘部分：

||||
|-|-|-|
|`alloc_text`|`include_alias`|`pack`|
|`auto_inline`|`init_seg`|`pointers_to_members`|
|`check_stack`|`inline_depth`|`setlocale`|
|`code_seg`|`inline_recursion`|`vtordisp`|
|`data_seg`|`intrinsic`|`warning`|
|`function`|`optimize`||

## <a name="consistency-rules-for-yc-and-yu"></a>/Yc 和 /Yu 的一致性規則

當您使用先行編譯標頭使用 /Yc 或 /Yu 建立時，編譯器就會比較目前編譯環境以取得存在於建立 PCH 檔案時。 請務必指定與上一個 （使用一致的編譯器選項、 pragma，等等） 目前的編譯一致的環境。 如果編譯器偵測到不一致的問題，它會發出警告，並盡可能識別不一致的情況。 這類警告不一定表示有問題 PCH 檔案;只要可以警告您可能發生的衝突。 下列各節說明先行編譯標頭的一致性需求。

### <a name="compiler-option-consistency"></a>編譯器選項一致性

下表列出使用先行編譯標頭時，可能會觸發不一致警告的編譯器選項︰

|選項|名稱|規則|
|------------|----------|----------|
|/D|定義常數和巨集|必須建立先行編譯標頭的編譯與目前的編譯相同。 定義常數的狀態未核取，但如果您的檔案取決於已變更的常數值，就可能發生無法預期的結果。|
|/E 或 /EP|將前置處理器輸出複製到標準輸出|先行編譯標頭功能不適用於 /E 或 /EP 選項。|
|/Fr 或 /FR|產生 Microsoft 來源瀏覽器資訊|如需有效 /Yu 選項 /Fr 和 /FR 選項，必須也已作用中建立先行編譯標頭時。 使用先行編譯標頭的後續編譯也會產生來源瀏覽器資訊。 瀏覽器資訊放在單一的.sbr 檔和其他檔案參考中的 CodeView 資訊在相同的方式。 您無法覆寫來源瀏覽器資訊的位置。|
|/ GA，/GD、 /GE、 /Gw 或 /GW|Windows 通訊協定選項|必須建立先行編譯標頭的編譯與目前的編譯相同。 如果這些選項不同，便會產生一則警告訊息。|
|/ZI|產生完整的偵錯資訊|如果建立先行編譯標頭時，這個選項會是作用中，使用先行編譯的後續編譯就可以使用該偵錯資訊。 如果 /Zi 不是作用中建立先行編譯標頭時，使用先行編譯和 /Zi 選項的後續編譯會觸發警告。 偵錯資訊置於目前的物件檔案和先行編譯標頭中定義的本機符號不適用於偵錯工具。|

> [!NOTE]
>  先行編譯標頭設備適合只有在 C 和 c + + 原始程式檔。

## <a name="using-precompiled-headers-in-a-project"></a>在專案中使用先行編譯標頭檔

前幾節會提供的先行編譯標頭： /Yc 和 /Yu，/Fp 選項中，而[hdrstop](../../preprocessor/hdrstop.md) pragma。 本章節描述的專案中; 中使用手動先行編譯標頭選項的方法範例 makefile 與它所管理的程式碼結束。

在專案中使用手動先行編譯標頭選項的另一種方法，如研究位於 MFC\SRC 目錄是預設在安裝期間建立的 Visual c + + 的 makefile 的其中一個。 這些 makefile 採取類似的方式來顯示這一節，但更善用 Microsoft 計劃維護公用程式 (NMAKE) 巨集，並提供更好的控制，建置程序。

## <a name="pch-files-in-the-build-process"></a>建置程序中的 PCH 檔

軟體專案的程式碼基底通常會包含在多個 C 或 c + + 原始程式檔、 目的檔、 程式庫和標頭檔中。 一般而言，makefile 協調這些項目的組合，為可執行檔。 下圖顯示使用先行編譯標頭檔的 makefile 結構。 NMAKE 巨集名稱和檔案名稱，在此圖中會保持一致與範例程式碼中找到[PCH 的 Makefile 範例](#sample-makefile-for-pch)並[PCH 範例程式碼](#example-code-for-pch)。

此圖會使用三個圖表的裝置，顯示的建置程序流程。 名稱的矩形代表每個檔案或巨集;三個巨集代表一或多個檔案。 陰影的區域代表每個編譯或連結的動作。 箭號會顯示在編譯或連結流程期間合併的檔案與巨集。

![使用先行編譯標頭檔的 makefile 結構](../../build/reference/media/vc30ow1.gif "使用先行編譯標頭檔的 makefile 結構") <br/>
使用先行編譯標頭檔的 Makefile 的結構

從頂端，STABLEHDRS 和界限是圖表的您可以在其中列出不太可能需要重新編譯檔案的 NMAKE 巨集。 這些檔案編譯的命令字串

`CL /c /W3 /Yc$(BOUNDRY) applib.cpp myapp.cpp`

只有當先行編譯標頭檔 （編譯） 不存在或您對列出在兩個巨集的檔案變更。 在任一情況下，先行編譯標頭檔會包含只從 STABLEHDRS 巨集中列出的檔案的程式碼。 列出您想要先行編譯界限巨集中的最後一個檔案。

標頭檔或 C 或 c + + 原始程式檔，可以是您在這些巨集中列出的檔案。 （與 C 和 c + + 模組無法使用單一的 PCH 檔）。請注意，您可以使用**hdrstop**巨集來停止在界限檔案內的某個時間點的先行編譯。 請參閱[hdrstop](../../preprocessor/hdrstop.md)如需詳細資訊。

APPLIB.obj 繼續往下圖，代表您最終的應用程式中使用的支援程式碼。 它會建立從 APPLIB.cpp，檔案列在 UNSTABLEHDRS 巨集和先行編譯程式碼從先行編譯標頭。

MYAPP.obj 代表最終的應用程式。 它會建立從 MYAPP.cpp，檔案列在 UNSTABLEHDRS 巨集和先行編譯程式碼從先行編譯標頭。

最後，可執行檔 (MYAPP。EXE) 會建立連結的 OBJ 巨集 （APPLIB.obj 和 MYAPP.obj） 中列出的檔案。

## <a name="sample-makefile-for-pch"></a>PCH 的 Makefile 範例

下列的 makefile 使用巨集和 ！如果 ！否則 ！ENDIF 來簡化其與您專案的流程控制命令結構。

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
LINKFLAGS = /NOD /ONERROR:NOEXE
!IF "$(DEBUG)" == "1"
CLFLAGS   = /D_DEBUG $(CLFLAGS) /Od /Zi /f
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

圖 」 結構的 Makefile，會使用先行編譯標頭檔案 > 中所示的 STABLEHDRS、 界限，以及 UNSTABLEHDRS 巨集除了[建置程序中的 PCH 檔](#pch-files-in-the-build-process)，此 makefile 提供 CLFLAGS 巨集和 LINKFLAGS巨集。 若要列出編譯器和連結器選項適用於無論您建置偵錯] 或 [應用程式的可執行檔的最終版本，您必須使用這些巨集。 另外還有 LIBS 巨集清單的程式庫的地方需要您的專案。

Makefile 也會使用 ！如果 ！否則 ！ENDIF 來偵測是否在 NMAKE 命令列上定義的偵錯符號：

```NMAKE
NMAKE DEBUG=[1|0]
```

這項功能可讓您在開發期間使用相同的 makefile 和最終版本的程式 — 使用 偵錯 = 0 的最終版本。 下列命令列是相等的：

```NMAKE
NMAKE
NMAKE DEBUG=0
```

如需有關 makefile 的詳細資訊，請參閱[NMAKE 參考](../../build/nmake-reference.md)。 另請參閱[編譯器選項](../../build/reference/compiler-options.md)並[連結器選項](../../build/reference/linker-options.md)。

## <a name="example-code-for-pch"></a>PCH 範例程式碼

下列的原始程式檔會在中所述的 makefile[建置程序中的 PCH 檔](#pch-files-in-the-build-process)並[PCH 的 Makefile 範例](#sample-makefile-for-pch)。 請注意，註解會包含重要資訊。

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
#include<iostream.h>
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

[C/C++ 建置參考](../../build/reference/c-cpp-building-reference.md)<br/>
[編譯器選項](../../build/reference/compiler-options.md)