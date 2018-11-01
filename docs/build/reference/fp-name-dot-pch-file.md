---
title: /Fp (命名 .Pch 檔案)
ms.date: 11/04/2016
f1_keywords:
- VC.Project.VCCLCompilerTool.PrecompiledHeaderFile
- /fp
- VC.Project.VCCLWCECompilerTool.PrecompiledHeaderFile
helpviewer_keywords:
- Fp compiler option [C++]
- -Fp compiler option [C++]
- naming precompiler header files
- PCH files, naming
- names [C++], PCH
- .pch files, naming
- precompiled header files, naming
- /Fp compiler option [C++]
ms.assetid: 0fcd9cbd-e09f-44d3-9715-b41efb5d0be2
ms.openlocfilehash: 30a569b367d10a4f230d0054b19833c6614afac7
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50517087"
---
# <a name="fp-name-pch-file"></a>/Fp (命名 .Pch 檔案)

提供 先行編譯的標頭，而不是使用預設的路徑名稱的路徑名稱。

## <a name="syntax"></a>語法

> **/Fp**<em>路徑名稱</em>

## <a name="remarks"></a>備註

使用這個選項搭配[/Yc （建立先行編譯標頭檔）](../../build/reference/yc-create-precompiled-header-file.md)或是[/Yu （使用先行編譯標頭檔）](../../build/reference/yu-use-precompiled-header-file.md)提供先行編譯的標頭，而不是使用預設的路徑名稱的路徑名稱。 您也可以使用 **/Fp**具有 **/Yc**若要指定不同的先行編譯標頭檔使用 **/Yc**<em>filename</em>引數和從原始程式檔的基底名稱。

如果您未指定延伸模組的路徑名稱的一部分，則會假設副檔名為.pch。 如果您指定不含檔案名稱的目錄，預設檔名為 VC*x*0.pch，其中*x*是使用 Visual c + + 的主要版本。

您也可以使用 **/Fp**選項搭配 **/Yu**。

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 開發環境中設定這個編譯器選項

1. 開啟專案的 [屬性頁]  對話方塊。 如需詳細資料，請參閱[使用專案屬性](../../ide/working-with-project-properties.md)。

1. 按一下 [C/C++]  資料夾。

1. 按一下 **先行編譯標頭**屬性頁。

1. 修改**先行編譯標頭檔**屬性。

### <a name="to-set-this-compiler-option-programmatically"></a>若要以程式方式設定這個編譯器選項

- 請參閱 <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.PrecompiledHeaderFile%2A>。

## <a name="example"></a>範例

如果您想要建立您的程式的偵錯版本的先行編譯標頭檔和標頭檔和原始程式碼所編譯，您可以指定命令例如：

```
CL /DDEBUG /Zi /Yc /FpDPROG.PCH PROG.CPP
```

## <a name="example"></a>範例

下列命令會指定名為 MYPCH.pch 先行編譯標頭檔。 編譯器會假設來源中的程式碼 PROG.cpp 已透過 MYAPP.h 已經先行編譯和先行編譯的程式碼位於 MYPCH.pch。 它使用 MYPCH.pch 的內容，並會編譯 PROG.cpp，若要建立的.obj 檔案的其餘部分。 此範例的輸出是名為 PROG.exe 的檔案。

```
CL /YuMYAPP.H /FpMYPCH.PCH PROG.CPP
```

## <a name="see-also"></a>另請參閱

[輸出檔 (/F) 選項](../../build/reference/output-file-f-options.md)<br/>
[編譯器選項](../../build/reference/compiler-options.md)<br/>
[設定編譯器選項](../../build/reference/setting-compiler-options.md)<br/>
[指定路徑名稱](../../build/reference/specifying-the-pathname.md)