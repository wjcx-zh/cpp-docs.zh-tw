---
title: -WINMD （產生 Windows 中繼資料） |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- VC.Project.VCLinkerTool.GenerateWindowsMetadata
dev_langs:
- C++
ms.assetid: bcfb4901-411e-4c9e-9f78-23028b6e5fcc
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 25b8b34e55fc0814653f4c44be50e545633be373
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/17/2018
ms.locfileid: "45705720"
---
# <a name="winmd-generate-windows-metadata"></a>/WINMD (產生 Windows 中繼資料)

可讓產生的 Windows 執行階段中繼資料 (.winmd) 檔。

```
/WINMD[:{NO|ONLY}]
```

## <a name="remarks"></a>備註

**/ WINMD**<br/>
通用 Windows 平台應用程式的預設設定。 連結器產生的二進位可執行檔和.winmd 中繼資料檔案。

**/WINMD:NO**<br/>
連結器會產生只有二進位可執行檔，但不是.winmd 檔案。

**/ WINMD： 只有**<br/>
連結器會產生只有.winmd 檔案，但不是二進位可執行檔的檔案。

根據預設，輸出檔名具有表單`binaryname`.winmd。 若要指定不同的檔案名稱，請使用[/WINMDFILE](../../build/reference/winmdfile-specify-winmd-file.md)選項。

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 開發環境中設定這個連結器選項

1. 開啟專案的 [屬性頁]  對話方塊。 如需詳細資料，請參閱[使用專案屬性](../../ide/working-with-project-properties.md)。

1. 選取 **連結器**資料夾。

1. 選取  **Windows 中繼資料**屬性頁。

1. 在 **產生 Windows 中繼資料**下拉式清單方塊中，選取您想要的選項。

## <a name="see-also"></a>另請參閱

[設定連結器選項](../../build/reference/setting-linker-options.md)<br/>
[連結器選項](../../build/reference/linker-options.md)