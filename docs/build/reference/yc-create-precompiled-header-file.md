---
title: /Yc (建立先行編譯標頭檔)
ms.date: 11/04/2016
f1_keywords:
- VC.Project.VCCLCompilerTool.UsePrecompiledHeader
- /yc
- VC.Project.VCCLWCECompilerTool.PrecompiledHeaderThrough
- VC.Project.VCCLWCECompilerTool.UsePrecompiledHeader
- VC.Project.VCCLCompilerTool.PrecompiledHeaderThrough
helpviewer_keywords:
- precompiled header files, creating
- PCH files, creating
- .pch files, creating
- -Yc compiler option [C++]
- /Yc compiler option [C++]
- Yc compiler option [C++]
ms.assetid: 47c2e555-b4f5-46e6-906e-ab5cf21f0678
ms.openlocfilehash: 0d902b9ebb35bc7f267cb67861b7be0763f378a6
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2019
ms.locfileid: "57821426"
---
# <a name="yc-create-precompiled-header-file"></a>/Yc (建立先行編譯標頭檔)

會指示編譯器建立代表某一點的編譯狀態的先行編譯標頭 (.pch) 檔案。

## <a name="syntax"></a>語法

> __/Yc__<br/>
> __/Yc__*filename*

## <a name="arguments"></a>引數

*filename*<br/>
指定的標頭 (.h) 檔。 使用這個引數時，編譯器會編譯的.h 檔案包括所有的程式碼。

## <a name="remarks"></a>備註

當 **/Yc**但未指定引數，編譯器會編譯到 end 的基底的原始程式檔，或在基底的檔案中的點的所有程式碼所在[hdrstop](../../preprocessor/hdrstop.md)指示詞，就會發生。 產生的.pch 檔案會具有作為基底的原始程式檔相同的基底名稱除非您指定不同的檔案名稱，使用**hdrstop** pragma 或 **/Fp**選項。

先行編譯的程式碼會儲存在檔案中建立基底名稱的指定檔案的名稱 **/Yc**選項和副檔名為.pch。 您也可以使用[/Fp （名稱。Pch 檔案）](fp-name-dot-pch-file.md)選項來指定先行編譯標頭檔的名稱。

如果您使用 __/Yc__*filename*，編譯器會編譯，且包含指定的檔案，用於後續的所有程式碼[/Yu （使用先行編譯標頭檔）](yu-use-precompiled-header-file.md)選項。

如果選項 __/Yc__*filename*並 __/Yu__*filename*發生相同的命令列和兩個參考，或暗示，相同的檔案名稱，__/Yc__*filename*會優先使用。 這項功能可簡化撰寫的 makefile。

如需有關先行編譯標頭的詳細資訊，請參閱：

- [/Y (先行編譯標頭檔)](y-precompiled-headers.md)

- [先行編譯標頭檔](../creating-precompiled-header-files.md)

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 開發環境中設定這個編譯器選項

1. 選取的.cpp 檔案。 .Cpp 檔必須 #include 包含先行編譯標頭資訊的.h 檔案。 專案的 **/Yc**檔案層級可以覆寫設定。

1. 開啟專案的 [屬性頁]  對話方塊。 如需詳細資訊，請參閱 <<c0> [ 在 Visual Studio 中的設定 c + + 編譯器和組建屬性](../working-with-project-properties.md)。

1. 開啟**組態屬性**， **C/c + +**，**先行編譯標頭**屬性頁。

1. 修改**先行編譯標頭**屬性。

1. 若要將檔案名稱，修改**先行編譯標頭檔**屬性。

### <a name="to-set-this-compiler-option-programmatically"></a>若要以程式方式設定這個編譯器選項

- 請參閱 <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.PrecompiledHeaderThrough%2A> 和 <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.UsePrecompiledHeader%2A>。

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

此程式碼與命令的編譯時`CL /YcMYAPP.H PROG.CPP`，編譯器會將儲存為 AFXWIN.h，RESOURCE.h，所有前置處理和 MYAPP.h 先行編譯標頭檔中的呼叫 MYAPP.pch。

## <a name="see-also"></a>另請參閱

[MSVC 編譯器選項](compiler-options.md)<br/>
[MSVC 編譯器的命令列語法](compiler-command-line-syntax.md)<br/>
[先行編譯標頭檔](../creating-precompiled-header-files.md)
