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
ms.openlocfilehash: 71a05df3adc74edfd814bb6dc15121e4a343dc4d
ms.sourcegitcommit: 6b749db14b4cf3a2b8d581fda6fdd8cb98bc3207
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/05/2020
ms.locfileid: "82825752"
---
# <a name="yc-create-precompiled-header-file"></a>/Yc (建立先行編譯標頭檔)

指示編譯器建立先行編譯標頭檔（.pch），此檔案表示在特定時間點編譯的狀態。

## <a name="syntax"></a>語法

> __/Yc__\
> __/Yc__*filename*

## <a name="arguments"></a>引數

*名稱*<br/>
指定標頭（.h）檔案。 使用這個引數時，編譯器會將所有程式碼編譯成，並包含 .h 檔案。

## <a name="remarks"></a>備註

當指定了不含引數的 **/yc**時，編譯器會將所有程式碼編譯到基底原始程式檔的結尾，或編譯成[hdrstop](../../preprocessor/hdrstop.md)指示詞發生所在基底檔案中的點。 產生的 .pch 檔案與基底原始程式檔具有相同的基底名稱，除非您使用**hdrstop** pragma 或 **/fp**選項指定不同的檔案名。

先行編譯的程式碼會儲存在檔案中，該檔案的名稱是使用 **/yc**選項和 .pch 副檔名所指定之檔案的基底名稱所建立。 您也可以使用[/fp （Name。Pch 檔案）](fp-name-dot-pch-file.md)選項，指定先行編譯標頭檔的名稱。

如果您使用 __/yc__*filename*，編譯器會將所有程式碼編譯為，並包含指定的檔案，以供後續用於[/Yu （使用先行編譯標頭檔）](yu-use-precompiled-header-file.md)選項。

如果選項 __/yc__*filename*和 __/yu__*filename*出現在相同的命令列上，而且參考或表示相同的檔案名，則會優先使用 __/yc__*filename* 。 這項功能簡化了 makefile 的撰寫。

如需先行編譯標頭檔的詳細資訊，請參閱：

- [/Y (先行編譯標頭檔)](y-precompiled-headers.md)

- [先行編譯標頭檔](../creating-precompiled-header-files.md)

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 開發環境中設定這個編譯器選項

1. 選取 .cpp 檔案。 .Cpp 檔案必須 #include 包含先行編譯標頭資訊的 .h 檔案。 專案的 **/yc**設定可以在檔案層級覆寫。

1. 開啟專案的 [屬性頁] **** 對話方塊。 如需詳細資料，請參閱[在 Visual Studio 中設定 C ++ 編譯器和組建屬性](../working-with-project-properties.md)。

1. 開啟 [設定**屬性**， **C/c + +**，先行**編譯標頭**] 屬性頁。

1. 修改先行**編譯的標頭**屬性。

1. 若要設定檔案名，請修改先行**編譯標頭檔**屬性。

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

當使用命令`CL /YcMYAPP.H PROG.CPP`來編譯此程式碼時，編譯器會將 afxwin.h 的所有前置處理儲存在名為 MYAPP 的先行編譯標頭檔中。

## <a name="see-also"></a>請參閱

[MSVC 編譯器選項](compiler-options.md)<br/>
[MSVC 編譯器命令列語法](compiler-command-line-syntax.md)<br/>
[先行編譯標頭檔](../creating-precompiled-header-files.md)
