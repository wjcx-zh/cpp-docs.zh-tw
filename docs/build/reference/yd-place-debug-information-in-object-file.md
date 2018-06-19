---
title: -Yd （將在目的檔中的偵錯資訊） |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /yd
dev_langs:
- C++
helpviewer_keywords:
- /Yd compiler option [C++]
- -Yd compiler option [C++]
- debugging [C++], debug information files
- Yd compiler option [C++]
ms.assetid: c5a699fe-65ce-461e-964c-7f5eb2a8320a
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 39b03b0faf975caba8c5a287c88afcdf53f7a71f
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
ms.locfileid: "32378229"
---
# <a name="yd-place-debug-information-in-object-file"></a>/Yd (將偵錯資訊置入目的檔)
從先行編譯標頭 (.pch) 檔案搭配使用時建立完整的偵錯資訊置於所有目的檔置[/Yc](../../build/reference/yc-create-precompiled-header-file.md)和[/Z7](../../build/reference/z7-zi-zi-debug-information-format.md)選項。 已取代。  
  
## <a name="syntax"></a>語法  
  
```  
/Yd  
```  
  
## <a name="remarks"></a>備註  
 **/Yd**已被取代。[!INCLUDE[vcprvc](../../build/includes/vcprvc_md.md)]現在支援多個物件寫入至單一的.pdb 檔案，使用 **/Zi**改為。 如需已被取代的編譯器選項的清單，請參閱**已取代及移除的編譯器選項**中[依分類排列的編譯器選項](../../build/reference/compiler-options-listed-by-category.md)。  
  
 除非您要散發程式庫包含偵錯資訊，請使用[/Zi](../../build/reference/z7-zi-zi-debug-information-format.md)選項而非 **/Z7**和 **/Yd**。  
  
 只將包含偵錯資訊的程式庫，必須在每個.obj 檔案中儲存完整偵錯資訊。 它會減緩編譯，且需要大量磁碟空間。 當 **/Yc**和 **/Z7**不會使用 **/Yd**，編譯器會建立從.pch 檔案之第一個.obj 檔案中儲存通用偵錯資訊。 編譯器不會將這項資訊插入.pch 檔案，從後續建立的.obj 檔案它會插入交互參照到的資訊。 無論多少的.obj 檔案使用的.pch 檔案，只有一個.obj 檔案會包含常見的偵錯資訊。  
  
 雖然此預設行為會產生更快建置時間，而且會減少磁碟空間的需求，但是它並不想如果小幅變更需要重新建立含有常見的偵錯資訊的.obj 檔案。 在此情況下，編譯器必須重建包含對原始的.obj 檔案的交互參照的所有.obj 檔案。 此外，如果不同的專案會使用通用的.pch 檔案，就難以依賴單一.obj 檔案的交互參照。  
  
 如需先行編譯標頭的詳細資訊，請參閱：  
  
-   [/Y (先行編譯標頭檔)](../../build/reference/y-precompiled-headers.md)  
  
-   [建立先行編譯標頭檔](../../build/reference/creating-precompiled-header-files.md)  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 開發環境中設定這個編譯器選項  
  
1.  開啟專案的 [屬性頁]  對話方塊。 如需詳細資訊，請參閱[使用專案屬性](../../ide/working-with-project-properties.md)。  
  
2.  按一下 [C/C++]  資料夾。  
  
3.  按一下 [命令列]  屬性頁。  
  
4.  在 [其他選項]  方塊中，輸入編譯器選項。  
  
### <a name="to-set-this-compiler-option-programmatically"></a>若要以程式方式設定這個編譯器選項  
  
-   請參閱 <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>。  
  
## <a name="examples"></a>範例  
 假設您有兩個基底的檔案，F.cpp 和 G.cpp，每個包含這些 **#include**陳述式：  
  
```  
#include "windows.h"  
#include "etc.h"  
```  
  
 El comando siguiente crea 先行編譯標頭檔案 ETC.pch 和物件檔案 F.obj:  
  
```  
CL /YcETC.H /Z7 F.CPP  
```  
  
 目的檔 F.obj 包含類型和 WINDOWS.h 和 ETC.h 的符號資訊 （和它們所包含的任何其他標頭檔）。 現在您可以使用先行編譯標頭 ETC.pch 來編譯原始程式檔 G.cpp:  
  
```  
CL /YuETC.H /Z7 G.CPP  
```  
  
 目的檔 G.obj 不包含先行編譯標頭的偵錯資訊，但只是參考 F.obj 檔案中的該資訊。 請注意，您必須使用 F.obj 檔案連結。  
  
 如果您先行編譯標頭不以編譯 **/Z7**，您仍然可以使用它在稍後使用的編譯中 **/Z7**。 不過，偵錯資訊置於目前的物件檔案，而且無法使用偵錯工具的函式和先行編譯標頭中定義類型的本機符號。  
  
## <a name="see-also"></a>另請參閱  
 [編譯器選項](../../build/reference/compiler-options.md)   
 [設定編譯器選項](../../build/reference/setting-compiler-options.md)