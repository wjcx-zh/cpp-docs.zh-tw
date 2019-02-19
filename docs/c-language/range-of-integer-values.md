---
title: 整數值的範圍
ms.date: 11/04/2016
ms.assetid: 0e9c6161-8f3f-4bfb-9fcc-a6c8dc97d702
ms.openlocfilehash: e34e700df203004388cd912089711b5849e00fd7
ms.sourcegitcommit: f4be868c0d1d78e550fba105d4d3c993743a1f4b
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/12/2019
ms.locfileid: "56152517"
---
# <a name="range-of-integer-values"></a>整數值的範圍

**ANSI 3.1.2.5**：各種整數類型值的表示和設定

整數包含 32 個位元 (四個位元組)。 帶正負號的整數以二補數格式表示。 最大有效位數位元存放正負號：1 代表負數，0 代表正數與零。 其值如下所列：

|類型|最小和最大值|
|----------|-------------------------|
|**unsigned short**|0 到 65535|
|`signed short`|-32768 到 32767|
|`unsigned long`|0 到 4294967295|
|**signed long**|-2147483648 到 2147483647|

## <a name="see-also"></a>另請參閱

[整數](../c-language/integers.md)
