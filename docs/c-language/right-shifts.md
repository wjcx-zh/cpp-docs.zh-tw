---
title: 右移位
ms.date: 11/04/2016
ms.assetid: c878e97d-ea3c-4c6b-90a8-b1b24b2d5b19
ms.openlocfilehash: 4b83aa231e6e7904fe5682b32a861ffe301b9747
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87199408"
---
# <a name="right-shifts"></a>右移位

負值帶正負號的整數類資料類型向右移位的結果

將負值向右移位會產生絕對值的一半 (無條件捨去)。 例如， **`signed short`** 值為-253 （十六進位0xFF03，二進位 11111111 00000011）右移一個位會產生-127 （十六進位0xFF81，二進位 11111111 10000001）。 正 253 向右移位會產生 +126。

向右移位會保留帶正負號之整數類資料類型的正負號位元。 當帶正負號的整數向右移位時，最高有效位元會保持原位。 例如，如果0xF0000000 為帶正負號的 **`int`** ，右移會產生0xF8000000。 將負 **`int`** 向右32次移位會產生0xffffffff。

當不帶正負號的整數向右移位時，會清除最高有效位元。 例如，如果 0xF000 不帶正負號，結果是 0x7800。 右移 **`unsigned`** 或正面的 **`int`** 32 次會產生0x00000000。

## <a name="see-also"></a>另請參閱

[陣列](../c-language/integers.md)
