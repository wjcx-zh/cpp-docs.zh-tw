---
title: 先行編譯標頭檔
ms.date: 10/24/2019
helpviewer_keywords:
- precompiled header files, creating
- PCH files, creating
- cl.exe compiler, precompiling code
- .pch files, creating
ms.assetid: e2cdb404-a517-4189-9771-c869c660cb1b
ms.openlocfilehash: c68de0ee8e6376731254adf965fb9a81f10f2861
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/25/2020
ms.locfileid: "88838850"
---
# <a name="precompiled-header-files"></a>先行編譯標頭檔

當您在 Visual Studio 中建立新專案時，會將名為*pch*的先行*編譯標頭檔*新增至專案。  (在 Visual Studio 2017 及更早版本中，檔案稱為 *stdafx.h*。 ) 檔案的目的是加速組建程式。 任何穩定的標頭檔（例如，標準程式庫標頭） `<vector>` 都應該包含在此。 只有在修改先行編譯標頭檔或包含的任何檔案時，才會進行編譯。 如果您只在專案原始程式碼中進行變更，組建將會略過先行編譯標頭檔的編譯。

先行編譯標頭的編譯器選項為 [/y](reference/y-precompiled-headers.md)。 在專案屬性頁中，選項位於 [設定 **屬性] > C/c + + > 先行編譯頭**檔。 您可以選擇不使用先行編譯標頭檔，也可以指定標頭檔名稱和輸出檔的名稱和路徑。

## <a name="custom-precompiled-code"></a>自訂先行編譯器代碼

對於花費很長時間來建立的大型專案，您可能會想要考慮建立自訂的先行編譯檔。 Microsoft C 和 C++ 編譯器提供對任何 C 或 C++ 程式碼進行先行編譯的選項，包括內嵌程式碼。 您可以使用這項效能功能來編譯穩定的程式碼主體，並將程式碼的編譯狀態儲存在檔案中，然後在後續編譯期間，將先行編譯的程式碼與仍在開發中的程式碼結合。 由於穩定的程式碼不需要重新編譯，因此每個後續編譯的速度會更快。

## <a name="when-to-precompile-source-code"></a>先行編譯原始程式碼的時機

在開發週期中，先行編譯的程式碼很有用，可減少編譯時間，特別是在下列情況下：

- 您一律使用不常變更的大型程式碼主體。

- 您的套裝程式含多個模組，全都使用一組標準的 include 檔和相同的編譯選項。 在此情況下，所有 include 檔案都可以先行編譯成一個先行編譯標頭檔。

第一個編譯（ (PCH) 檔建立先行編譯標頭檔的編譯）比後續編譯需要更長的時間。 藉由包含先行編譯的程式碼，可以更快速地進行後續的編譯。

您可以先行編譯 C 和 c + + 程式。 在 c + + 程式設計中，常見的作法是將類別介面資訊分隔成標頭檔。 這些標頭檔稍後可包含在使用類別的程式中。 藉由先行編譯這些標頭，您可以減少程式編譯所需的時間。

> [!NOTE]
> 雖然您可以在每個原始檔中只使用一個先行編譯標頭檔 ( .pch) 檔案，但是您可以在專案中使用多個 .pch 檔。

## <a name="two-choices-for-precompiling-code"></a>先行編譯程式碼的兩個選擇

您可以先行編譯任何 C 或 c + + 程式碼;您不限於僅先行編譯標頭檔。

先行編譯需要規劃，但如果您先行編譯了簡單標頭檔以外的原始程式碼，則會提供明顯的編譯速度。

當您知道原始程式檔使用一般的標頭檔集，但未以相同順序包含它們，或您想要在先行編譯中包含原始程式碼時，先行編譯器代碼。

先行編譯標頭選項是 [/yc (建立先行編譯標頭檔) ](reference/yc-create-precompiled-header-file.md) 和 [/yu (使用先行編譯標頭檔) ](reference/yu-use-precompiled-header-file.md)。 使用 **/yc** 建立先行編譯標頭檔。 當搭配選用的 [hdrstop](../preprocessor/hdrstop.md) pragma 使用時， **/yc** 可讓您先行編譯標頭檔和原始程式碼。 選取 [ **/yu** ] 以使用現有編譯中的現有先行編譯標頭檔。 您也可以使用 **/fp** 和 **/yc** 和 **/yu** 選項來提供先行編譯標頭檔的替代名稱。

**/Yu**和 **/yc**的編譯器選項參考主題討論如何在開發環境中存取這項功能。

## <a name="precompiled-header-consistency-rules"></a>先行編譯標頭的一致性規則

因為 PCH 檔案包含電腦環境的相關資訊，以及有關程式的記憶體位址資訊，所以您應該只在建立檔案的電腦上使用 PCH 檔案。

## <a name="consistency-rules-for-per-file-use-of-precompiled-headers"></a>針對每個檔案使用的先行編譯標頭的一致性規則

[/Yu](reference/yu-use-precompiled-header-file.md)編譯器選項可讓您指定要使用的 PCH 檔案。

當您使用 PCH 檔案時，編譯器會假設相同的編譯環境，也就是使用一致的編譯器選項、pragma 等等，在您建立 PCH 檔案時，除非您另外指定。 如果編譯器偵測到不一致的情況，則會發出警告，並盡可能找出不一致的情況。 這類警告不一定表示 PCH 檔案有問題;它們只是警告您可能發生的衝突。 下列各節將說明 PCH 檔案的一致性需求。

### <a name="compiler-option-consistency"></a>編譯器選項一致性

使用 PCH 檔案時，下列編譯器選項可能會觸發不一致的警告：

- 使用預處理器 (/D) 選項建立的宏在建立 PCH 檔案的編譯和目前的編譯之間必須相同。 未檢查已定義常數的狀態，但如果這些變更，可能會發生無法預期的結果。

- PCH 檔案無法搭配/E 和/EP 選項使用。

- PCH 檔案必須使用 [產生流覽資訊 (/FR) ] 選項或 [排除區域變數] (/Fr) 選項來建立，然後使用 PCH 檔案的後續編譯才能使用這些選項。

### <a name="c-70-compatible-z7"></a>C 7.0-相容 (/Z7) 

如果在建立 PCH 檔案時此選項有效，則使用 PCH 檔案的後續編譯可以使用偵錯工具資訊。

如果在建立 PCH 檔案時，C 7.0 相容的 (/Z7) 選項沒有作用，則使用 PCH 檔案和/Z7 的後續編譯將會觸發警告。 偵錯工具會將偵錯工具資訊放在目前的 .obj 檔案中，而 PCH 檔中定義的本機符號將無法供偵錯工具使用。

### <a name="include-path-consistency"></a>包含路徑一致性

PCH 檔案不包含在建立時作用中的 include 路徑相關資訊。 當您使用 PCH 檔案時，編譯器一律會使用目前編譯中指定的 include 路徑。

### <a name="source-file-consistency"></a>來源檔案一致性

當您指定使用先行編譯標頭檔 (/Yu) 選項時，編譯器會忽略所有的預處理器指示詞， (包括出現在要先行編譯之原始程式碼中的 pragma) 。 這類預處理器指示詞所指定的編譯，必須與用於建立先行編譯標頭檔 (/Yc) 選項的編譯相同。

### <a name="pragma-consistency"></a>Pragma 一致性

在建立 PCH 檔案期間處理的 pragma 通常會影響後續使用 PCH 檔案的檔案。 `comment`和 `message` pragma 不會影響編譯的其餘部分。

這些 pragma 只會影響 PCH 檔案內的程式碼;它們不會影響後續使用 PCH 檔案的程式碼：

:::row:::
   :::column span="":::
      `comment`\
      `linesize`
   :::column-end:::
   :::column span="":::
      `message`\
      `page`
   :::column-end:::
   :::column span="":::
      `pagesize`\
      `skip`
   :::column-end:::
   :::column span="":::
      `subtitle`\
      `title`
   :::column-end:::
:::row-end:::

這些 pragma 會保留為先行編譯標頭檔的一部分，並且會影響使用先行編譯標頭檔的編譯的其餘部分：

:::row:::
   :::column span="":::
      `alloc_text`\
      `auto_inline`\
      `check_stack`\
      `code_seg`\
      `data_seg`
   :::column-end:::
   :::column span="":::
      `function`\
      `include_alias`\
      `init_seg`\
      `inline_depth`
   :::column-end:::
   :::column span="":::
      `inline_recursion`\
      `intrinsic`\
      `optimize`\
      `pack`
   :::column-end:::
   :::column span="":::
      `pointers_to_members`\
      `setlocale`\
      `vtordisp`\
      `warning`
   :::column-end:::
:::row-end:::

## <a name="consistency-rules-for-yc-and-yu"></a>/Yc 和 /Yu 的一致性規則

當您使用以/Yc 或/Yu 建立的先行編譯標頭檔時，編譯器會將目前的編譯環境與您建立 PCH 檔案時所存在的環境進行比較。 請務必指定與上一個環境一致的環境， (在目前的編譯中使用一致的編譯器選項、pragma 等) 。 如果編譯器偵測到不一致的情況，則會發出警告，並盡可能找出不一致的情況。 這類警告不一定表示 PCH 檔案有問題;它們只是警告您可能發生的衝突。 下列各節說明先行編譯標頭檔的一致性需求。

### <a name="compiler-option-consistency"></a>編譯器選項一致性

下表列出在使用先行編譯標頭檔時，可能會觸發不一致警告的編譯器選項：

|選項|名稱|規則|
|------------|----------|----------|
|/D|定義常數和宏|建立先行編譯標頭檔和目前編譯的編譯之間必須是相同的。 系統不會檢查已定義常數的狀態，但如果您的檔案相依于已變更常數的值，則可能會發生無法預期的結果。|
|/E 或/EP|將預處理器輸出複製到標準輸出|先行編譯的標頭無法搭配/E 或/EP 選項使用。|
|/Fr 或/FR|產生 Microsoft 來源瀏覽器資訊|若要使用/Yu 選項有效的/Fr 和/FR 選項，它們也必須在先行編譯標頭檔建立時生效。 使用先行編譯標頭檔的後續編譯也會產生來源瀏覽器資訊。 瀏覽器資訊會放在單一 .sbr 檔中，並以 CodeView 資訊的相同方式參考其他檔案。 您無法覆寫來源瀏覽器資訊的位置。|
|/GA、/GD、/GE、/Gw 或/GW|Windows 通訊協定選項|建立先行編譯標頭檔和目前編譯的編譯之間必須是相同的。 如果這些選項不同，則會產生警告訊息。|
|/ZI|產生完整的調試資訊|如果在建立先行編譯標頭檔時此選項有效，則使用先行編譯的後續編譯可以使用該偵錯工具資訊。 如果在建立先行編譯標頭檔時，/Zi 沒有作用，則使用先行編譯的後續編譯和/Zi 選項都會觸發警告。 偵錯工具會將偵錯工具資訊放在目前的物件檔案中，而在先行編譯標頭檔中定義的本機符號則無法供偵錯工具使用。|

> [!NOTE]
> 先行編譯標頭檔僅供 C 和 c + + 原始程式檔使用。

## <a name="using-precompiled-headers-in-a-project"></a>在專案中使用先行編譯的標頭

前幾節提供先行編譯標頭檔的總覽：/Yc 和/Yu、/Fp 選項和 [hdrstop](../preprocessor/hdrstop.md) pragma。 本節說明在專案中使用手動先行編譯標頭選項的方法;它的結尾是範例 makefile 和它所管理的程式碼。

若要使用專案中手動先行編譯標頭選項的另一個方法，請研究 Visual Studio 預設安裝期間所建立之 MFC\SRC 目錄中的其中一個 makefile。 這些 makefile 採用類似于本節所述的方法，但是更充分利用 Microsoft 程式維護公用程式 (NMAKE) 宏，並提供更大的組建流程式控制制。

## <a name="pch-files-in-the-build-process"></a>建置程序中的 PCH 檔

軟體專案的程式碼基底通常包含在多個 C 或 c + + 原始程式檔、物件檔案、程式庫和標頭檔中。 通常，makefile 會將這些專案的組合協調成可執行檔。 下圖顯示使用先行編譯標頭檔的 makefile 結構。 此圖表中的 NMAKE 宏名稱和檔案名，與在 [pch 的範例 Makefile](#sample-makefile-for-pch) 和 [pch](#example-code-for-pch)的範例程式碼中找到的名稱一致。

此圖使用三個圖表裝置來顯示組建程式的流程。 命名的矩形代表每個檔案或宏;這三個宏代表一或多個檔案。 陰影區域代表每個編譯或連結動作。 箭號會顯示編譯或連結程式期間要合併的檔案和宏。

![使用先行編譯標頭檔的 makefile 結構](media/vc30ow1.gif "使用先行編譯標頭檔的 makefile 結構") <br/>
使用先行編譯標頭檔的 Makefile 結構

從圖表的頂端開始，STABLEHDRS 和 BOUNDRY 都是 NMAKE 宏，您可以在其中列出不太可能需要重新編譯的檔案。 這些檔案是由命令字串所編譯

`CL /c /W3 /Yc$(BOUNDRY) applib.cpp myapp.cpp`

只有當先行編譯標頭檔 (穩定的) 不存在時，或如果您對兩個宏中所列的檔案進行變更。 無論是哪一種情況，先行編譯標頭檔都只會包含 STABLEHDRS 宏所列檔案中的程式碼。 列出您要在 BOUNDRY 宏中先行編譯的最後一個檔案。

您在這些宏中列出的檔案可以是標頭檔或 C 或 c + + 原始檔。  (單一 PCH 檔案無法搭配 C 和 c + + 模組使用。 ) 請注意，您可以使用 **hdrstop** 宏，在 BOUNDRY 檔中的某個時間點停止先行編譯。 如需詳細資訊，請參閱 [hdrstop](../preprocessor/hdrstop.md) 。

繼續進行圖表 APPLIB，表示您的最終應用程式中所使用的支援程式碼。 它是從 APPLIB、UNSTABLEHDRS 宏所列的檔案，以及先行編譯標頭檔中的先行編譯器代碼所建立。

MYAPP 表示您的最終應用程式。 它是從 MYAPP、UNSTABLEHDRS 宏中所列的檔案，以及先行編譯標頭檔中的先行編譯器代碼所建立。

最後， ( # A0) 的可執行檔建立方式，是將 OBJ 宏中列出的檔案連結 (APPLIB .obj 和 MYAPP.) 。

## <a name="sample-makefile-for-pch"></a>PCH 的 Makefile 範例

下列 makefile 使用宏和！如果！還！ENDIF 流程式控制制命令結構，以簡化它對您的專案的調適。

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

除了 STABLEHDRS、BOUNDRY 和 UNSTABLEHDRS 宏（在 [組建程式的 PCH](#pch-files-in-the-build-process)檔案中，使用先行編譯標頭檔的 Makefile 結構）中所示，這個 MAKEFILE 提供 CLFLAGS 宏和 LINKFLAGS 宏。 您必須使用這些宏來列出編譯器和連結器選項，無論您建立的是應用程式的可執行檔的偵錯工具或最終版本，都適用。 另外還有一個程式庫宏，您可以在其中列出專案所需的程式庫。

Makefile 也會使用！如果！還！ENDIF 來偵測是否在 NMAKE 命令列上定義 DEBUG 符號：

```NMAKE
NMAKE DEBUG=[1|0]
```

這項功能可讓您在開發期間使用相同的 makefile，以及針對程式的最終版本，在最終版本中使用 DEBUG = 0。 下列命令列是相等的：

```NMAKE
NMAKE
NMAKE DEBUG=0
```

如需 makefile 的詳細資訊，請參閱 [NMAKE 參考](reference/nmake-reference.md)。 另請參閱 [MSVC 編譯器選項](reference/compiler-options.md) 和 [MSVC 連結器選項](reference/linker-options.md)。

## <a name="example-code-for-pch"></a>PCH 範例程式碼

下列原始程式檔會在組建程式中的 [pch](#pch-files-in-the-build-process) 檔和 [Pch 的範例 makefile](#sample-makefile-for-pch)中所述的 makefile 中使用。 請注意，批註包含重要的資訊。

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
