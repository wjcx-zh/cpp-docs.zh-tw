---
title: /WINMDFILE (指定 winmd 檔案)
ms.date: 11/04/2016
f1_keywords:
- VC.Project.VCLinkerTool.GenerateWindowsMetadataFile
ms.assetid: 062b41b3-14d6-432c-a361-fdb66e918931
ms.openlocfilehash: 5532046f4284100c60bb82c12b4d47c721fc275e
ms.sourcegitcommit: bff17488ac5538b8eaac57156a4d6f06b37d6b7f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2019
ms.locfileid: "57413078"
---
# <a name="winmdfile-specify-winmd-file"></a>/WINMDFILE (指定 winmd 檔案)

指定所產生的 Windows 執行階段中繼資料 (.winmd) 輸出檔的檔案名稱[/WINMD](../../build/reference/winmd-generate-windows-metadata.md)連結器選項。

```
/WINMDFILE:filename
```

## <a name="remarks"></a>備註

使用 `filename` 中指定的值來覆寫預設的 .winmd 檔案名稱 (`binaryname` .winmd)。 請注意，您不用附加 「.winmd 」 至`filename`。  如果多個值陳列 **/WINMDFILE**命令列的最後一個會優先。

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 開發環境中設定這個連結器選項

1. 開啟專案的 [屬性頁]  對話方塊。 如需詳細資料，請參閱[使用專案屬性](../../ide/working-with-project-properties.md)。

1. 選取 **連結器**資料夾。

1. 選取  **Windows 中繼資料**屬性頁。

1. 在  **Windows 中繼資料檔案**方塊中，輸入檔案位置。

## <a name="see-also"></a>另請參閱

[/WINMD (產生 Windows 中繼資料)](../../build/reference/winmd-generate-windows-metadata.md)<br/>
[設定連結器選項](../../build/reference/setting-linker-options.md)<br/>
[連結器選項](../../build/reference/linker-options.md)
