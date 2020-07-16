---
title: /HIGHENTROPYVA
ms.date: 06/12/2018
f1_keywords:
- /HIGHENTROPYVA
helpviewer_keywords:
- HIGHENTROPYVA editbin option
- -HIGHENTROPYVA editbin option
- /HIGHENTROPYVA editbin option
ms.assetid: ef4b7c63-440d-40ca-b39d-edefb3217505
ms.openlocfilehash: 1adc12c0673764460b4af5eb7cf3b394d9666e81
ms.sourcegitcommit: 6b3d793f0ef3bbb7eefaf9f372ba570fdfe61199
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/15/2020
ms.locfileid: "86404095"
---
# <a name="highentropyva"></a>/HIGHENTROPYVA

指定可執行檔映像是否支援高熵 64 位元位址空間配置隨機載入 (ASLR)。

## <a name="syntax"></a>語法

> **`/HIGHENTROPYVA`**[**`:NO`**]

## <a name="remarks"></a>備註

此選項會修改*可執行圖像*檔案的標頭（例如 *`.dll`* 或檔案 *`.exe`* ），以表示支援64位位址 ASLR。 若要產生效果，請在可執行檔及其相依的所有模組上設定選項。 接著，支援64位 ASLR 的作業系統，可以使用隨機的64位虛擬位址，在載入時間為可執行映射的區段重訂基底。 這個大型位址空間會使攻擊者較難猜到特定記憶體區域的位置。

根據預設，連結器會啟用 **`/HIGHENTROPYVA`** 64 位可執行檔映射。 此選項需要 [`/DYNAMICBASE`](dynamicbase.md) 和 [`/LARGEADDRESSAWARE`](largeaddressaware.md) ，這在預設情況下也會針對64位映射啟用。 **`/HIGHENTROPYVA`** 不適用於32位可執行檔映射，其中會忽略選項。 若要明確停用此選項，請使用 **`/HIGHENTROPYVA:NO`** 。

## <a name="see-also"></a>另請參閱

[EDITBIN 選項](editbin-options.md)\
[`/DYNAMICBASE`](dynamicbase.md)\
[`/LARGEADDRESSAWARE`](largeaddressaware.md)\
[Windows ISV 軟體安全性防禦](https://docs.microsoft.com/previous-versions/bb430720(v=msdn.10))
