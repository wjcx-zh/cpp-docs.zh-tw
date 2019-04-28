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
ms.openlocfilehash: 90d3c868eaab85e3b1a2a416c9aa14b0e27ec8f9
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62270220"
---
# <a name="highentropyva"></a>/HIGHENTROPYVA

指定可執行檔映像是否支援高熵 64 位元位址空間配置隨機載入 (ASLR)。

## <a name="syntax"></a>語法

> **/HIGHENTROPYVA**[**:NO**]

## <a name="remarks"></a>備註

這個選項修改的標頭*可執行映像*，.dll 檔或.exe 檔案，以指示是否支援 64 位元位址的 ASLR。 在可執行檔和它所依據的所有模組上設定此選項時，支援 64 位元 ASLR 的作業系統可以使用 64 位元虛擬位址空間中的隨機位址，在載入時間為可執行映像的區段重訂基底。 這個大型位址空間會使攻擊者較難猜到特定記憶體區域的位置。

根據預設，連結器可讓 **/HIGHENTROPYVA** 64 位元可執行檔映像。 這個選項需要[/LARGEADDRESSAWARE](largeaddressaware.md)，這也會啟用預設值為 64 位元映像。 **/HIGHENTROPYVA**不適用於 32 位元可執行映像，已忽略選項。 若要明確停用此選項，請使用 **/highentropyva: no**。 此選項才有效果，請[/DYNAMICBASE](dynamicbase.md)也必須設定選項。

## <a name="see-also"></a>另請參閱

- [EDITBIN 選項](editbin-options.md)
- [/DYNAMICBASE](dynamicbase.md)
- [Windows ISV 軟體安全性防禦措施](https://msdn.microsoft.com/library/bb430720.aspx)
