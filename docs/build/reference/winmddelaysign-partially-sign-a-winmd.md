---
title: /WINMDDELAYSIGN (部分簽署 winmd)
ms.date: 11/04/2016
f1_keywords:
- VC.Project.VCLinkerTool.WINMDDelaySign
ms.assetid: 445cd602-62cb-400a-8e3a-4beb6572724d
ms.openlocfilehash: 5e6eab3fbc40543b634f03da826d3bd3477b9623
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62316596"
---
# <a name="winmddelaysign-partially-sign-a-winmd"></a>/WINMDDELAYSIGN (部分簽署 winmd)

可將公開金鑰放在檔案中的 Windows 執行階段中繼資料 (.winmd) 檔案的部分簽署。

```
/WINMDDELAYSIGN[:NO]
```

## <a name="remarks"></a>備註

類似於[/DELAYSIGN](delaysign-partially-sign-an-assembly.md)套用至.winmd 檔案的連結器選項。 使用 **/WINMDDELAYSIGN**如果您想要將僅將公開金鑰放在.winmd 檔案。 根據預設，連結器作用如同 **/winmddelaysign: no**指定; 亦即，不會簽署 winmd 檔案。

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 開發環境中設定這個連結器選項

1. 開啟專案的 [屬性頁]  對話方塊。 如需詳細資訊，請參閱 <<c0> [ 設定C++Visual Studio 中的編譯器和組建屬性](../working-with-project-properties.md)。</c0>

1. 選取 **連結器**資料夾。

1. 選取  **Windows 中繼資料**屬性頁。

1. 在  **Windows 中繼資料延遲簽署**下拉式清單方塊中，選取您想要的選項。

## <a name="see-also"></a>另請參閱

[MSVC 連結器參考](linking.md)<br/>
[MSVC 連結器選項](linker-options.md)
