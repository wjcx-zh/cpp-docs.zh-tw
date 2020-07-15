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
ms.openlocfilehash: b2ff9929de74d99fbc45e4f4ff38fd6b939697bc
ms.sourcegitcommit: 31a443c9998cf5cfbaff00fcf815b133f55b2426
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/14/2020
ms.locfileid: "86373823"
---
# <a name="highentropyva"></a>/HIGHENTROPYVA

指定可執行檔映像是否支援高熵 64 位元位址空間配置隨機載入 (ASLR)。

## <a name="syntax"></a>語法

> **/HIGHENTROPYVA**[**： NO**]

## <a name="remarks"></a>備註

此選項會修改*可執行檔映射*的標頭（.dll 檔案或 .exe 檔案），以指示是否支援具有64位位址的 ASLR。 在可執行檔和它所依據的所有模組上設定此選項時，支援 64 位元 ASLR 的作業系統可以使用 64 位元虛擬位址空間中的隨機位址，在載入時間為可執行映像的區段重訂基底。 這個大型位址空間會使攻擊者較難猜到特定記憶體區域的位置。

根據預設，連結器會啟用64位可執行檔映射的 **/HIGHENTROPYVA** 。 此選項需要[/LARGEADDRESSAWARE](largeaddressaware.md)，預設也會針對64位映射啟用此功能。 **/HIGHENTROPYVA**不適用於32位可執行檔映射，其中會忽略選項。 若要明確停用此選項，請使用 **/HIGHENTROPYVA： NO**。 若要讓此選項生效，您也必須設定[/DYNAMICBASE](dynamicbase.md)選項。

## <a name="see-also"></a>另請參閱

- [EDITBIN 選項](editbin-options.md)
- [/DYNAMICBASE](dynamicbase.md)
- [Windows ISV 軟體安全性防禦](https://docs.microsoft.com/previous-versions/bb430720(v=msdn.10))
