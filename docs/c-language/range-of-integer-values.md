---
title: 整數值的範圍
ms.date: 11/04/2016
ms.assetid: 0e9c6161-8f3f-4bfb-9fcc-a6c8dc97d702
ms.openlocfilehash: e34e700df203004388cd912089711b5849e00fd7
ms.sourcegitcommit: c6f8e6c2daec40ff4effd8ca99a7014a3b41ef33
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/24/2019
ms.locfileid: "64343116"
---
# <a name="range-of-integer-values"></a>整數值的範圍

**ANSI 3.1.2.5**：各種整數類型值的表示和設定

整數包含 32 個位元 (四個位元組)。 帶正負號的整數以二補數格式表示。 最高有效位元會保存此正負號：1 為負數，0 為正數及零。 其值如下所列：

|類型|最小和最大值|
|----------|-------------------------|
|**unsigned short**|0 到 65535|
|`signed short`|-32768 到 32767|
|`unsigned long`|0 到 4294967295|
|**signed long**|-2147483648 到 2147483647|

## <a name="see-also"></a>請參閱

[整數](../c-language/integers.md)
