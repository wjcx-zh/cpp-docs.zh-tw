---
title: 從不帶正負號整數型別的轉換
ms.date: 10/02/2019
helpviewer_keywords:
- integers, converting
- type casts, involving integers
- data type conversion [C++], signed and unsigned integers
- type conversion [C++], signed and unsigned integers
- integral conversions, from unsigned
ms.assetid: 60fb7e10-bff9-4a13-8a48-e19f25a36a02
ms.openlocfilehash: 08b88b1343f56f8d79fc39c53505b26caecfe3c4
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87226460"
---
# <a name="conversions-from-unsigned-integral-types"></a>從不帶正負號整數型別的轉換

當不帶正負號的整數轉換成整數或浮點數型別時，如果原始值是以結果型別表示，此值就不會改變。

將不帶正負號的整數轉換為較大的整數時，此值為零擴充。 轉換成較小大小的整數時，會截斷高序位位。 結果會使用結果型別來解讀，如下列範例所示。

```C
unsigned k = 65533;
short j;

j = k;
printf_s( "%hd\n", j );   // Prints -3
```

將不帶正負號的整數轉換成浮點類型時，如果原始值無法精確表示在結果類型中，則結果會是下一個較高或較低的可顯示值。

如需整數和浮點類型大小的詳細資訊，請參閱[基本類型的儲存空間](../c-language/storage-of-basic-types.md)。

**Microsoft 特定的**

在 Microsoft 編譯器中， **`unsigned`** （或 **`unsigned int`** ）和 **`unsigned long`** 是不同但對等的類型。 轉換 **`unsigned int`** 值的方式與的轉換相同 **`unsigned long`** 。

**結束 Microsoft 專有**

下表摘要說明從不帶正負號整數類資料類型進行轉換。

## <a name="table-of-conversions-from-unsigned-integral-types"></a>不帶正負號整數類資料類型的轉換資料表

|寄件者|收件者|方法|
|----------|--------|------------|
|**`unsigned char`**|**`char`**|保留位元模式，高序位位元會變成正負號位元|
|**`unsigned char`**|**`short`**|零擴充|
|**`unsigned char`**|**`long`**|零擴充|
|**`unsigned char`**|**`long long`**|零擴充|
|**`unsigned char`**|**`unsigned short`**|零擴充|
|**`unsigned char`**|**`unsigned long`**|零擴充|
|**`unsigned char`**|**`unsigned long long`**|零擴充|
|**`unsigned char`**|**`float`**|轉換成 **`long`** ; 將轉換 **`long`** 成**`float`**|
|**`unsigned char`**|**`double`**|轉換成 **`long`** ; 將轉換 **`long`** 成**`double`**|
|**`unsigned char`**|**`long double`**|轉換成 **`long`** ; 將轉換 **`long`** 成**`double`**|
|**`unsigned short`**|**`char`**|保留低序位位元組|
|**`unsigned short`**|**`short`**|保留位元模式，高序位位元會變成正負號位元|
|**`unsigned short`**|**`long`**|零擴充|
|**`unsigned short`**|**`long long`**|零擴充|
|**`unsigned short`**|**`unsigned char`**|保留低序位位元組|
|**`unsigned short`**|**`unsigned long`**|零擴充|
|**`unsigned short`**|**`unsigned long long`**|零擴充|
|**`unsigned short`**|**`float`**|轉換成 **`long`** ; 將轉換 **`long`** 成**`float`**|
|**`unsigned short`**|**`double`**|轉換成 **`long`** ; 將轉換 **`long`** 成**`double`**|
|**`unsigned short`**|**`long double`**|轉換成 **`long`** ; 將轉換 **`long`** 成**`double`**|
|**`unsigned long`**|**`char`**|保留低序位位元組|
|**`unsigned long`**|**`short`**|保留低序位字組|
|**`unsigned long`**|**`long`**|保留位元模式，高序位位元會變成正負號位元|
|**`unsigned long`**|**`long long`**|零擴充|
|**`unsigned long`**|**`unsigned char`**|保留低序位位元組|
|**`unsigned long`**|**`unsigned short`**|保留低序位字組|
|**`unsigned long`**|**`unsigned long long`**|零擴充|
|**`unsigned long`**|**`float`**|轉換成 **`long`** ; 將轉換 **`long`** 成**`float`**|
|**`unsigned long`**|**`double`**|直接轉換成**`double`**|
|**`unsigned long`**|**`long double`**|轉換成 **`long`** ; 將轉換 **`long`** 成**`double`**|
|**`unsigned long long`**|**`char`**|保留低序位位元組|
|**`unsigned long long`**|**`short`**|保留低序位字組|
|**`unsigned long long`**|**`long`**|保留低序位 dword|
|**`unsigned long long`**|**`long long`**|保留位元模式，高序位位元會變成正負號位元|
|**`unsigned long long`**|**`unsigned char`**|保留低序位位元組|
|**`unsigned long long`**|**`unsigned short`**|保留低序位字組|
|**`unsigned long long`**|**`unsigned long`**|保留低序位 dword|
|**`unsigned long long`**|**`float`**|轉換成 **`long`** ; 將轉換 **`long`** 成**`float`**|
|**`unsigned long long`**|**`double`**|直接轉換成**`double`**|
|**`unsigned long long`**|**`long double`**|轉換成 **`long`** ; 將轉換 **`long`** 成**`double`**|

## <a name="see-also"></a>另請參閱

[指派轉換](../c-language/assignment-conversions.md)
