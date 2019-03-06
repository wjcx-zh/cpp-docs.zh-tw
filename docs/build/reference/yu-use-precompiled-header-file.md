---
title: /Yu (使用先行編譯標頭檔)
ms.date: 11/04/2016
f1_keywords:
- /yu
helpviewer_keywords:
- Yu compiler option [C++]
- /Yu compiler option [C++]
- -Yu compiler option [C++]
- PCH files, use existing
- .pch files, use existing
- precompiled header files, use existing
ms.assetid: 24f1bd0e-b624-4296-a17e-d4b53e374e1f
ms.openlocfilehash: 49cc7a67a8b25e515d352d481b6ede8d521e51e1
ms.sourcegitcommit: bff17488ac5538b8eaac57156a4d6f06b37d6b7f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2019
ms.locfileid: "57424115"
---
# <a name="yu-use-precompiled-header-file"></a>/Yu (使用先行編譯標頭檔)

指示編譯器將使用現有的先行編譯標頭 (.pch) 檔案中目前的編譯。

## <a name="syntax"></a>語法

```
/Yu[filename]
```

## <a name="arguments"></a>引數

*filename*<br/>
包含在來源檔案使用的標頭檔名稱 **#include**前置處理器指示詞。

## <a name="remarks"></a>備註

Include 檔案的名稱必須是相同 **/Yc**選項建立先行編譯標頭和任何後續 **/Yu**指出使用先行編譯標頭的選項。

針對 **/Yc**，`filename`指定之起點的先行編譯停止; 編譯器會先行編譯所有的程式碼不過`filename`並將產生的先行編譯標頭，以使用 include 檔和擴充功能的基底名稱為.pch。

.Pch 檔案必須已經建立使用 **/Yc**。

編譯器會將所有的程式碼做為先行編譯的.h 檔案前發生。 它會跳到只是超越 **#include**指示詞相關聯的.h 檔案中，使用.pch 檔案中包含的程式碼，並將編譯後的所有程式碼`filename`。

在命令列中，不允許有空格之間 **/Yu**和`filename`。

當您指定 **/Yu**不含檔案名稱，您的原始程式的選項必須包含[#pragma hdrstop](../../preprocessor/hdrstop.md) pragma 指定先行編譯標頭，.pch 檔的檔案名稱。 在此情況下，編譯器會使用名為先行編譯標頭 （.pch 檔案） [/Fp （名稱。Pch 檔案）](../../build/reference/fp-name-dot-pch-file.md)。 編譯器會跳到該 pragma 的位置，從指定的 pragma，先行編譯標頭檔案還原的已編譯的狀態，然後編譯 只有 pragma 後方的程式碼。 如果 **#pragma hdrstop**未指定檔案名稱，編譯器會尋找名稱，衍生自原始程式檔，副檔名為.pch 的主檔名的檔案。 您也可以使用 **/Fp**選項來指定不同的.pch 檔案。

如果您指定 **/Yu**選項不含檔案名稱，並無法指定**hdrstop** pragma，會產生錯誤訊息，並在編譯會失敗。

如果 **/Yc** `filename`並 **/Yu** `filename`選項發生在相同的命令列上，且兩者都參考相同的檔案名稱， **/Yc** `filename`採用優先順序，最多先行編譯所有的程式碼，包括命名的檔案。 這項功能可簡化撰寫的 makefile。

因為.pch 檔包含機器環境的相關資訊，以及關於此計畫的記憶體位址資訊，您應該只使用 pch 檔案在電腦上的，建立位置。

如需有關先行編譯標頭的詳細資訊，請參閱：

- [/Y (先行編譯標頭檔)](../../build/reference/y-precompiled-headers.md)

- [建立先行編譯標頭檔](../../build/reference/creating-precompiled-header-files.md)

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 開發環境中設定這個編譯器選項

1. 指定[/Yc （建立先行編譯標頭檔）](../../build/reference/yc-create-precompiled-header-file.md)專案中的.cpp 檔上。

1. 開啟專案的 [屬性頁]  對話方塊。 如需詳細資料，請參閱[使用專案屬性](../../ide/working-with-project-properties.md)。

1. 按一下 [C/C++]  資料夾。

1. 按一下 **先行編譯標頭**屬性頁。

1. 修改**透過檔案建立/使用 PCH**屬性或**建立/使用先行編譯標頭**屬性。

### <a name="to-set-this-compiler-option-programmatically"></a>若要以程式方式設定這個編譯器選項

- 請參閱 <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.PrecompiledHeaderThrough%2A> 和 <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.UsePrecompiledHeader%2A>。

## <a name="examples"></a>範例

如果下列程式碼：

```
#include <afxwin.h>   // Include header for class library
#include "resource.h" // Include resource definitions
#include "myapp.h"    // Include information specific to this app
...
```

使用命令列編譯`CL /YuMYAPP.H PROG.CPP`，編譯器不會處理三個包含陳述式，但使用先行編譯程式碼從 MYAPP.pch，藉此節省前置處理所有的三個檔案 （和它們可能會包含任何檔案） 中所需的時間。

您可以使用[/Fp （名稱。Pch 檔案）](../../build/reference/fp-name-dot-pch-file.md)選項搭配 **/Yu**選項來指定.pch 檔的名稱，如果名稱不同於其中一個檔案名稱引數來 **/Yc**或原始程式檔，如下所示的基底名稱下列：

```
CL /YuMYAPP.H /FpMYPCH.pch PROG.CPP
```

此命令會指定名為 MYPCH.pch 的先行編譯標頭檔。 編譯器會使用其內容，若要還原的所有標頭檔，最多並包括 MYAPP.h 先行編譯的狀態。 編譯器將編譯的程式碼，之後 MYAPP.h**包括**陳述式。

## <a name="see-also"></a>另請參閱

[編譯器選項](../../build/reference/compiler-options.md)<br/>
[設定編譯器選項](../../build/reference/setting-compiler-options.md)
