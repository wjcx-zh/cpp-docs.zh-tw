---
title: /MERGE (結合區段)
ms.date: 11/04/2016
f1_keywords:
- /merge
- VC.Project.VCLinkerTool.MergeSections
helpviewer_keywords:
- sections, combining
- /MERGE linker option
- sections, naming
- sections
- -MERGE linker option
- MERGE linker option
ms.assetid: 10fb20c2-0b3f-4c8d-98a8-f69aedf03d52
ms.openlocfilehash: e0329c6a29a8667a09a56d894386f5c173a77916
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50532180"
---
# <a name="merge-combine-sections"></a>/MERGE (結合區段)

```
/MERGE:from=to
```

## <a name="remarks"></a>備註

/MERGE 選項結合的第一個區段 (*從*) 與第二個區段 (*要*)，命名產生的區段*至*。 例如，`/merge:.rdata=.text`。

如果第二個區段不存在，連結會重新命名一節*從*作為*至*。

/MERGE 選項適合用來建立 VxDs 和覆寫編譯器所產生的區段名稱。

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 開發環境中設定這個連結器選項

1. 開啟專案的 [屬性頁]  對話方塊。 如需詳細資訊，請參閱 <<c0> [ 設定 Visual c + + 專案屬性](../../ide/working-with-project-properties.md)。

1. 按一下 **連結器**資料夾。

1. 按一下 **進階**屬性頁。

1. 修改**合併區段**屬性。

### <a name="to-set-this-linker-option-programmatically"></a>若要以程式設計方式設定這個連結器選項

1. 請參閱 <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.MergeSections%2A>。

## <a name="see-also"></a>另請參閱

[設定連結器選項](../../build/reference/setting-linker-options.md)<br/>
[連結器選項](../../build/reference/linker-options.md)