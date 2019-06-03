---
title: /Fp (名稱&period;pch 檔案)
description: 您可以使用 /Fp 編譯器選項來指定先行編譯標頭檔名稱。
ms.date: 05/31/2019
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
ms.openlocfilehash: 6e7faa934d14acb5d129173c5e0c7ee67d6caf2b
ms.sourcegitcommit: 540fa2f5015de1adfa7b6bf823f6eb4ed5a6a4bd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/03/2019
ms.locfileid: "66460883"
---
# <a name="fp-name-periodpch-file"></a>/Fp (名稱&period;pch 檔案)

提供 先行編譯的標頭，而不是使用預設的路徑名稱的路徑名稱。

## <a name="syntax"></a>語法

> **/Fp**<em>pathname</em>

## <a name="remarks"></a>備註

使用 **/Fp**選項搭配[/Yc （建立先行編譯標頭檔）](yc-create-precompiled-header-file.md)或是[/Yu （使用先行編譯標頭檔）](yu-use-precompiled-header-file.md)指定先行編譯標頭 (PCH) 的路徑和檔案名稱檔案。 根據預設， **/Yc**選項會建立一個 PCH 檔案名稱使用的原始程式檔的基底名稱並*pch*延伸模組。

如果您未指定延伸模組的一部分*pathname*的延伸模組*pch*假設。 當您指定的目錄名稱使用斜線 ( **/** ) 的結尾*pathname*，預設檔名為 vc*版本*0.pch，其中*版本*是 Visual Studio 工具組的主要版本。 此目錄必須存在，或會產生 C1083 錯誤。

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 開發環境中設定這個編譯器選項

1. 開啟專案的 [屬性頁]  對話方塊。 如需詳細資料，請參閱[在 Visual Studio 中設定 C ++ 編譯器和組建屬性](../working-with-project-properties.md)。

1. 開啟**組態屬性** > **C /C++**  > **先行編譯標頭**屬性頁。

1. 修改**先行編譯標頭輸出檔**屬性。

### <a name="to-set-this-compiler-option-programmatically"></a>若要以程式方式設定這個編譯器選項

- 請參閱 <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>。

## <a name="examples"></a>範例

若要建立一個名為您的程式的偵錯組建的先行編譯標頭檔的版本，您可以指定這類命令：

```CMD
CL /DDEBUG /Zi /Yc /FpDPROG.PCH PROG.CPP
```

下列命令會指定名為 MYPCH.pch 先行編譯標頭檔。 編譯器會先行編譯 PROG.cpp 透過 MYAPP.h，結尾中的原始程式碼，並置於 MYPCH.pch 先行編譯的程式碼。 然後使用 MYPCH.pch 的內容，並會編譯 PROG.cpp，若要建立的.obj 檔案的其餘部分。 此範例的輸出是名為 PROG.exe 的檔案。

```CMD
CL /YuMYAPP.H /FpMYPCH.PCH PROG.CPP
```

## <a name="see-also"></a>另請參閱

[輸出檔 (/F) 選項](output-file-f-options.md)<br/>
[MSVC 編譯器選項](compiler-options.md)<br/>
[MSVC 編譯器命令列語法](compiler-command-line-syntax.md)<br/>
[指定路徑名稱](specifying-the-pathname.md)
