---
title: -nologo （隱藏程式啟始資訊） （C/c + +） |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- VC.Project.VCCLWCECompilerTool.SuppressStartupBanner
- VC.Project.VCCLCompilerTool.SuppressStartupBanner
dev_langs:
- C++
helpviewer_keywords:
- -nologo compiler option [C++]
- /nologo compiler option [C++]
- nologo compiler option [C++]
- banners, suppressing startup
ms.assetid: 75930d8b-b11c-4db8-99e5-b52f97da0693
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 36f1d1771abb56bd22e8239923fe2e3c15b1588f
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/17/2018
ms.locfileid: "45711863"
---
# <a name="nologo-suppress-startup-banner-cc"></a>/nologo (隱藏程式啟始資訊) (C/C++)

會隱藏編譯器啟動時顯示著作權橫幅以及編譯期間顯示的告知性訊息。

## <a name="syntax"></a>語法

```
/nologo
```

## <a name="remarks"></a>備註

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 開發環境中設定這個編譯器選項

1. 開啟專案的 [屬性頁]  對話方塊。 如需詳細資料，請參閱[使用專案屬性](../../ide/working-with-project-properties.md)。

1. 按一下 [C/C++]  資料夾。

1. 按一下 **一般**屬性頁。

1. 修改**隱藏程式啟始資訊**屬性。

### <a name="to-set-this-compiler-option-programmatically"></a>若要以程式方式設定這個編譯器選項

- 請參閱 <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.SuppressStartupBanner%2A>。

## <a name="see-also"></a>另請參閱

[編譯器選項](../../build/reference/compiler-options.md)<br/>
[設定編譯器選項](../../build/reference/setting-compiler-options.md)