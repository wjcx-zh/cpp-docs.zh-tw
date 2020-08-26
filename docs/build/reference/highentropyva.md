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
ms.openlocfilehash: 80e34a3f57974e1af6afb65196697cce9aa344b1
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/25/2020
ms.locfileid: "88834995"
---
# <a name="highentropyva"></a>/HIGHENTROPYVA

指定可執行檔映像是否支援高熵 64 位元位址空間配置隨機載入 (ASLR)。

## <a name="syntax"></a>語法

> **`/HIGHENTROPYVA`**[**`:NO`**]

## <a name="remarks"></a>備註

此選項會修改 *可執行檔圖像* 檔案的標頭 (例如 *`.dll`* 或檔案 *`.exe`*) ，以表示支援64位位址 ASLR。 若要產生效果，請在可執行檔及其相依的所有模組上設定選項。 然後支援64位 ASLR 的作業系統，可以在載入時使用隨機的64位虛擬位址來將可執行映射的區段重定基底。 這個大型位址空間會使攻擊者較難猜到特定記憶體區域的位置。

根據預設，連結器會啟用 **`/HIGHENTROPYVA`** 64 位可執行檔映射。 此選項同時需要 [`/DYNAMICBASE`](dynamicbase.md) 和 [`/LARGEADDRESSAWARE`](largeaddressaware.md) ，64位的映射預設也會啟用此選項。 **`/HIGHENTROPYVA`** 不適用於可忽略選項的32位可執行檔映射。 若要明確停用此選項，請使用 **`/HIGHENTROPYVA:NO`** 。

## <a name="see-also"></a>另請參閱

[EDITBIN 選項](editbin-options.md)\
[`/DYNAMICBASE`](dynamicbase.md)\
[`/LARGEADDRESSAWARE`](largeaddressaware.md)\
[Windows ISV 軟體安全性防禦措施](/previous-versions/bb430720(v=msdn.10))
