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
ms.openlocfilehash: ac9d1f067259b092a261702b51f2355d4f908469
ms.sourcegitcommit: bff17488ac5538b8eaac57156a4d6f06b37d6b7f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2019
ms.locfileid: "57417433"
---
# <a name="allowisolation"></a>/ALLOWISOLATION

指定資訊清單查閱的行為。

## <a name="syntax"></a>語法

```

/ALLOWISOLATION[:NO]
```

## <a name="remarks"></a>備註

**/ALLOWISOLATION**會導致作業系統查閱和載入資訊清單。

**/ALLOWISOLATION**是預設值。

**/ALLOWISOLATION:NO**指出已載入可執行檔，好像沒有資訊清單，並會使[EDITBIN 參考](../../build/reference/editbin-reference.md)來設定`IMAGE_DLLCHARACTERISTICS_NO_ISOLATION`選擇性標頭的位元`DllCharacteristics`欄位。

可執行檔停用隔離時，Windows 載入器並不會試圖尋找新建立處理序的應用程式資訊清單。 新的處理序沒有預設啟用內容，即使可執行檔本身的資訊清單，或者如果沒有資訊清單具有名稱*可執行檔名稱*.exe.manifest。

## <a name="see-also"></a>另請參閱

[EDITBIN 選項](../../build/reference/editbin-options.md)<br/>
[/ALLOWISOLATION (資訊清單查閱)](../../build/reference/allowisolation-manifest-lookup.md)<br/>
[資訊清單檔案參考](/windows/desktop/SbsCs/manifest-files-reference)
