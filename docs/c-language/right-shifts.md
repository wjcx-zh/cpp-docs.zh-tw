---
title: 右移位
ms.date: 11/04/2016
ms.assetid: c878e97d-ea3c-4c6b-90a8-b1b24b2d5b19
ms.openlocfilehash: f39c1f2f49f5a8a1f3bb5eb3f21736eedf32077e
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50518205"
---
# <a name="right-shifts"></a>右移位

負值帶正負號的整數類資料類型向右移位的結果

將負值向右移位會產生絕對值的一半 (無條件捨去)。 例如，-253 的帶正負號 `short` 值 (十六進位 0xFF03、二進位 11111111 00000011) 向右移位一個位元會產生 -127 (十六進位 0xFF81、二進位 11111111 10000001)。 正 253 向右移位會產生 +126。

向右移位會保留帶正負號之整數類資料類型的正負號位元。 當帶正負號的整數向右移位時，最高有效位元會保持原位。 例如，如果 0xF0000000 為帶正負號的 `int`，向右移位會產生 0xF8000000。 負 `int` 向右移位 32 次會產生 0xFFFFFFFF。

當不帶正負號的整數向右移位時，會清除最高有效位元。 例如，如果 0xF000 不帶正負號，結果是 0x7800。 `unsigned` 或正 `int` 向右移位 32 次會產生 0x00000000。

## <a name="see-also"></a>請參閱

[整數](../c-language/integers.md)