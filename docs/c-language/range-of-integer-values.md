---
title: 整數值的範圍
ms.date: 11/04/2016
ms.assetid: 0e9c6161-8f3f-4bfb-9fcc-a6c8dc97d702
ms.openlocfilehash: 3a7bff54e3048c7eb52d153aff5aa8ecf24a0516
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87227786"
---
# <a name="range-of-integer-values"></a>整數值的範圍

**ANSI 3.1.2.5**：各種整數類型值的表示和設定

整數包含 32 個位元 (四個位元組)。 帶正負號的整數以二補數格式表示。 最高有效位元會保存此正負號：1 為負數，0 為正數及零。 其值如下所列：

|類型|最小和最大值|
|----------|-------------------------|
|**`unsigned short`**|0 到 65535|
|**`signed short`**|-32768 到 32767|
|**`unsigned long`**|0 到 4294967295|
|**`signed long`**|-2147483648 到 2147483647|

## <a name="see-also"></a>另請參閱

[陣列](../c-language/integers.md)
