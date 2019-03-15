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
ms.openlocfilehash: 7d51f599dfb81dfa860e1bdba86c4372e80379fb
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2019
ms.locfileid: "57822440"
---
# <a name="reserved-words"></a>保留的字

下列為保留字，連結器。 這些名稱可用來當做引數[模組定義陳述式](module-definition-dot-def-files.md)才以雙引號括住的名稱 ("")。

||||
|-|-|-|
|**APPLOADER**<sup>1</sup>|**INITINSTANCE**<sup>2</sup>|**預先載入**|
|**BASE**|**IOPL**|**PRIVATE**|
|**CODE**|**LIBRARY**<sup>1</sup>|**PROTMODE**<sup>2</sup>|
|**符合**|**LOADONCALL**<sup>1</sup>|**純**<sup>1</sup>|
|**DATA**|**LONGNAMES**<sup>2</sup>|**READONLY**|
|**描述**|**可移動**<sup>1</sup>|**READWRITE**|
|**DEV386**|**MOVEABLE**<sup>1</sup>|**REALMODE**<sup>1</sup>|
|**可捨棄**|**多個**|**RESIDENT**|
|**DYNAMIC**|**NAME**|**RESIDENTNAME**<sup>1</sup>|
|**EXECUTE-ONLY**|**NEWFILES**<sup>2</sup>|**區段**|
|**EXECUTEONLY**|**NODATA**<sup>1</sup>|**SEGMENTS**|
|**EXECUTEREAD**|**NOIOPL**<sup>1</sup>|**SHARED**|
|**EXETYPE**|**NONAME**|**單一**|
|**EXPORTS**|**不合格**<sup>1</sup>|**STACKSIZE**|
|**固定**<sup>1</sup>|**NONDISCARDABLE**|**STUB**|
|**函式**<sup>2</sup>|**NONE**|**VERSION**|
|**HEAPSIZE**|**非共用**|**WINDOWAPI**|
|**匯入**|**NOTWINDOWCOMPAT**<sup>1</sup>|**WINDOWCOMPAT**|
|**IMPURE**<sup>1</sup>|**OBJECTS**|**WINDOWS**|
|**包含**<sup>2</sup>|**OLD**<sup>1</sup>||

<sup>1</sup>連結器會遇到這個詞彙時，會發出警告 （「 忽略 」）。 不過，這個字仍會被保留。

<sup>2</sup>連結器會忽略這個字，但不會發出警告。

## <a name="see-also"></a>另請參閱

- [MSVC 連結器參考](linking.md)
- [MSVC 連結器選項](linker-options.md)