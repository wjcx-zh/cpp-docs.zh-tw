---
title: -WINMDKEYFILE (指定 winmd 金鑰檔) |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- VC.Project.VCLinkerTool.WINMDKeyFile
dev_langs:
- C++
ms.assetid: 65d88fdc-fff9-49ea-8cfc-b2f408741734
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: d688db3039681fc684e6344e4a27ae7a64544757
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/17/2018
ms.locfileid: "45714439"
---
# <a name="winmdkeyfile-specify-winmd-key-file"></a>/WINMDKEYFILE (指定 winmd 金鑰檔)

指定金鑰或金鑰組簽署 Windows 執行階段中繼資料 (.winmd) 檔案。

```
/WINMDKEYFILE:filename
```

## <a name="remarks"></a>備註

類似於[/KEYFILE](../../build/reference/keyfile-specify-key-or-key-pair-to-sign-an-assembly.md)套用到.winmd 檔案的連結器選項。

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 開發環境中設定這個連結器選項

1. 開啟專案的 [屬性頁]  對話方塊。 如需詳細資料，請參閱[使用專案屬性](../../ide/working-with-project-properties.md)。

1. 選取 **連結器**資料夾。

1. 選取  **Windows 中繼資料**屬性頁。

1. 在  **Windows 中繼資料金鑰檔**方塊中，輸入檔案位置。

## <a name="see-also"></a>另請參閱

[設定連結器選項](../../build/reference/setting-linker-options.md)<br/>
[連結器選項](../../build/reference/linker-options.md)