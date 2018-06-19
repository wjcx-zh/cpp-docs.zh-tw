---
title: -Yc （建立先行編譯標頭檔） |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- devlang-cpp
ms.topic: reference
f1_keywords:
- VC.Project.VCCLCompilerTool.UsePrecompiledHeader
- /yc
- VC.Project.VCCLWCECompilerTool.PrecompiledHeaderThrough
- VC.Project.VCCLWCECompilerTool.UsePrecompiledHeader
- VC.Project.VCCLCompilerTool.PrecompiledHeaderThrough
dev_langs:
- C++
helpviewer_keywords:
- precompiled header files, creating
- PCH files, creating
- .pch files, creating
- -Yc compiler option [C++]
- /Yc compiler option [C++]
- Yc compiler option [C++]
ms.assetid: 47c2e555-b4f5-46e6-906e-ab5cf21f0678
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 7f26121c80378f4317d02f51582ad67033972765
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
ms.locfileid: "32378658"
---
# <a name="yc-create-precompiled-header-file"></a>/Yc (建立先行編譯標頭檔)
指示編譯器建立代表某一點的編譯狀態的先行編譯標頭 (.pch) 檔案。  
  
## <a name="syntax"></a>語法  
  
> __/Yc__
>  __/Yc__*檔名*  
  
  
## <a name="arguments"></a>引數  
*filename*  
 指定的標頭 (.h) 檔案。 使用這個引數時，編譯器將編譯的.h 檔案包括所有的程式碼。  
  
## <a name="remarks"></a>備註  
 當 **/Yc**但未指定引數，編譯器便會編譯到 end 的基底的原始程式檔，或在基底檔案為止的所有程式碼位置[hdrstop](../../preprocessor/hdrstop.md)指示詞，就會發生。 產生的.pch 檔案會有當做基底的原始程式檔相同的基底名稱除非您指定不同的檔案名稱使用**hdrstop** pragma 或 **/Fp**選項。  
  
 先行編譯的程式碼會儲存在檔案中建立與指定的檔案名稱的名稱 **/Yc**選項和副檔名為.pch。 您也可以使用[/Fp （名稱。Pch 檔案）](../../build/reference/fp-name-dot-pch-file.md)選項來指定先行編譯標頭檔的名稱。  
  
 如果您使用 __/Yc__*filename*，編譯器編譯的所有程式碼，且包含指定的檔案，供後續使用與[/Yu （使用先行編譯標頭檔）](../../build/reference/yu-use-precompiled-header-file.md)選項。  
  
 如果選項 __/Yc__*filename*和 __/Yu__*filename*發生在相同的命令列上，且兩個參考，或暗示，相同的檔案名稱，__/Yc__*filename*優先。 這項功能可簡化撰寫 makefile。  
  
 如需先行編譯標頭的詳細資訊，請參閱：  
  
-   [/Y (先行編譯標頭檔)](../../build/reference/y-precompiled-headers.md)  
  
-   [建立先行編譯標頭檔](../../build/reference/creating-precompiled-header-files.md)  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 開發環境中設定這個編譯器選項  
  
1.  選取的.cpp 檔案。 .Cpp 檔必須 #include 包含先行編譯標頭資訊的.h 檔案。 專案的 **/Yc**設定會覆寫在檔案層級。  
  
2.  開啟專案的 [屬性頁]  對話方塊。 如需詳細資訊，請參閱[使用專案屬性](../../ide/working-with-project-properties.md)。  
  
3.  開啟**組態屬性**， **C/c + +**，**先行編譯標頭**屬性頁。  
  
4.  修改**先行編譯標頭**屬性。  
  
5.  若要設定檔案名稱，請修改**先行編譯標頭檔**屬性。
  
### <a name="to-set-this-compiler-option-programmatically"></a>若要以程式方式設定這個編譯器選項  
  
-   請參閱<xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.PrecompiledHeaderThrough%2A>和<xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.UsePrecompiledHeader%2A>。  
  
## <a name="example"></a>範例  
 請考慮下列程式碼：  
  
```cpp  
// prog.cpp
// compile with: cl /c /Ycmyapp.h prog.cpp
#include <afxwin.h>   // Include header for class library  
#include "resource.h" // Include resource definitions  
#include "myapp.h"    // Include information specific to this app  
// ...  
```  
  
此程式碼與命令的編譯時`CL /YcMYAPP.H PROG.CPP`、 編譯器儲存 AFXWIN.h，命名為 RESOURCE.h 的所有前置處理和 MYAPP.h 先行編譯標頭檔中的呼叫 MYAPP.pch。  
  
## <a name="see-also"></a>另請參閱  
 [編譯器選項](../../build/reference/compiler-options.md)   
 [設定編譯器選項](../../build/reference/setting-compiler-options.md)[建立先行編譯標頭檔](../../build/reference/creating-precompiled-header-files.md)