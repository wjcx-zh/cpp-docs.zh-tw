---
title: /SWAPRUN (將連結器輸出載入至交換檔)
ms.date: 11/04/2016
f1_keywords:
- VC.Project.VCLinkerTool.SwapRunFromNet
- /swaprun
- VC.Project.VCLinkerTool.SwapRunFromCD
helpviewer_keywords:
- -SWAPRUN linker option
- files [C++], LINK
- LINK tool [C++], output
- linker [C++], copying output to swap file
- swap file for linker output
- output files, linker
- /SWAPRUN linker option
- SWAPRUN linker option
ms.assetid: 4a1e7f46-4399-4161-8dfc-d6a71beaf683
ms.openlocfilehash: bd0b3a46f52ec9b5a292e2f45671523d8c5cdf5e
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62317545"
---
# <a name="swaprun-load-linker-output-to-swap-file"></a>/SWAPRUN (將連結器輸出載入至交換檔)

```
/SWAPRUN:{NET|CD}
```

## <a name="remarks"></a>備註

/SWAPRUN 選項會告訴連結器輸出到交換檔，然後從該處執行映像第一次複製作業系統。 這是 Windows NT 4.0 （和更新版本） 功能。

如果指定 NET，作業系統會先將二進位檔映像從網路複製到交換檔，並將其從該處。 此選項可用於透過網路執行應用程式。 指定 CD 時，作業系統就會卸除式磁碟的映像複製到分頁檔，並再將其載入。

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 開發環境中設定這個連結器選項

1. 開啟專案的 [屬性頁]  對話方塊。 如需詳細資訊，請參閱 <<c0> [ 設定C++Visual Studio 中的編譯器和組建屬性](../working-with-project-properties.md)。</c0>

1. 按一下 **連結器**資料夾。

1. 按一下 **系統**屬性頁。

1. 修改下列屬性之一：

   - **從光碟片交換執行**

   - **從網路交換執行**

### <a name="to-set-this-linker-option-programmatically"></a>若要以程式設計方式設定這個連結器選項

1. 請參閱 <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.SwapRunFromCD%2A> 和 <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.SwapRunFromNet%2A> 屬性。

## <a name="see-also"></a>另請參閱

[MSVC 連結器參考](linking.md)<br/>
[MSVC 連結器選項](linker-options.md)
