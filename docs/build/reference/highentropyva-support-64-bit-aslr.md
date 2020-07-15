---
title: /HIGHENTROPYVA (支援 64 位元 ASLR)
ms.date: 06/12/2018
ms.assetid: fe35f9f7-d28e-4694-9aeb-a79db06168e0
ms.openlocfilehash: 8f8601d89e8456461aac3d91f9fd2cfda216d7f5
ms.sourcegitcommit: 31a443c9998cf5cfbaff00fcf815b133f55b2426
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/14/2020
ms.locfileid: "86373836"
---
# <a name="highentropyva-support-64-bit-aslr"></a>/HIGHENTROPYVA (支援 64 位元 ASLR)

指定可執行檔映像是否支援高熵 64 位元位址空間配置隨機載入 (ASLR)。

## <a name="syntax"></a>語法

> **/HIGHENTROPYVA**[**： NO**]

## <a name="remarks"></a>備註

**/HIGHENTROPYVA**會修改*可執行映射*的標頭，也就是 .dll 檔案或 .exe 檔案，以指出 ASLR 是否可以使用整個64位的位址空間。 在可執行檔和它所依據的所有模組上設定此選項時，支援 64 位元 ASLR 的作業系統可以使用 64 位元虛擬位址空間中的隨機位址，在載入時間為可執行映像的區段重訂基底。 這個大型位址空間會使攻擊者較難猜到特定記憶體區域的位置。

根據預設，會啟用64位可執行檔映射的 **/HIGHENTROPYVA** 。 此選項需要[/LARGEADDRESSAWARE](largeaddressaware-handle-large-addresses.md)，預設也會針對64位映射啟用此功能。 **/HIGHENTROPYVA**不適用於32位可執行檔映射，其中連結器會忽略選項。 若要明確停用此選項，請使用 **/HIGHENTROPYVA： NO**。

若要讓 **/HIGHENTROPYVA**在載入時有效果，也必須啟用[/DYNAMICBASE](dynamicbase-use-address-space-layout-randomization.md) 。 **/DYNAMICBASE**預設為啟用，而且必須在 Windows Vista 和更新版本的作業系統中啟用 ASLR。 舊版的 Windows 會忽略此旗標。

### <a name="to-set-this-linker-option-in-visual-studio"></a>在 Visual Studio 中設定這個連結器選項

1. 開啟專案的 [ **屬性頁** ] 對話方塊。 如需詳細資料，請參閱[在 Visual Studio 中設定 C ++ 編譯器和組建屬性](../working-with-project-properties.md)。

1. 選取 [設定] [**屬性**] [  >  **連結器**  >  **命令列**] 屬性頁。

1. 在 [**其他選項**] 中，輸入 `/HIGHENTROPYVA` 或 `/HIGHENTROPYVA:NO` 。

## <a name="see-also"></a>另請參閱

- [MSVC 連結器參考](linking.md)
- [MSVC 連結器選項](linker-options.md)
- [/DYNAMICBASE](dynamicbase-use-address-space-layout-randomization.md)
- [/LARGEADDRESSAWARE](largeaddressaware-handle-large-addresses.md)
- [Windows ISV 軟體安全性防禦](https://docs.microsoft.com/previous-versions/bb430720(v=msdn.10))
