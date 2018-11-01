---
title: /HIGHENTROPYVA (支援 64 位元 ASLR)
ms.date: 06/12/2018
ms.assetid: fe35f9f7-d28e-4694-9aeb-a79db06168e0
ms.openlocfilehash: a8bd1b2231530c0f1632b244edaf36ee14ed65b8
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50534793"
---
# <a name="highentropyva-support-64-bit-aslr"></a>/HIGHENTROPYVA (支援 64 位元 ASLR)

指定可執行映像是否支援高熵 64 位元位址空間配置隨機載入 (ASLR)。

## <a name="syntax"></a>語法

> **/ HIGHENTROPYVA**[**: NO**]

## <a name="remarks"></a>備註

**/ HIGHENTROPYVA**修改的標頭*可執行映像*，.dll 檔或.exe 檔案，以指出 ASLR 是否可以使用整個 64 位元位址空間。 在可執行檔和它所依據的所有模組上設定此選項時，支援 64 位元 ASLR 的作業系統可以使用 64 位元虛擬位址空間中的隨機位址，在載入時間為可執行映像的區段重訂基底。 這個大型位址空間會使攻擊者較難猜到特定記憶體區域的位置。

根據預設， **/HIGHENTROPYVA**都可使用 64 位元可執行映像。 這個選項需要[/LARGEADDRESSAWARE](largeaddressaware-handle-large-addresses.md)，這也會啟用預設值為 64 位元映像。 **/HIGHENTROPYVA**不適用於 32 位元可執行映像，連結器會忽略選項。 若要明確停用此選項，請使用 **/highentropyva: no**。

針對 **/HIGHENTROPYVA**若要在載入期間，會影響[/DYNAMICBASE](dynamicbase-use-address-space-layout-randomization.md)也必須啟用。 **/DYNAMICBASE**依預設，會啟用與，才能啟用 Windows Vista 和更新版本的作業系統中的 ASLR。 舊版的 Windows 會忽略這個旗標。

### <a name="to-set-this-linker-option-in-visual-studio"></a>在 Visual Studio 中設定這個連結器選項

1. 開啟專案的 [ **屬性頁** ] 對話方塊。 如需詳細資訊，請參閱[使用專案屬性](../../ide/working-with-project-properties.md)。

1. 選取 **組態屬性** > **連結器** > **命令列**屬性頁。

1. 在 **其他選項**，輸入`/HIGHENTROPYVA`或`/HIGHENTROPYVA:NO`。

## <a name="see-also"></a>另請參閱

- [設定連結器選項](../../build/reference/setting-linker-options.md)
- [連結器選項](../../build/reference/linker-options.md)
- [/DYNAMICBASE](dynamicbase-use-address-space-layout-randomization.md)
- [/LARGEADDRESSAWARE](largeaddressaware-handle-large-addresses.md)
- [Windows ISV 軟體安全性防禦措施](https://msdn.microsoft.com/library/bb430720.aspx)
