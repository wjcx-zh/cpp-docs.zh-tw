---
title: /WINMDKEYFILE (指定 winmd 金鑰檔)
ms.date: 11/04/2016
f1_keywords:
- VC.Project.VCLinkerTool.WINMDKeyFile
ms.assetid: 65d88fdc-fff9-49ea-8cfc-b2f408741734
ms.openlocfilehash: 4b0c847bc5be6c73b78af4aa15b0074c712cc840
ms.sourcegitcommit: faa42c8a051e746d99dcebe70fd4bbaf3b023ace
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/15/2019
ms.locfileid: "57820399"
---
# <a name="winmdkeyfile-specify-winmd-key-file"></a>/WINMDKEYFILE (指定 winmd 金鑰檔)

指定金鑰或金鑰組簽署 Windows 執行階段中繼資料 (.winmd) 檔案。

```
/WINMDKEYFILE:filename
```

## <a name="remarks"></a>備註

類似於[/KEYFILE](keyfile-specify-key-or-key-pair-to-sign-an-assembly.md)套用到.winmd 檔案的連結器選項。

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 開發環境中設定這個連結器選項

1. 開啟專案的 [屬性頁]  對話方塊。 如需詳細資訊，請參閱 <<c0> [ 在 Visual Studio 中的設定 c + + 編譯器和組建屬性](../working-with-project-properties.md)。

1. 選取 **連結器**資料夾。

1. 選取  **Windows 中繼資料**屬性頁。

1. 在  **Windows 中繼資料金鑰檔**方塊中，輸入檔案位置。

## <a name="see-also"></a>另請參閱

[MSVC 連結器參考](linking.md)<br/>
[MSVC 連結器選項](linker-options.md)
