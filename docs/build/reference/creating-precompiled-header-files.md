---
title: 建立先行編譯標頭檔 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- pch
dev_langs:
- C++
helpviewer_keywords:
- precompiled header files, creating
- PCH files, creating
- cl.exe compiler, precompiling code
- .pch files, creating
ms.assetid: e2cdb404-a517-4189-9771-c869c660cb1b
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 31d9708f203c3d79d4cf369583c75d348278d06a
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
---
# <a name="creating-precompiled-header-files"></a>建立先行編譯標頭檔
  
Microsoft C 和 C++ 編譯器提供對任何 C 或 C++ 程式碼進行先行編譯的選項，包括內嵌程式碼。 您可以使用這項效能功能來編譯穩定的程式碼主體，並將程式碼的編譯狀態儲存在檔案中，然後在後續編譯期間，將先行編譯的程式碼與仍在開發中的程式碼結合。 由於穩定的程式碼不需要重新編譯，因此每個後續編譯的速度會更快。  
  
本主題涵蓋下列先行編譯標頭主題：  
  
-   [先行編譯原始程式碼的時機](#when-to-precompile-source-code)  
  
-   [先行編譯程式碼的兩個選擇](#two-choices-for-precompiling-code)  
  
-   [先行編譯標頭檔的一致性規則](#precompiled-header-consistency-rules)  
  
-   [針對每個檔案使用的先行編譯標頭檔的一致性規則](#consistency-rules-for-per-file-use-of-precompiled-headers)  
  
-   [/Yc 和 /Yu 的一致性規則](#consistency-rules-for-yc-and-yu)  
  
-   [在專案中使用先行編譯標頭檔](#using-precompiled-headers-in-a-project)  
  
-   [建置程序中的 PCH 檔](#pch-files-in-the-build-process)  
  
-   [PCH 的 Makefile 範例](#sample-makefile-for-pch)  
  
-   [PCH 範例程式碼](#example-code-for-pch)  
  
編譯器選項與先行編譯標頭相關參考資訊，請參閱[/Y （先行編譯標頭）](../../build/reference/y-precompiled-headers.md)。  
  
<a name="when-to-precompile-source-code"></a>  
  
## <a name="when-to-precompile-source-code"></a>先行編譯原始程式碼的時機  
  
先行編譯程式碼很有用在開發週期內，以縮短編譯時間，特別是當：  
  
-   您一律使用大型不常變更的程式碼主體。  
  
-   您的程式包含多個模組，而其全都使用一組標準的 include 檔和相同的編譯選項。 在此情況下，所有包含的檔案可以先行編譯成一個先行編譯標頭。  
  
第一次的編譯-建立先行編譯標頭 (PCH) 檔案的一個 — 時間長於有點後續編譯。 後續編譯可以包含的先行編譯的程式碼更快速地繼續執行。  
  
您可以先行編譯 C 和 c + + 程式。 在 c + + 程式設計中很常見的作法是分隔成標頭檔的類別介面資訊。 稍後可以使用類別的程式包含這些標頭檔。 先行編譯這些標頭，您可以縮短程式編譯所需的時間。  
  
> [!NOTE]
>  雖然您可以使用只有一個先行編譯標頭 (.pch) 檔，每個來源檔案，您可以使用多個專案中的.pch 檔案。  
  
<a name="two-choices-for-precompiling-code"></a>  
  
# <a name="two-choices-for-precompiling-code"></a>先行編譯程式碼的兩個選擇  
  
Visual c + + 中，您可以先行編譯的任何 C 或 c + + 程式碼;您不限於先行編譯僅標頭檔。  
  
先行編譯需要計劃，但如果您先行編譯原始程式碼，簡單的標頭檔以外，它會提供更快的編譯。  
  
您知道原始程式檔使用的標頭檔的一般集，但不將它們包含在相同的順序，或當您想要包含在您先行編譯原始程式碼時，先行編譯程式碼。  
  
先行編譯標頭選項[/Yc （建立先行編譯標頭檔）](../../build/reference/yc-create-precompiled-header-file.md)和[/Yu （使用先行編譯標頭檔）](../../build/reference/yu-use-precompiled-header-file.md)。 使用 **/Yc**建立先行編譯標頭。 當搭配選擇性[hdrstop](../../preprocessor/hdrstop.md) pragma， **/Yc**可讓您先行編譯這兩個標頭檔及原始程式碼。 選取 **/Yu**現有編譯中使用現有的先行編譯標頭。 您也可以使用 **/Fp**與 **/Yc**和 **/Yu**選項，以提供先行編譯標頭的替代名稱。  
  
編譯器選項參考主題 **/Yu**和 **/Yc**討論如何存取這項功能在開發環境中的。  
  
<a name="precompiled-header-consistency-rules"></a>  
  
## <a name="precompiled-header-consistency-rules"></a>先行編譯標頭檔的一致性規則  
  
因為 PCH 檔包含有關電腦環境的資訊，以及關於此計畫的記憶體位址資訊，您應該只使用 PCH 檔案在電腦上的，建立位置。  
  
<a name="consistency-rules-for-per-file-use-of-precompiled-headers"></a>  
  
## <a name="consistency-rules-for-per-file-use-of-precompiled-headers"></a>針對每個檔案使用的先行編譯標頭檔的一致性規則

[/Yu](../../build/reference/yu-use-precompiled-header-file.md)編譯器選項可讓您指定要使用哪一個 PCH 檔案。  
  
當您使用 PCH 檔案時，編譯器會假設相同編譯環境，使用一致的編譯器選項或 pragma 等等，，已在作用中時建立 PCH 檔案，除非您另外指定。 如果編譯器偵測到不一致，它會發出警告並盡可能識別不一致的情況。 這類警告不一定表示有問題的 PCH 檔案。只要可以警告您可能發生的衝突。 下列章節中詳述的 PCH 檔的一致性需求。  
  
### <a name="compiler-option-consistency"></a>編譯器選項一致性  
  
使用 PCH 檔案時，下列編譯器選項可以觸發不一致警告：  
  
-   建立使用前置處理器巨集 (/ D) 選項必須是之間所建立的 PCH 檔的編譯和目前的編譯相同。 定義常數的狀態不會檢查，但如果這些變更可能會發生無法預期的結果。  
  
-   PCH 檔案與 /E 和 /EP 選項無法運作。  
  
-   必須使用產生瀏覽資訊來建立 PCH 檔 (/ FR) 選項或排除的本機變數 (/ Fr) 選項使用 PCH 檔案的後續編譯才能使用這些選項。  
  
### <a name="c-70-compatible-z7"></a>C 7.0 相容 (/ Z7)  
  
如果建立 PCH 檔案時，這個選項會是作用中，使用 PCH 檔案的後續編譯都可以使用偵錯資訊。  
  
如果 C 7.0 相容 (/ Z7) 選項不是作用中建立 PCH 檔案時，使用 PCH 檔案，並在 /Z7 後續編譯觸發警告。 偵錯資訊置於目前的.obj 檔案，並在 PCH 檔案中定義的本機符號並不適用於偵錯工具。  
  
### <a name="include-path-consistency"></a>包含路徑一致性  
  
PCH 檔案並不會包含已在作用中建立時的 include 路徑的相關資訊。 當您使用 PCH 檔案時，編譯器一律會使用目前的編譯中指定的 include 路徑。  
  
### <a name="source-file-consistency"></a>原始程式檔一致性  
  
當您指定 [使用先行編譯標頭檔 (/Yu)] 選項時，編譯器會忽略所有前置處理器指示詞 （包括 pragma），將先行編譯的原始程式碼中出現。 這類前置處理器指示詞所指定的編譯必須是用於建立先行編譯標頭檔 (/Yc) 選項的編譯相同。  
  
### <a name="pragma-consistency"></a>Pragma 一致性    
  
通常的 PCH 檔建立期間所處理的 Pragma 會影響的檔案的後續使用 PCH 檔案。 `comment`和`message`pragma 不會影響在編譯的其餘部分。  
  
這些 pragma 會影響的 PCH 檔案; 在程式碼它們不會影響後續使用 PCH 檔案的程式碼：  
  
||||  
|-|-|-|  
|`comment`|`page`|`subtitle`|  
|`linesize`|`pagesize`|`title`|  
|`message`|`skip`||  
  
這些 pragma 會保留做為先行編譯標頭的一部分，而且會影響使用先行編譯標頭之編譯的其餘部分：  
  
||||  
|-|-|-|  
|`alloc_text`|`include_alias`|`pack`|  
|`auto_inline`|`init_seg`|`pointers_to_members`|  
|`check_stack`|`inline_depth`|`setlocale`|  
|`code_seg`|`inline_recursion`|`vtordisp`|  
|`data_seg`|`intrinsic`|`warning`|  
|`function`|`optimize`||  
  
<a name="consistency-rules-for-yc-and-yu"></a>  
  
## <a name="consistency-rules-for-yc-and-yu"></a>/Yc 和 /Yu 的一致性規則  
  
當您使用建立的 /Yc /Yu 先行編譯標頭時，則編譯器會比較目前的編譯環境，以建立 PCH 檔案時存在的一個。 請務必指定環境與上一個 （使用一致的編譯器選項或 pragma 等等） 目前編譯的一致。 如果編譯器偵測到不一致，它會發出警告並盡可能識別不一致的情況。 這類警告不一定表示有問題 PCH 檔案。只要可以警告您可能發生的衝突。 下列各節說明先行編譯標頭的一致性需求。  
  
### <a name="compiler-option-consistency"></a>編譯器選項一致性  
  
下表列出使用先行編譯標頭時，可能會觸發不一致警告的編譯器選項：  
  
|選項|名稱|規則|  
|------------|----------|----------|  
|/D|定義常數和巨集|必須是之間建立先行編譯標頭的編譯和目前的編譯相同。 定義常數的狀態不會檢查，但如果您的檔案變更常數的值而定，可能會發生無法預期的結果。|  
|/E 或 /EP|複製前置處理器輸出至標準輸出|先行編譯標頭搭配 /E 或 /EP 選項無法運作。|  
|/Fr 或 /fr 進行|產生 Microsoft 來源瀏覽器資訊|/Fr，/FR 有效 /Yu 選項與選項，它們必須也是作用中時建立先行編譯標頭。 使用先行編譯標頭的後續編譯也會產生來源瀏覽器資訊。 瀏覽器資訊放在單一的.sbr 檔並正由其他檔案中的 CodeView 資訊在相同的方式。 您無法覆寫來源瀏覽器資訊的位置。|  
|/ GA、 /GD、 /GE、 /Gw 或 /GW|Windows 通訊協定選項|必須是之間建立先行編譯標頭的編譯和目前的編譯相同。 如果這些選項不同，就會產生一則警告訊息。|  
|/ZI|產生完整偵錯資訊|這個選項是否作用中建立先行編譯標頭時，使用先行編譯的後續編譯都可以使用偵錯資訊。 如果 /Zi 不是作用中建立先行編譯標頭時，後續編譯使用先行編譯和 /Zi 選項，就會觸發警告。 偵錯資訊置於目前的物件檔案，而在先行編譯標頭中定義的本機符號無法提供偵錯工具。|  
  
> [!NOTE]
>  先行編譯標頭設備適用於只能在 C 和 c + + 原始程式檔中。  
  
<a name="using-precompiled-headers-in-a-project"></a>  
  
## <a name="using-precompiled-headers-in-a-project"></a>在專案中使用先行編譯標頭檔  
  
先前的章節將先行編譯標頭的概觀： /Yc 和 /Yu，/Fp 選項，而[hdrstop](../../preprocessor/hdrstop.md) pragma。 本章節描述一種方法在專案中，使用手動先行編譯標頭選項並以範例 makefile 和其所管理的程式碼。  
  
另一個專案中使用手動先行編譯標頭選項的方法，如研究位於 MFC\SRC 目錄是預設在安裝期間建立的 Visual c + + 的 makefile 的其中一個。 這些 makefile 運用本節所呈現的一個類似的方法，但更善用 Microsoft 程式維護公用程式 (NMAKE) 巨集，並提供更好的控制，在建置程序。  
  
<a name="pch-files-in-the-build-process"></a>  
  
## <a name="pch-files-in-the-build-process"></a>建置程序中的 PCH 檔  
  
軟體專案的程式碼基底通常會包含在多個 C 或 c + + 原始程式檔、 目的檔、 程式庫和標頭檔中。 一般而言，makefile 協調這些項目的組合，為可執行檔。 下圖顯示使用先行編譯標頭檔的 makefile 的結構。 NMAKE 巨集名稱與這個圖表中的檔案名稱就會一致與在範例程式碼中找到[PCH 的 Makefile 範例](#sample-makefile-for-pch)和[PCH 範例程式碼](#example-code-for-pch)。  
  
此圖會使用三種圖形顯示的建置程序流程。 名稱的矩形代表每個檔案或巨集;三個巨集代表一或多個檔案。 灰色的區域代表每個編譯或連結的動作。 箭號顯示哪些檔案和巨集組合期間編譯或連結程序。  
  
![使用先行編譯標頭檔的 Makefile](../../build/reference/media/vc30ow1.gif "結構時使用先行編譯標頭檔的 Makefile")  
##### <a name="structure-of-a-makefile-that-uses-a-precompiled-header-file"></a>使用先行編譯標頭檔的 Makefile 的結構  
  
從圖表的頂端，STABLEHDRS 和界限是它列出檔案可能不需要重新編譯的 NMAKE 巨集。 這些檔案編譯的命令字串  
  
`CL /c /W3 /Yc$(BOUNDRY) applib.cpp myapp.cpp`  
  
只有當先行編譯標頭檔 （編譯） 不存在或對兩個巨集中列出的檔案變更。 在任一情況下，先行編譯標頭檔會包含程式碼，只能從 STABLEHDRS 巨集中列出的檔案。 列出您想先行編譯界限巨集中的最後一個檔案。  
  
標頭檔或 C 或 c + + 原始程式檔，可以是您在這些巨集清單的檔案。 （使用 C 和 c + + 模組無法使用單一的 PCH 檔）。請注意，您可以使用**hdrstop**巨集，以停止在某個時間點內界限檔案的先行編譯。 請參閱[hdrstop](../../preprocessor/hdrstop.md)如需詳細資訊。  
  
APPLIB.obj 繼續關閉圖表，代表最後應用程式中使用的支援程式碼。 它會建立從 APPLIB.cpp，檔案列在 UNSTABLEHDRS 巨集和先行編譯程式碼從先行編譯標頭。  
  
MYAPP.obj 代表最後應用程式。 它會建立從 MYAPP.cpp，檔案列在 UNSTABLEHDRS 巨集和先行編譯程式碼從先行編譯標頭。  
  
最後，可執行檔 (MYAPP。EXE) 會建立連結 OBJS 巨集 （APPLIB.obj 和 MYAPP.obj） 中列出的檔案。  
  
<a name="sample-makefile-for-pch"></a>  
  
## <a name="sample-makefile-for-pch"></a>PCH 的 Makefile 範例  
  
下列的 makefile 會使用巨集和 ！如果 ！ELSE ！若要簡化您的專案與 ENDIF 流量控制命令結構。  
  
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
  
圖 」 結構的 Makefile，會使用先行編譯標頭檔 」 中所示的 STABLEHDRS、 邊界，以及 UNSTABLEHDRS 巨集除了[建置程序中的 PCH 檔](#pch-files-in-the-build-process)，此 makefile 提供 CLFLAGS 巨集和 LINKFLAGS巨集。 您必須使用這些巨集來列出編譯器和連結器選項適用於無論您建置偵錯或應用程式的可執行檔的最終版本。 另外還有 LIBS 巨集您用來列出這些程式庫需要您的專案。  
  
也會使用 makefile ！如果 ！ELSE ！ENDIF 來偵測是否定義 DEBUG 符號 NMAKE 命令列：  
  
```NMAKE  
NMAKE DEBUG=[1|0]  
```  
  
這項功能可讓您在開發期間使用相同的 makefile 和程式的最終版本 — 使用 偵錯 = 0 的最終版本。 下列命令列是相等的：  
  
```NMAKE  
NMAKE   
NMAKE DEBUG=0  
```  
  
如需有關 makefile 的詳細資訊，請參閱[NMAKE 參考](../../build/nmake-reference.md)。 另請參閱[編譯器選項](../../build/reference/compiler-options.md)和[連結器選項](../../build/reference/linker-options.md)。  
  
<a name="example-code-for-pch"></a>  
  
## <a name="example-code-for-pch"></a>PCH 範例程式碼  
  
使用下列原始程式檔中所述的 makefile[建置程序中的 PCH 檔](#pch-files-in-the-build-process)和[PCH 的 Makefile 範例](#sample-makefile-for-pch)。 請注意，註解會包含重要資訊。  
  
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
[C/C++ 建置參考](../../build/reference/c-cpp-building-reference.md)   
[編譯器選項](../../build/reference/compiler-options.md)