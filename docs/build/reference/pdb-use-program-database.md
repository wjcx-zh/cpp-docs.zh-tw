---
title: /PDB (使用程式資料庫)
ms.date: 11/04/2016
f1_keywords:
- /pdb
- VC.Project.VCLinkerTool.ProgramDatabaseFile
helpviewer_keywords:
- -PDB linker option
- /PDB linker option
- PDB linker option
- PDB files, creating
- .pdb files, creating
ms.assetid: d23db0ce-10cb-427a-bc60-d6b2a852723d
ms.openlocfilehash: 6a57e4eb23d40355094f4c8274a42ccb7e1b0e20
ms.sourcegitcommit: bff17488ac5538b8eaac57156a4d6f06b37d6b7f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2019
ms.locfileid: "57420631"
---
# <a name="pdb-use-program-database"></a>/PDB (使用程式資料庫)

```
/PDB:filename
```

## <a name="arguments"></a>引數

*filename*<br/>
使用者指定連結器所建立的程式資料庫 (PDB) 名稱。 它會取代預設的名稱。

## <a name="remarks"></a>備註

根據預設，當[/ 偵錯](../../build/reference/debug-generate-debug-info.md)指定，連結器所建立的保存偵錯資訊的程式資料庫 (PDB)。 PDB 的預設檔案名稱具有基底名稱的程式和副檔名.pdb。

使用 /PDB:*filename*指定 PDB 檔的名稱。 如果未指定 /DEBUG，則會忽略 /PDB 選項。

PDB 檔案可達 2 GB。

如需詳細資訊，請參閱 < [.pdb 檔，做為連結器輸入](../../build/reference/dot-pdb-files-as-linker-input.md)。

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 開發環境中設定這個連結器選項

1. 開啟專案的 [屬性頁]  對話方塊。 如需詳細資訊，請參閱 <<c0> [ 設定 Visual c + + 專案屬性](../../ide/working-with-project-properties.md)。

1. 按一下 **連結器**資料夾。

1. 按一下 **偵錯**屬性頁。

1. 修改**產生程式資料庫檔**屬性。

### <a name="to-set-this-linker-option-programmatically"></a>若要以程式設計方式設定這個連結器選項

- 請參閱 <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.ProgramDatabaseFile%2A>。

## <a name="see-also"></a>另請參閱

[設定連結器選項](../../build/reference/setting-linker-options.md)<br/>
[連結器選項](../../build/reference/linker-options.md)
