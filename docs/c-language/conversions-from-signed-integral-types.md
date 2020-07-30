---
title: 從帶正負號整數型別的轉換
ms.date: 10/02/2019
helpviewer_keywords:
- integral conversions, from signed
- integers, converting
- conversions [C++], integral
- data type conversion [C++], signed and unsigned integers
- type conversion [C++], signed and unsigned integers
ms.assetid: 5eea32f8-8b14-413d-acac-c063b3d118d7
ms.openlocfilehash: d41d2fd205a87f9f2be2179ffd8e38256a96e4f7
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87226473"
---
# <a name="conversions-from-signed-integral-types"></a>從帶正負號整數型別的轉換

當帶正負號的整數轉換成整數或浮點類型時，如果原始值是以結果類型表示，則此值不會變更。

當帶正負號的整數轉換成大小較大的整數時，此值會是「簽署擴充」。 轉換成大小較小的整數時，會截斷高序位位。 結果會使用結果型別來解讀，如下列範例所示：

```C
int i = -3;
unsigned short u;

u = i;
printf_s( "%hu\n", u );  // Prints 65533
```

將帶正負號的整數轉換成浮點類型時，如果原始值無法完全在結果類型中顯示，則結果會是下一個較高或較低的可顯示值。

如需整數和浮點類型大小的詳細資訊，請參閱[基本類型的儲存區](../c-language/storage-of-basic-types.md)。

下表摘要說明從帶正負號整數類資料類型進行轉換。 它假設 **`char`** 類型預設為帶正負號。 如果您使用編譯時間選項，將類型的預設值變更為不帶正負號，則會套用 **`char`** 類型[之不帶正負號整數類型資料表轉換](../c-language/conversions-from-unsigned-integral-types.md)中所指定的轉換 **`unsigned char`** ，而不是此資料表中的轉換。

**Microsoft 特定的**

在 Microsoft 編譯器中， **`int`** 和 **`long`** 是不同但對等的類型。 轉換 **`int`** 值的方式與的轉換相同 **`long`** 。

**結束 Microsoft 專有**

## <a name="table-of-conversions-from-signed-integral-types"></a>從帶正負號的整數類資料類型轉換的資料表

|寄件者|收件者|方法|
|----------|--------|------------|
|**`char`**<sup>sha-1</sup>|**`short`**|正負號擴充|
|**`char`**|**`long`**|正負號擴充|
|**`char`**|**`long long`**|正負號擴充|
|**`char`**|**`unsigned char`**|保留模式，高序位位元會遺失，做為正負號位元使用|
|**`char`**|**`unsigned short`**|正負號-延伸至， **`short`** 轉換 **`short`** 成**`unsigned short`**|
|**`char`**|**`unsigned long`**|正負號-延伸至， **`long`** 轉換 **`long`** 成**`unsigned long`**|
|**`char`**|**`unsigned long long`**|正負號-延伸至， **`long long`** 轉換 **`long long`** 成**`unsigned long long`**|
|**`char`**|**`float`**|正負號-延伸至， **`long`** 轉換 **`long`** 成**`float`**|
|**`char`**|**`double`**|正負號-延伸至， **`long`** 轉換 **`long`** 成**`double`**|
|**`char`**|**`long double`**|正負號-延伸至， **`long`** 轉換 **`long`** 成**`double`**|
|**`short`**|**`char`**|保留低序位位元組|
|**`short`**|**`long`**|正負號擴充|
|**`short`**|**`long long`**|正負號擴充|
|**`short`**|**`unsigned char`**|保留低序位位元組|
|**`short`**|**`unsigned short`**|保留位元模式，高序位位元會遺失，做為正負號位元使用|
|**`short`**|**`unsigned long`**|正負號-延伸至， **`long`** 轉換 **`long`** 成**`unsigned long`**|
|**`short`**|**`unsigned long long`**|正負號-延伸至， **`long long`** 轉換 **`long long`** 成**`unsigned long long`**|
|**`short`**|**`float`**|正負號-延伸至， **`long`** 轉換 **`long`** 成**`float`**|
|**`short`**|**`double`**|正負號-延伸至， **`long`** 轉換 **`long`** 成**`double`**|
|**`short`**|**`long double`**|正負號-延伸至， **`long`** 轉換 **`long`** 成**`double`**|
|**`long`**|**`char`**|保留低序位位元組|
|**`long`**|**`short`**|保留低序位字組|
|**`long`**|**`long long`**|正負號擴充|
|**`long`**|**`unsigned char`**|保留低序位位元組|
|**`long`**|**`unsigned short`**|保留低序位字組|
|**`long`**|**`unsigned long`**|保留位元模式，高序位位元會遺失，做為正負號位元使用|
|**`long`**|**`unsigned long long`**|正負號-延伸至， **`long long`** 轉換 **`long long`** 成**`unsigned long long`**|
|**`long`**|**`float`**|表示為 **`float`** 。 如果 **`long`** 無法完全表示，則會遺失一些精確度。|
|**`long`**|**`double`**|表示為 **`double`** 。 如果 **`long`** 無法完全表示為，則 **`double`** 會遺失一些精確度。|
|**`long`**|**`long double`**|表示為 **`double`** 。 如果 **`long`** 無法完全表示為，則 **`double`** 會遺失一些精確度。|
|**`long long`**|**`char`**|保留低序位位元組|
|**`long long`**|**`short`**|保留低序位字組|
|**`long long`**|**`long`**|保留低序位 dword|
|**`long long`**|**`unsigned char`**|保留低序位位元組|
|**`long long`**|**`unsigned short`**|保留低序位字組|
|**`long long`**|**`unsigned long`**|保留低序位 dword|
|**`long long`**|**`unsigned long long`**|保留位元模式，高序位位元會遺失，做為正負號位元使用|
|**`long long`**|**`float`**|表示為 **`float`** 。 如果 **`long long`** 無法完全表示，則會遺失一些精確度。|
|**`long long`**|**`double`**|表示為 **`double`** 。 如果 **`long long`** 無法完全表示為，則 **`double`** 會遺失一些精確度。|
|**`long long`**|**`long double`**|表示為 **`double`** 。 如果 **`long long`** 無法完全表示為，則 **`double`** 會遺失一些精確度。|

<sup>1</sup>所有 **`char`** 專案都會假設 **`char`** 類型預設為已簽署。

## <a name="see-also"></a>另請參閱

[指派轉換](../c-language/assignment-conversions.md)
