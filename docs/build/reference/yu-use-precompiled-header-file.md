---
title: /Yu (使用先行編譯標頭檔)
ms.date: 07/31/2020
f1_keywords:
- /Yu
helpviewer_keywords:
- Yu compiler option [C++]
- /Yu compiler option [C++]
- -Yu compiler option [C++]
- PCH files, use existing
- .pch files, use existing
- precompiled header files, use existing
ms.assetid: 24f1bd0e-b624-4296-a17e-d4b53e374e1f
ms.openlocfilehash: 8cccce39949f23e4ceb72807ecaef3597ab733c4
ms.sourcegitcommit: f2a135d69a2a8ef1777da60c53d58fe06980c997
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/03/2020
ms.locfileid: "87520458"
---
# <a name="yu-use-precompiled-header-file"></a>`/Yu`（使用先行編譯標頭檔）

指示編譯器在目前的編譯中使用現有的先行編譯頭 *`.pch`* 檔（）。

## <a name="syntax"></a>Syntax

> **`/Yu`**\[*檔案名*]

## <a name="arguments"></a>引數

*filename*<br/>
標頭檔的名稱，該檔案會使用預處理器指示詞包含在原始程式檔中 `#include` 。

## <a name="remarks"></a>備註

針對 **`/Yc`** 建立先行編譯標頭檔的選項，以及 **`/Yu`** 表示使用先行編譯標頭的任何後續選項，include 檔案的名稱都必須相同。

若為 **`/Yc`** ， *filename*會指定先行編譯停止的時間點。編譯器會使用 include 檔案的基底名稱和的副檔名來預先編譯所有的程式碼，並將產生的先行編譯標頭檔命名為*filename* *`.pch`* 。

檔案 *`.pch`* 必須使用建立 **`/Yc`** 。

編譯器會將 .h 檔案之前發生的所有程式碼視為先行編譯。 它會略過超過與檔案相關聯的指示詞 `#include` *`.h`* ，並使用檔案中包含的程式碼 *`.pch`* ，然後編譯*filename*後面的所有程式碼。

在命令列上，和 filename 之間不允許有空格 **`/Yu`** 。 *filename*

當您指定 **`/Yu`** 不含檔案名的選項時，您的來來源程式必須包含 [`#pragma hdrstop`](../../preprocessor/hdrstop.md) 指定先行編譯標頭檔檔案名的 pragma *`.pch`* 。 在此情況下，編譯器會使用由命名的先行編譯標頭檔（檔案 *`.pch`* ） [`/Fp (Name .pch file)`](fp-name-dot-pch-file.md) 。 編譯器會略過該 pragma 的位置，並從指定的先行編譯頭檔案還原已編譯的狀態。 然後，它只會編譯緊接在 pragma 後面的程式碼。 如果 `#pragma hdrstop` 未指定檔案名，編譯器會尋找名稱衍生自原始程式檔基底名稱（副檔名為）的檔案 *`.pch`* 。 您也可以使用 **`/Fp`** 選項來指定不同的檔案 *`.pch`* 。

如果您指定的 **`/Yu`** 選項沒有檔案名，而且無法指定 `hdrstop` pragma，就會產生錯誤訊息，而且編譯會失敗。

如果 **`/Yc`** _filename_和 **`/Yu`** _filename_選項出現在相同的命令列上，而且兩者都參考相同的檔案名， **`/Yc`** _filename_就會優先使用，並將所有程式碼先行編譯成和包含指定的檔案。 這項功能簡化了 makefile 的撰寫。

因為檔案 *`.pch`* 包含關於電腦環境的資訊，以及有關程式的記憶體位址資訊，所以您應該只 *`.pch`* 在建立該檔案的電腦上使用檔案。

如需先行編譯標頭檔的詳細資訊，請參閱：

- [`/Y`（先行編譯標頭檔）](y-precompiled-headers.md)

- [先行編譯標頭檔](../creating-precompiled-header-files.md)

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 開發環境中設定這個編譯器選項

1. 在專案的 .cpp 檔案上指定[ `/Yc` （建立先行編譯標頭檔）](yc-create-precompiled-header-file.md) 。

1. 開啟專案的 [屬性頁] **** 對話方塊。 如需詳細資料，請參閱[在 Visual Studio 中設定 C ++ 編譯器和組建屬性](../working-with-project-properties.md)。

1. 選取 [設定**屬性**] [  >  **c/c + +** 先行  >  **編譯頭**檔] 屬性頁。

1. 修改先行**編譯的標頭**屬性、**透過檔案屬性建立/使用 PCH** ，或**建立/使用先行編譯標頭**屬性。

### <a name="to-set-this-compiler-option-programmatically"></a>若要以程式方式設定這個編譯器選項

- 請參閱 <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.PrecompiledHeaderThrough%2A> 和 <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.UsePrecompiledHeader%2A>。

## <a name="example"></a>範例

如果是下列程式碼：

```cpp
#include <afxwin.h>   // Include header for class library
#include "resource.h" // Include resource definitions
#include "myapp.h"    // Include information specific to this app
...
```

是使用命令列編譯的 `CL /YuMYAPP.H PROG.CPP` ，編譯器不會處理三個 include 語句。 相反地，它會使用的先行編譯器代碼 *`MYAPP.pch`* ，這可節省前置處理所有三個檔案（以及它們可能包含的任何檔案）所需的時間。

[`/Fp (Name .pch file)`](fp-name-dot-pch-file.md) **`/Yu`** *`.pch`* 如果名稱不同于*filename*引數或來源檔案的基底名稱，您可以使用選項搭配選項來指定檔案名 **`/Yc`** ，如下列範例所示：

```cmd
CL /YuMYAPP.H /FpMYPCH.pch PROG.CPP
```

此命令會指定名為的先行編譯標頭檔 *`MYPCH.pch`* 。 編譯器會使用其內容來還原所有標頭檔的先行編譯狀態，包括和在內 *`MYAPP.h`* 。 編譯器接著會編譯出現在 * 指示詞之後的程式碼 `#include "MYAPP.h"` 。

## <a name="see-also"></a>另請參閱

[MSVC 編譯器選項](compiler-options.md)<br/>
[MSVC 編譯器命令列語法](compiler-command-line-syntax.md)
