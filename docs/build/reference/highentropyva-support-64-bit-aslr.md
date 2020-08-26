---
title: /HIGHENTROPYVA (支援 64 位元 ASLR)
ms.date: 06/12/2018
ms.assetid: fe35f9f7-d28e-4694-9aeb-a79db06168e0
ms.openlocfilehash: ead296b1bd31171fb1a187685f407f6a0cf8a74c
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/25/2020
ms.locfileid: "88835021"
---
# <a name="highentropyva-support-64-bit-aslr"></a>/HIGHENTROPYVA (支援 64 位元 ASLR)

指定可執行檔映像是否支援高熵 64 位元位址空間配置隨機載入 (ASLR)。

## <a name="syntax"></a>語法

> **`/HIGHENTROPYVA`**[**`:NO`**]

## <a name="remarks"></a>備註

**`/HIGHENTROPYVA`** 修改 *可執行檔圖像* 檔案的標頭 (例如 *`.dll`* 或檔案 *`.exe`*) ，以指出 ASLR 是否可以使用整個64位位址空間。  若要產生效果，請在可執行檔及其相依的所有模組上設定選項。 然後，支援64位 ASLR 的作業系統，可以在載入時使用64位隨機虛擬位址來將可執行映射的區段重訂基底。 這個大型位址空間會使攻擊者較難猜到特定記憶體區域的位置。

根據預設， **`/HIGHENTROPYVA`** 會啟用64位可執行檔映射。 這個選項需要 [`/LARGEADDRESSAWARE`](largeaddressaware-handle-large-addresses.md) ，預設也會針對64位的映射啟用。 **`/HIGHENTROPYVA`** 不適用於32位的可執行映射，連結器會忽略此選項。 若要明確停用此選項，請使用 **`/HIGHENTROPYVA:NO`** 。

**`/HIGHENTROPYVA`** 若要在載入時產生效果， [`/DYNAMICBASE`](dynamicbase-use-address-space-layout-randomization.md) 也必須啟用。 **`/DYNAMICBASE`** 預設為啟用，而且必須在 Windows Vista 和更新版本的作業系統中啟用 ASLR。 舊版的 Windows 會忽略此旗標。

### <a name="to-set-this-linker-option-in-visual-studio"></a>在 Visual Studio 中設定這個連結器選項

1. 開啟專案的 [ **屬性頁** ] 對話方塊。 如需詳細資料，請參閱[在 Visual Studio 中設定 C ++ 編譯器和組建屬性](../working-with-project-properties.md)。

1. 選取 [設定**屬性**  >  **連結器**  >  **命令列**] 屬性頁。

1. 在 [ **其他選項**] 中，輸入 `/HIGHENTROPYVA` 或 `/HIGHENTROPYVA:NO` 。

## <a name="see-also"></a>另請參閱

- [MSVC 連結器參考](linking.md)
- [MSVC 連結器選項](linker-options.md)
- [`/DYNAMICBASE`](dynamicbase-use-address-space-layout-randomization.md)
- [`/LARGEADDRESSAWARE`](largeaddressaware-handle-large-addresses.md)
- [Windows ISV 軟體安全性防禦措施](/previous-versions/bb430720(v=msdn.10))
