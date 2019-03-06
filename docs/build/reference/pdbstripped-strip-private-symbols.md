---
title: /PDBSTRIPPED (移除專用符號)
ms.date: 11/04/2016
f1_keywords:
- /pdbstripped
- VC.Project.VCLinkerTool.StripPrivateSymbols
helpviewer_keywords:
- /PDBSTRIPPED linker option
- -PDBSTRIPPED linker option
- .pdb files, stripping private symbols
- PDB files, stripping private symbols
- PDBSTRIPPED linker option
ms.assetid: 9b9e0070-6a13-4142-8180-19c003fbbd55
ms.openlocfilehash: c0a79eb8d1c00be2b855ec08ffe44f4e7d7a2e05
ms.sourcegitcommit: bff17488ac5538b8eaac57156a4d6f06b37d6b7f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2019
ms.locfileid: "57412623"
---
# <a name="pdbstripped-strip-private-symbols"></a>/PDBSTRIPPED (移除專用符號)

```
/PDBSTRIPPED:pdb_file_name
```

## <a name="arguments"></a>引數

*pdb_file_name*<br/>
使用者指定連結器所建立的已移除的程式資料庫 (PDB) 名稱。

## <a name="remarks"></a>備註

當您建置程式映像與任何編譯器或連結器產生的 PDB 檔案的選項時，/PDBSTRIPPED 選項會建立第二個程式資料庫 (PDB) 檔案 ([/debug](../../build/reference/debug-generate-debug-info.md)， [/z7](../../build/reference/z7-zi-zi-debug-information-format.md)，debug、/z7、/zd 或 /Zi)。 第二個 PDB 檔會省略您不想要出貨給客戶的符號。 只會包含第二個 PDB 檔案：

- 公用符號

- 物件檔案和它們所提供的可執行檔的部分清單

- 用來周遊堆疊的框架指標最佳化 (FPO) 偵錯記錄

將不會包含已移除的 PDB 檔案：

- 型別資訊

- 行號資訊

- 每個物件檔案 CodeView 符號，例如函式、 區域變數和靜態資料

當您使用 /PDBSTRIPPED，仍會產生完整的 PDB 檔案。

如果您未建立 PDB 檔案，則會忽略 /PDBSTRIPPED。

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 開發環境中設定這個連結器選項

1. 開啟專案的 [屬性頁]  對話方塊。 如需詳細資訊，請參閱 <<c0> [ 設定 Visual c + + 專案屬性](../../ide/working-with-project-properties.md)。

1. 按一下 **連結器**資料夾。

1. 按一下 **偵錯**屬性頁。

1. 修改**移除專用符號**屬性。

### <a name="to-set-this-linker-option-programmatically"></a>若要以程式設計方式設定這個連結器選項

- 請參閱 <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.StripPrivateSymbols%2A>。

## <a name="see-also"></a>另請參閱

[設定連結器選項](../../build/reference/setting-linker-options.md)<br/>
[連結器選項](../../build/reference/linker-options.md)
