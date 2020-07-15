---
title: /DYNAMICBASE (使用位址空間隨機載入)
ms.date: 06/12/2018
f1_keywords:
- VC.Project.VCLinkerTool.RandomizedBaseAddress
helpviewer_keywords:
- -DYNAMICBASE linker option
- /DYNAMICBASE linker option
- DYNAMICBASE linker option
ms.assetid: 6c0ced8e-fe9c-4b63-b956-eb8a55fbceb2
ms.openlocfilehash: 206c054f383418e176e00f4155f9f6a25a37e253
ms.sourcegitcommit: 31a443c9998cf5cfbaff00fcf815b133f55b2426
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/14/2020
ms.locfileid: "86373706"
---
# <a name="dynamicbase-use-address-space-layout-randomization"></a>/DYNAMICBASE (使用位址空間隨機載入)

指定是否要產生可執行映射，以在載入時使用 windows Vista 中第一次提供的 Windows 的位址空間配置隨機載入（ASLR）功能來隨機重定基底。

## <a name="syntax"></a>語法

> **/DYNAMICBASE**[**： NO**]

## <a name="remarks"></a>備註

**/DYNAMICBASE**選項會修改*可執行映射*（.dll 或 .exe 檔案）的標頭，以指出是否應在載入時隨機重定基底應用程式，並啟用虛擬位址配置隨機，這會影響堆積、堆疊和其他作業系統配置的虛擬記憶體位置。 **/DYNAMICBASE**選項同時適用于32位和64位的映射。 Windows Vista 和更新版本的作業系統都支援 ASLR。 舊版作業系統會忽略此選項。

根據預設，會啟用 **/DYNAMICBASE** 。 若要停用此選項，請使用 **/DYNAMICBASE： NO**。 必須要有 **/DYNAMICBASE**選項， [/HIGHENTROPYVA](highentropyva-support-64-bit-aslr.md)選項才會生效。

### <a name="to-set-this-linker-option-in-visual-studio"></a>在 Visual Studio 中設定這個連結器選項

1. 開啟專案的 [ **屬性頁** ] 對話方塊。 如需詳細資料，請參閱[在 Visual Studio 中設定 C ++ 編譯器和組建屬性](../working-with-project-properties.md)。

1. 選取 [設定**屬性**  >  **連結器**] 的 [  >  **Advanced** ] 屬性頁。

1. 修改**隨機化基底位址**屬性。

### <a name="to-set-this-linker-option-programmatically"></a>若要以程式設計方式設定這個連結器選項

- 請參閱＜ <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.RandomizedBaseAddress%2A> ＞。

## <a name="see-also"></a>另請參閱

- [MSVC 連結器參考](linking.md)
- [MSVC 連結器選項](linker-options.md)
- [/HIGHENTROPYVA](highentropyva-support-64-bit-aslr.md)
- [Windows ISV 軟體安全性防禦](https://docs.microsoft.com/previous-versions/bb430720(v=msdn.10))
