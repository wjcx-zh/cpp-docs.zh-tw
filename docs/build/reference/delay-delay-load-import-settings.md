---
title: /DELAY (延遲載入匯入設定)
ms.date: 11/04/2016
f1_keywords:
- /delay
- VC.Project.VCLinkerTool.DelayNoBind
- VC.Project.VCLinkerTool.SupportUnloadOfDelayLoadedDLL
- VC.Project.VCLinkerTool.DelayUnload
helpviewer_keywords:
- delayed loading of DLLs, /DELAY option
- DELAY linker option
- /DELAY linker option
- -DELAY linker option
ms.assetid: 9334b332-cc58-4dae-b10f-a4c75972d50c
ms.openlocfilehash: ef6f5f768cf86f470d1322fa2a7bee6db794c2ef
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/15/2019
ms.locfileid: "69493000"
---
# <a name="delay-delay-load-import-settings"></a>/DELAY (延遲載入匯入設定)

```
/DELAY:UNLOAD
/DELAY:NOBIND
```

## <a name="remarks"></a>備註

/DELAY 選項控制 Dll 的[延遲載入](linker-support-for-delay-loaded-dlls.md):

- UNLOAD 限定詞會告知延遲載入 Helper 函式，支援明確卸載 DLL。 匯入位址表 (IAT) 會重設為其原始形式，這會使 IAT 指標失效，並導致它們被覆寫。

   如果您未選取 [卸載], 任何對[FUnloadDelayLoadedDLL](explicitly-unloading-a-delay-loaded-dll.md)的呼叫都會失敗。

- NOBIND 限定詞會告知連結器不在最終映像檔中包含可繫結 IAT。 預設會是針對延遲載入 DLL 建立可繫結 IAT。 所產生的映像檔無法靜態繫結 (具有可繫結 IAT 的映像檔在執行之前，可能是靜態繫結的)。請參閱[/BIND](bind.md)。

   如果 DLL 已系結, helper 函式會嘗試使用系結資訊, 而不是在每個參考的匯入上呼叫[GetProcAddress](/windows/win32/api/libloaderapi/nf-libloaderapi-getprocaddress) 。 如果時間戳記或慣用位址與那些已載入 DLL 的時間戳記或慣用位址不相符，則 Helper 函式會假設已繫結 IAT 已過期，且會像已繫結 IAT 不存在那樣來進行處理。

   NOBIND 會導致您的程式映像檔變大，但可加速 DLL 的載入。 如果您從未繫結 DLL，則 NOBIND 會防止產生已繫結 IAT。

若要指定 Dll 以延遲載入, 請使用[/DELAYLOAD](delayload-delay-load-import.md)選項。

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 開發環境中設定這個連結器選項

1. 開啟專案的 [屬性頁] 對話方塊。 如需詳細資訊, 請參閱[在 Visual Studio 中設定C++編譯器和組建屬性](../working-with-project-properties.md)。

1. 展開 [設定] [**屬性**]、[**連結器**], 然後選取 [ **Advanced**]。

1. 修改 [**延遲載入 DLL** ] 屬性。

### <a name="to-set-this-linker-option-programmatically"></a>若要以程式設計方式設定這個連結器選項

- 請參閱 <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.DelayLoadDLLs%2A>。

## <a name="see-also"></a>另請參閱

[MSVC 連結器參考](linking.md)<br/>
[MSVC 連結器選項](linker-options.md)
