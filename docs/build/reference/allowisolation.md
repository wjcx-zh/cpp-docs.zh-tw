---
title: /ALLOWISOLATION
ms.date: 11/04/2016
f1_keywords:
- /ALLOWISOLATION_EDITBIN
helpviewer_keywords:
- -ALLOWISOLATION editbin option
- /ALLOWISOLATION editbin option
- ALLOWISOLATION editbin option
ms.assetid: 91430344-f64f-491a-a5a5-7ea3b21cbe68
ms.openlocfilehash: 3dae8ee83e25492fab0ba2c6a55681728d5f3453
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/17/2020
ms.locfileid: "79440367"
---
# <a name="allowisolation"></a>/ALLOWISOLATION

指定資訊清單查閱的行為。

## <a name="syntax"></a>語法

```

/ALLOWISOLATION[:NO]
```

## <a name="remarks"></a>備註

**/ALLOWISOLATION**會導致作業系統執行資訊清單查閱和載入。

**/ALLOWISOLATION**是預設值。

**/ALLOWISOLATION： [否**] 表示載入可執行檔的方式就好像沒有資訊清單一樣，而且會導致[EDITBIN 參考](editbin-reference.md)在選擇性標頭的 `DllCharacteristics` 欄位中設定 `IMAGE_DLLCHARACTERISTICS_NO_ISOLATION` 位。

可執行檔停用隔離時，Windows 載入器並不會試圖尋找新建立處理序的應用程式資訊清單。 新的進程沒有預設啟用內容，即使可執行檔本身中有資訊清單，或者如果有資訊清單具有名稱*可執行檔*名稱 .exe。

## <a name="see-also"></a>另請參閱

[EDITBIN 選項](editbin-options.md)<br/>
[/ALLOWISOLATION (資訊清單查閱)](allowisolation-manifest-lookup.md)<br/>
[資訊清單檔案參考](/windows/win32/SbsCs/manifest-files-reference)
