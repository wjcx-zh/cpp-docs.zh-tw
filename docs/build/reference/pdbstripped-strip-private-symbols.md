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
ms.openlocfilehash: 3ed36eca727a15a3c70bc51a07cd3c143d7f66da
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2019
ms.locfileid: "57815212"
---
# <a name="pdbstripped-strip-private-symbols"></a>/PDBSTRIPPED (移除專用符號)

```
/PDBSTRIPPED:pdb_file_name
```

## <a name="arguments"></a>引數

*pdb_file_name*<br/>
使用者指定連結器所建立的已移除的程式資料庫 (PDB) 名稱。

## <a name="remarks"></a>備註

當您建置程式映像與任何編譯器或連結器產生的 PDB 檔案的選項時，/PDBSTRIPPED 選項會建立第二個程式資料庫 (PDB) 檔案 ([/debug](debug-generate-debug-info.md)， [/z7](z7-zi-zi-debug-information-format.md)，debug、/z7、/zd 或 /Zi)。 第二個 PDB 檔會省略您不想要出貨給客戶的符號。 只會包含第二個 PDB 檔案：

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

1. 開啟專案的 [屬性頁]  對話方塊。 如需詳細資訊，請參閱 <<c0> [ 在 Visual Studio 中的設定 c + + 編譯器和組建屬性](../working-with-project-properties.md)。

1. 按一下 **連結器**資料夾。

1. 按一下 **偵錯**屬性頁。

1. 修改**移除專用符號**屬性。

### <a name="to-set-this-linker-option-programmatically"></a>若要以程式設計方式設定這個連結器選項

- 請參閱 <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.StripPrivateSymbols%2A>。

## <a name="see-also"></a>另請參閱

[MSVC 連結器參考](linking.md)<br/>
[MSVC 連結器選項](linker-options.md)
