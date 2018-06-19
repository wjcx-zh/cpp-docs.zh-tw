---
title: 從浮點類型的轉換 | Microsoft Docs
ms.custom: ''
ms.date: 01/29/2018
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- converting floating point
- floating-point conversion
ms.assetid: 96804c8e-fa3b-4742-9006-0082ed9e57f2
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: ce86a9ceffaa5d9dacfe56e6b89b677b3abb1517
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
ms.locfileid: "32392480"
---
# <a name="conversions-from-floating-point-types"></a>從浮點數類型的轉換

轉換成 **double** 或 **long double** 的 **float** 值，或轉換成 **long double** 的 **double**，其值不變。 轉換成 **float** 值的 **double** 值會盡可能確切表示。 如果無法正確表示值，則精確度可能會喪失。 如果結果超出範圍，則行為會是未定義。 如需浮點類型的範圍，請參閱[浮點常數的限制](../c-language/limits-on-floating-point-constants.md)。

浮點值轉換成整數值的過程，是先轉換成 **long**，然後從 **long** 值轉換成特定整數值。 浮點值的小數部分會在轉換成 **long** 的過程中捨棄。 如果結果仍然太大而無法適用 **long**，則轉換的結果會是未定義。

**Microsoft 特定的**

將 **double** 或 **long double** 浮點數轉換成較小的浮點數時，浮點數變數的值會在發生反向溢位時從小數點以下截斷。 溢位會造成執行階段錯誤。 請注意，Microsoft C 編譯器會將 **long double** 對應至 **double** 類型。

**結束 Microsoft 特定的**

下表摘要說明從浮點類型進行轉換。

## <a name="conversions-from-floating-point-types"></a>從浮點數類型的轉換

|從|以|方法|
|----------|--------|------------|
|**float**|**char**|轉換成 **long**；將 **long** 轉換成 **char**|
|**float**|**short**|轉換為 **long**，將 **long** 轉換為 **short**|
|**float**|**long**|於小數點截斷。 如果結果太大而無法以 **long** 表示，則結果會是未定義。|
|**float**|**unsigned short**|轉換為 **long**，將 **long** 轉換為 **unsigned short**|
|**float**|**unsigned long**|轉換成 **long**；將 **long** 轉換成 **unsigned long**|
|**float**|**double**|變更內部表示|
|**float**|**long double**|變更內部表示|
|**double**|**char**|轉換成 **float**；將 **float** 轉換成 **char**|
|**double**|**short**|轉換為 **float**，將 **float** 轉換為 **short**|
|**double**|**long**|於小數點截斷。 如果結果太大而無法以 **long** 表示，則結果會是未定義。|
|**double**|**unsigned short**|轉換為 **long**，將 **long** 轉換為 **unsigned short**|
|**double**|**unsigned long**|轉換成 **long**；將 **long** 轉換成 **unsigned long**|
|**double**|**float**|表示為 **float**。 如果 **double** 值無法以 **float** 確切表示，則會發生精確度喪失。 如果值太大而無法以 **float** 表示，則結果會是未定義。|
|**long double**|**char**|轉換成 **float**；將 **float** 轉換成 **char**|
|**long double**|**short**|轉換為 **float**，將 **float** 轉換為 **short**|
|**long double**|**long**|於小數點截斷。 如果結果太大而無法以 **long** 表示，則結果會是未定義。|
|**long double**|**unsigned short**|轉換為 **long**，將 **long** 轉換為 **unsigned short**|
|**long double**|**unsigned long**|轉換成 **long**；將 **long** 轉換成 **unsigned long**|
|**long double**|**float**|表示為 **float**。 如果 **double** 值無法以 **float** 確切表示，則會發生精確度喪失。 如果值太大而無法以 **float** 表示，則結果會是未定義。|
|**long double**|**double**|**long double** 值會被視為 **double**。|

如果轉換的值大於 **long** 的最大正數值，則從 **float**、**double** 或 **long double** 值轉換成 **unsigned long** 就會不精確。

## <a name="see-also"></a>另請參閱

[指派轉換](../c-language/assignment-conversions.md)  
