---
title: 保留字
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
ms.openlocfilehash: 16caacb77e052eebc8e2cd101990ee373535bd6e
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80171147"
---
# <a name="reserved-words"></a>保留字

連結器會保留下列文字。 只有當名稱以雙引號（""）括住時，這些名稱才能當做[模組定義語句](module-definition-dot-def-files.md)中的引數使用。

||||
|-|-|-|
|**APPLOADER**<sup>1</sup>|**INITINSTANCE**<sup>2</sup>|**預先載入**|
|**群體**|**IOPL**|**私人**|
|**錯誤碼**|連結**庫**<sup>1</sup>|**PROTMODE**<sup>2</sup>|
|**達標**|**LOADONCALL**<sup>1</sup>|**純粹**<sup>1</sup>|
|**DATA**|**LONGNAMES**<sup>2</sup>|**唯讀**|
|**DESCRIPTION**|**可移動**<sup>1</sup>|**READWRITE**|
|**DEV386**|**可移動**<sup>1</sup>|**REALMODE**<sup>1</sup>|
|**可捨棄**|**多個**|**公民**|
|**效果**|**名稱**|**RESIDENTNAME**<sup>1</sup>|
|**僅執行**|**Newfiles.format.ps1xml 檔案**<sup>2</sup>|**各節**|
|**EXECUTEONLY**|**NODATA**<sup>1</sup>|**部門**|
|**EXECUTEREAD**|**NOIOPL**<sup>1</sup>|**共用**|
|**EXETYPE**|**NONAME**|**單機**|
|**EXPORTS**|**NONCONFORMING**不合格<sup>1</sup>|**STACKSIZE**|
|已**修正**<sup>1</sup>|**NONDISCARDABLE**|**STUB**|
|**函數**<sup>2</sup>|**NONE**|**VERSION**|
|**HEAPSIZE**|**非共用**|**WINDOWAPI**|
|**進口**|**NOTWINDOWCOMPAT**<sup>1</sup>|**WINDOWCOMPAT**|
|**非純虛擬**<sup>1</sup>|**物件**|**時段**|
|**包含**<sup>2</sup>|**舊**<sup>1</sup>||

<sup>1</sup>當連結器遇到此字詞時，會發出警告（「已忽略」）。 不過，這個字仍然是保留的。

<sup>2</sup>連結器會忽略這個字，但不發出警告。

## <a name="see-also"></a>另請參閱

- [MSVC 連結器參考](linking.md)
- [MSVC 連結器選項](linker-options.md)
