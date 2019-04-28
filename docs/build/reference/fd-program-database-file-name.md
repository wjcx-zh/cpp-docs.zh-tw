---
title: /Fd (程式資料庫檔名)
ms.date: 11/04/2016
f1_keywords:
- /FD
- VC.Project.VCCLWCECompilerTool.ProgramDataBaseFileName
- VC.Project.VCCLCompilerTool.ProgramDataBaseFileName
helpviewer_keywords:
- /FD compiler option [C++]
- program database file name [C++]
- -FD compiler option [C++]
- PDB files, creating
- program database compiler option [C++]
- .pdb files, creating
- FD compiler option [C++]
ms.assetid: 3977a9ed-f0ac-45df-bf06-01cedd2ba85a
ms.openlocfilehash: c686de7dc9c9c20c404240db558d2ff66078ceb7
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62292727"
---
# <a name="fd-program-database-file-name"></a>/Fd (程式資料庫檔名)

指定程式資料庫 (PDB) 檔案所建立的檔案名稱[/z7，/Zi，/ZI （偵錯資訊格式）](z7-zi-zi-debug-information-format.md)。

## <a name="syntax"></a>語法

```
/Fdpathname
```

## <a name="remarks"></a>備註

不含 **/Fd**，PDB 檔案名稱會預設為 VC*x*0.pdb，其中*x*是視覺效果的主要版本C++使用中。

如果您指定的路徑名稱不包含檔案名稱 （路徑以反斜線結尾），編譯器會建立.pdb 檔案，名為 VC*x*0.pdb，在指定的目錄。

如果您指定不包括副檔名的檔案名稱，則編譯器會使用.pdb 的擴充功能。

此選項也會命名最少重建和累加編譯所使用的狀態 (.idb) 檔案。

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 開發環境中設定這個編譯器選項

1. 開啟專案的 [屬性頁]  對話方塊。 如需詳細資訊，請參閱 <<c0> [ 設定C++Visual Studio 中的編譯器和組建屬性](../working-with-project-properties.md)。</c0>

1. 按一下 [C/C++]  資料夾。

1. 按一下 [輸出檔]  屬性頁。

1. 修改**程式資料庫檔名**屬性。

### <a name="to-set-this-compiler-option-programmatically"></a>若要以程式方式設定這個編譯器選項

- 請參閱 <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.ProgramDataBaseFileName%2A>。

## <a name="example"></a>範例

此命令會建立名為 PROG.pdb 和名為 PROG.idb.idb 檔案的.pdb 檔案：

```
CL /DDEBUG /Zi /FdPROG.PDB PROG.CPP
```

## <a name="see-also"></a>另請參閱

[輸出檔 (/F) 選項](output-file-f-options.md)<br/>
[MSVC 編譯器選項](compiler-options.md)<br/>
[MSVC 編譯器命令列語法](compiler-command-line-syntax.md)<br/>
[指定路徑名稱](specifying-the-pathname.md)
