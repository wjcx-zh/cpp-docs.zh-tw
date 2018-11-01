---
title: 保留的字
ms.date: 11/04/2016
f1_keywords:
- code
- CONFORMING
- DISCARDABLE
- Description
- base
- APPLOADER
- Data
- DYNAMIC
- DEV386
helpviewer_keywords:
- .def files [C++], reserved words
- def files [C++], reserved words
- linker [C++], reserved words
- reserved words [C++]
ms.assetid: 9b9f49e5-0739-45ab-a37e-81e3915ceb25
ms.openlocfilehash: 360baf479f9100483fe694ca8860dfc1d7ebfe11
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50502462"
---
# <a name="reserved-words"></a>保留的字

下列為保留字，連結器。 這些名稱可用來當做引數[模組定義陳述式](../../build/reference/module-definition-dot-def-files.md)才以雙引號括住的名稱 ("")。

||||
|-|-|-|
|**APPLOADER**<sup>1</sup>|**INITINSTANCE**<sup>2</sup>|**預先載入**|
|**基底**|**IOPL**|**私用**|
|**程式碼**|**媒體櫃**<sup>1</sup>|**PROTMODE**<sup>2</sup>|
|**符合**|**LOADONCALL**<sup>1</sup>|**純**<sup>1</sup>|
|**資料**|**LONGNAMES**<sup>2</sup>|**唯讀**|
|**描述**|**可移動**<sup>1</sup>|**讀寫**|
|**DEV386**|**MOVEABLE**<sup>1</sup>|**REALMODE**<sup>1</sup>|
|**可捨棄**|**多個**|**常駐**|
|**動態**|**名稱**|**RESIDENTNAME**<sup>1</sup>|
|**僅執行**|**NEWFILES**<sup>2</sup>|**區段**|
|**EXECUTEONLY**|**NODATA**<sup>1</sup>|**區段**|
|**執行讀取**|**NOIOPL**<sup>1</sup>|**共用**|
|**EXETYPE**|**NONAME**|**單一**|
|**EXPORTS**|**不合格**<sup>1</sup>|**STACKSIZE**|
|**固定**<sup>1</sup>|**NONDISCARDABLE**|**STUB**|
|**函式**<sup>2</sup>|**NONE**|**版本**|
|**HEAPSIZE**|**非共用**|**WINDOWAPI**|
|**匯入**|**NOTWINDOWCOMPAT**<sup>1</sup>|**WINDOWCOMPAT**|
|**非純虛擬**<sup>1</sup>|**物件**|**WINDOWS**|
|**包含**<sup>2</sup>|**舊**<sup>1</sup>||

<sup>1</sup>連結器會遇到這個詞彙時，會發出警告 （「 忽略 」）。 不過，這個字仍會被保留。

<sup>2</sup>連結器會忽略這個字，但不會發出警告。

## <a name="see-also"></a>另請參閱

- [設定連結器選項](../../build/reference/setting-linker-options.md)
- [連結器選項](../../build/reference/linker-options.md)