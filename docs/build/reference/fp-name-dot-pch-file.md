---
title: /Fp （Name &period;pch file）
description: 使用/Fp 編譯器選項來指定先行編譯標頭檔名稱。
ms.date: 05/31/2019
f1_keywords:
- VC.Project.VCCLCompilerTool.PrecompiledHeaderFile
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
ms.openlocfilehash: d62c5bd9fc7920c0a2a5530879680fad2a01d39a
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/17/2020
ms.locfileid: "79439790"
---
# <a name="fp-name-periodpch-file"></a>/Fp （Name &period;pch file）

提供先行編譯標頭檔的路徑名稱，而不是使用預設的路徑名稱。

## <a name="syntax"></a>語法

> **/Fp**<em>路徑名稱</em>

## <a name="remarks"></a>備註

使用 **/fp**選項搭配[/yc （建立先行編譯標頭檔）](yc-create-precompiled-header-file.md)或[/Yu （使用先行編譯標頭檔）](yu-use-precompiled-header-file.md)來指定先行編譯標頭檔（PCH）檔案的路徑和檔案名。 根據預設， **/yc**選項會使用原始程式檔的基底名稱和*pch*延伸模組來建立 PCH 檔案名。

如果您未指定副檔名做為*路徑名稱*的一部分，則會假設使用*pch*的副檔名。 當您使用*pathname*結尾的斜線（ **/** ）來指定目錄名稱時，預設檔案名為 vc*版本*0 .pch，其中*version*是 Visual Studio 工具組的主要版本。 此目錄必須存在，或產生錯誤 C1083。

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 開發環境中設定這個編譯器選項

1. 開啟專案的 [屬性頁] 對話方塊。 如需詳細資訊，請參閱[在 Visual Studio 中設定 C ++ 編譯器和組建屬性](../working-with-project-properties.md)。

1. 開啟 [設定**屬性**] > [ **CC++ /**  > 先行**編譯頭**檔] 屬性頁。

1. 修改先行**編譯標頭檔的輸出**檔屬性。

### <a name="to-set-this-compiler-option-programmatically"></a>若要以程式方式設定這個編譯器選項

- 請參閱＜<xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>＞。

## <a name="examples"></a>範例

若要為程式的 debug 組建建立先行編譯標頭檔的個別命名版本，您可以指定命令，例如：

```CMD
CL /DDEBUG /Zi /Yc /FpDPROG.PCH PROG.CPP
```

下列命令會指定使用名為 MYPCH 的先行編譯標頭檔。 編譯器會將程式中的原始程式碼先行編譯到 MYAPP. h 結尾，並將先行編譯的程式碼放在 MYPCH 中。 然後，它會使用 MYPCH 的內容，並編譯器的其餘部分來建立 .obj 檔案。 這個範例的輸出是名為 al.exe 的檔案。

```CMD
CL /YuMYAPP.H /FpMYPCH.PCH PROG.CPP
```

## <a name="see-also"></a>另請參閱

[輸出檔 (/F) 選項](output-file-f-options.md)<br/>
[MSVC 編譯器選項](compiler-options.md)<br/>
[MSVC 編譯器命令列語法](compiler-command-line-syntax.md)<br/>
[指定路徑名稱](specifying-the-pathname.md)
