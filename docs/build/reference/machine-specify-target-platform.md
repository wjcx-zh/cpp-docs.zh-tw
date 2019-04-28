---
title: /MACHINE (指定目標平台)
ms.date: 11/04/2016
f1_keywords:
- VC.Project.VCLinkerTool.TargetMachine
- /machine
helpviewer_keywords:
- mapfiles, creating linker
- target platform
- -MACHINE linker option
- /MACHINE linker option
- MACHINE linker option
ms.assetid: 8d41bf4b-7e53-4ab9-9085-d852b08d31c2
ms.openlocfilehash: e64aa7b2ca9e50ebdc0760f64a9b25e851b45310
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62321718"
---
# <a name="machine-specify-target-platform"></a>/MACHINE (指定目標平台)

```
/MACHINE:{ARM|EBC|X64|X86}
```

## <a name="remarks"></a>備註

/MACHINE 選項會指定程式的目標平台。

通常，您不需指定 /MACHINE 選項。 連結會推斷.obj 檔中的機器類型。 不過，在某些情況下，連結無法判斷的機器類型和問題[連結器工具錯誤 LNK1113](../../error-messages/tool-errors/linker-tools-error-lnk1113.md)。 如果發生這類錯誤，請指定 /MACHINE。

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 開發環境中設定這個連結器選項

1. 開啟專案的 [屬性頁]  對話方塊。 如需詳細資訊，請參閱 <<c0> [ 設定C++Visual Studio 中的編譯器和組建屬性](../working-with-project-properties.md)。</c0>

1. 按一下 **連結器**資料夾。

1. 按一下 **進階**屬性頁。

1. 修改**目標機器**屬性。

### <a name="to-set-this-linker-option-programmatically"></a>若要以程式設計方式設定這個連結器選項

1. 請參閱 <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.TargetMachine%2A>。

## <a name="see-also"></a>另請參閱

[MSVC 連結器參考](linking.md)<br/>
[MSVC 連結器選項](linker-options.md)
