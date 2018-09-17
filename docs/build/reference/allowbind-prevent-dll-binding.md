---
title: -ALLOWBIND （防止 DLL 繫結） |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- VC.Project.VCLinkerTool.PreventDLLBinding
- /allowbind
dev_langs:
- C++
helpviewer_keywords:
- /ALLOWBIND linker option
- binding DLLs
- preventing DLL binding
- ALLOWBIND linker option
- -ALLOWBIND linker option
- DLLs [C++], preventing binding
ms.assetid: 30e37e24-12e4-407e-988a-39d357403598
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 536fc4f43cf227491ecae53cb5960e42ff79e081
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/17/2018
ms.locfileid: "45713618"
---
# <a name="allowbind-prevent-dll-binding"></a>/ALLOWBIND (阻止 DLL 繫結)

```
/ALLOWBIND[:NO]
```

## <a name="remarks"></a>備註

/ALLOWBIND:NO 在 DLL 的標頭中設定一個位元，向 Bind.exe 表示不允許繫結影像。 如果 DLL 已數位簽署，您便可能不想要繫結 DLL (繫結會使簽章無效)。

您可以編輯現有 DLL 的 /ALLOWBIND 功能[/ALLOWBIND](../../build/reference/allowbind.md) EDITBIN 公用程式的選項。

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 開發環境中設定這個連結器選項

1. 開啟專案的 [屬性頁]  對話方塊。 如需詳細資料，請參閱[使用專案屬性](../../ide/working-with-project-properties.md)。

1. 依序展開**組態屬性**，**連結器**，然後選取**命令列**。

1. 請輸入`/ALLOWBIND:NO`成**其他選項**。

### <a name="to-set-this-linker-option-programmatically"></a>若要以程式設計方式設定這個連結器選項

- 請參閱 <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>。

## <a name="see-also"></a>另請參閱

[設定連結器選項](../../build/reference/setting-linker-options.md)<br/>
[連結器選項](../../build/reference/linker-options.md)<br/>
[BindImage 函式](/windows/desktop/api/imagehlp/nf-imagehlp-bindimage)<br/>
[BindImageEx 函式](/windows/desktop/api/imagehlp/nf-imagehlp-bindimageex)