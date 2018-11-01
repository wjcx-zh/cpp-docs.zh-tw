---
title: /NOLOGO (隱藏程式啟始資訊) (連結器)
ms.date: 11/04/2016
f1_keywords:
- VC.Project.VCLinkerTool.SuppressStartupBanner
- /nologo
helpviewer_keywords:
- suppress startup banner linker option
- -NOLOGO linker option
- /NOLOGO linker option
- copyright message
- version numbers, preventing linker display
- banners, suppressing startup
- NOLOGO linker option
ms.assetid: 3b20dddd-eca6-4545-a331-9f70bf720197
ms.openlocfilehash: d246da2e10f7c16f7c194962841e2e44d1fd1758
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50515540"
---
# <a name="nologo-suppress-startup-banner-linker"></a>/NOLOGO (隱藏程式啟始資訊) (連結器)

```
/NOLOGO
```

## <a name="remarks"></a>備註

/NOLOGO 選項不顯示著作權訊息或版本號碼。

此選項也會隱藏命令檔的回應。 如需詳細資訊，請參閱 < [LINK 命令檔](../../build/reference/link-command-files.md)。

根據預設，這項資訊會傳送至輸出視窗，連結器。 在命令列中，它會傳送至標準輸出，並可以重新導向至檔案。

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 開發環境中設定這個連結器選項

1. 這個選項應該只用於從命令列。

### <a name="to-set-this-linker-option-programmatically"></a>若要以程式設計方式設定這個連結器選項

1. 這個連結器選項不能以程式設計方式變更。

## <a name="see-also"></a>另請參閱

[設定連結器選項](../../build/reference/setting-linker-options.md)<br/>
[連結器選項](../../build/reference/linker-options.md)