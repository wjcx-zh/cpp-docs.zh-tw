---
title: /Fm (命名對應檔)
ms.date: 11/04/2016
f1_keywords:
- /fm
helpviewer_keywords:
- -Fm compiler option [C++]
- mapfiles [C++], creating linker
- files [C++], creating map
- Fm compiler option [C++]
- /Fm compiler option [C++]
ms.assetid: 8154448a-93a7-4546-8e4c-5c44d0aff45d
ms.openlocfilehash: eebb1bc0c553dba1934aea75e2e63edc0f222fff
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62292401"
---
# <a name="fm-name-mapfile"></a>/Fm (命名對應檔)

會告訴連結器，以產生對應檔，其中包含以其出現在對應的.exe 檔或 DLL 中的順序中的區段清單。

## <a name="syntax"></a>語法

```
/Fmpathname
```

## <a name="remarks"></a>備註

根據預設，對應檔名稱會指定基底的相對應的 C 或C++具有原始程式檔。副檔名對應。

指定 **/Fm**有相同的效果，您必須指定[/MAP （產生對應檔）](map-generate-mapfile.md)連結器選項。

如果您指定[/c （編譯而不連結）](c-compile-without-linking.md)隱藏連結 **/Fm**沒有任何作用。

在對應檔的全域符號通常具有一或多個前置底線，因為編譯器會將變數名稱中的前置底線。 許多的全域符號出現在對應檔會在內部使用，由編譯器和標準程式庫。

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 開發環境中設定這個編譯器選項

1. 開啟專案的 [屬性頁]  對話方塊。 如需詳細資訊，請參閱 <<c0> [ 設定C++Visual Studio 中的編譯器和組建屬性](../working-with-project-properties.md)。</c0>

1. 按一下 [C/C++]  資料夾。

1. 按一下 [命令列]  屬性頁。

1. 在 [其他選項]  方塊中，輸入編譯器選項。

### <a name="to-set-this-compiler-option-programmatically"></a>若要以程式方式設定這個編譯器選項

- 請參閱 <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>。

## <a name="see-also"></a>另請參閱

[輸出檔 (/F) 選項](output-file-f-options.md)<br/>
[MSVC 編譯器選項](compiler-options.md)<br/>
[MSVC 編譯器命令列語法](compiler-command-line-syntax.md)<br/>
[指定路徑名稱](specifying-the-pathname.md)
