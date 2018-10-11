---
title: -DELAY （延遲載入匯入設定） |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /delay
- VC.Project.VCLinkerTool.DelayNoBind
- VC.Project.VCLinkerTool.SupportUnloadOfDelayLoadedDLL
- VC.Project.VCLinkerTool.DelayUnload
dev_langs:
- C++
helpviewer_keywords:
- delayed loading of DLLs, /DELAY option
- DELAY linker option
- /DELAY linker option
- -DELAY linker option
ms.assetid: 9334b332-cc58-4dae-b10f-a4c75972d50c
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 086fab7d1d50f96ab05c38f2e6d524d7ff344e02
ms.sourcegitcommit: 3a141cf07b5411d5f1fdf6cf67c4ce928cf389c3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/11/2018
ms.locfileid: "49081912"
---
# <a name="delay-delay-load-import-settings"></a>/DELAY (延遲載入匯入設定)

```
/DELAY:UNLOAD
/DELAY:NOBIND
```

## <a name="remarks"></a>備註

/DELAY 選項會控制[延遲載入](../../build/reference/linker-support-for-delay-loaded-dlls.md)的 Dll:

- UNLOAD 限定詞會告知延遲載入 Helper 函式，支援明確卸載 DLL。 匯入位址表 (IAT) 會重設為其原始形式，這會使 IAT 指標失效，並導致它們被覆寫。

   如果您未選取 UNLOAD，先呼叫[FUnloadDelayLoadedDLL](../../build/reference/explicitly-unloading-a-delay-loaded-dll.md)將會失敗。

- NOBIND 限定詞會告知連結器不在最終映像檔中包含可繫結 IAT。 預設會是針對延遲載入 DLL 建立可繫結 IAT。 所產生的映像檔無法靜態繫結  (具有可繫結 IAT 的映像檔在執行之前，可能是靜態繫結的)。請參閱[繫結/](../../build/reference/bind.md)。

   如果已繫結 DLL，helper 函式會嘗試使用的繫結的資訊，而不是呼叫[GetProcAddress](/windows/desktop/api/libloaderapi/nf-libloaderapi-getprocaddress)上每個參考匯入。 如果時間戳記或慣用位址與那些已載入 DLL 的時間戳記或慣用位址不相符，則 Helper 函式會假設已繫結 IAT 已過期，且會像已繫結 IAT 不存在那樣來進行處理。

   NOBIND 會導致您的程式映像檔變大，但可加速 DLL 的載入。 如果您從未繫結 DLL，則 NOBIND 會防止產生已繫結 IAT。

若要指定要延遲載入的 Dll，請使用[/DELAYLOAD](../../build/reference/delayload-delay-load-import.md)選項。

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 開發環境中設定這個連結器選項

1. 開啟專案的 [屬性頁]  對話方塊。 如需資訊，請參閱[使用專案屬性](../../ide/working-with-project-properties.md)。

1. 依序展開**組態屬性**，**連結器**，然後選取**進階**。

1. 修改**延遲載入 DLL**屬性。

### <a name="to-set-this-linker-option-programmatically"></a>若要以程式設計方式設定這個連結器選項

- 請參閱 <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.DelayLoadDLLs%2A>。

## <a name="see-also"></a>另請參閱

[設定連結器選項](../../build/reference/setting-linker-options.md)<br/>
[連結器選項](../../build/reference/linker-options.md)