---
title: /ALLOWISOLATION
ms.date: 11/04/2016
f1_keywords:
- /ALLOWISOLATION
helpviewer_keywords:
- -ALLOWISOLATION editbin option
- /ALLOWISOLATION editbin option
- ALLOWISOLATION editbin option
ms.assetid: 91430344-f64f-491a-a5a5-7ea3b21cbe68
ms.openlocfilehash: 359a68d5ec0a8c7390b5f0343530864e880a057c
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/15/2019
ms.locfileid: "69493122"
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

**/ALLOWISOLATION: NO**表示會載入可執行檔, 就好像沒有資訊清單一樣, 並會導致[EDITBIN 參考](editbin-reference.md)在選擇性標頭的`IMAGE_DLLCHARACTERISTICS_NO_ISOLATION` `DllCharacteristics`欄位中設定位。

可執行檔停用隔離時，Windows 載入器並不會試圖尋找新建立處理序的應用程式資訊清單。 新的進程沒有預設啟用內容, 即使可執行檔本身中有資訊清單, 或者如果有資訊清單具有名稱*可執行檔*名稱 .exe。

## <a name="see-also"></a>另請參閱

[EDITBIN 選項](editbin-options.md)<br/>
[/ALLOWISOLATION (資訊清單查閱)](allowisolation-manifest-lookup.md)<br/>
[資訊清單檔案參考](/windows/win32/SbsCs/manifest-files-reference)
