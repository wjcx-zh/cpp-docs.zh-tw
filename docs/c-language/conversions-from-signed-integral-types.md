---
title: "從帶正負號整數類型的轉換 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- integral conversions, from signed
- integers, converting
- conversions [C++], integral
- data type conversion [C++], signed and unsigned integers
- type conversion [C++], signed and unsigned integers
ms.assetid: 5eea32f8-8b14-413d-acac-c063b3d118d7
caps.latest.revision: 9
author: mikeblome
ms.author: mblome
manager: ghogen
ms.translationtype: HT
ms.sourcegitcommit: 16d1bf59dfd4b3ef5f037aed9c0f6febfdf1a2e8
ms.openlocfilehash: ccda8d6fa2573245f34a38f327395955bf92fdc2
ms.contentlocale: zh-tw
ms.lasthandoff: 10/09/2017

---
# <a name="conversions-from-signed-integral-types"></a>從帶正負號整數類型的轉換
將帶正負號的整數轉換為大小相等或大小較大的不帶正負號整數時，若帶正負號整數值不為負值，則其值不變。 轉換是透過帶正負號整數的帶正負號擴充方式所進行。 若將帶正負號整數轉換為較短的帶正負號整數，則會截斷高序位的位元。 其結果會解譯為不帶正負號的值，如此範例中所示。  
  
```  
int i = -3;  
unsigned short u;  
  
u = i;   
printf_s( "%hu\n", u );  // Prints 65533  
  
```  
  
 將帶正負號的整數轉換成浮動值時不會遺失資訊，不過，將 **long int** 或 **unsigned long int** 值轉換為 **float** 值時，可能會遺失一些精確度。  
  
 下表摘要說明從帶正負號整數類資料類型進行轉換。 此表假設 **char** 類型預設為帶正負號值。 如果您使用編譯時間選項來將 **char** 類型的預設值變更為不帶正負號類型，則在[從不帶正負號的整數類型轉換](../c-language/conversions-from-unsigned-integral-types.md)表中，針對 **unsigned char** 類型所套用的轉換會改為下表 (從帶正負號的整數類型轉換) 中所述的轉換。  
  
### <a name="conversions-from-signed-integral-types"></a>從帶正負號整數類型的轉換  
  
|從|以|方法|  
|----------|--------|------------|  
|**char**1|**short**|正負號擴充|  
|**char**|**long**|正負號擴充|  
|**char**|**unsigned char**|保留模式，高序位位元會遺失，做為正負號位元使用|  
|**char**|**unsigned short**|對 **short** 進行正負號擴充，將 **short** 轉換為 **unsigned short**|  
|**char**|**unsigned long**|對 **long** 進行正負號擴充，將 **long** 轉換為 **unsigned long**|  
|**char**|**float**|對 **long** 進行正負號擴充，將 **long** 轉換為 **float**|  
|**char**|**double**|對 **long** 進行正負號擴充，將 **long** 轉換為 **double**|  
|**char**|**long double**|對 **long** 進行正負號擴充，將 **long** 轉換為 **double**|  
|**short**|**char**|保留低序位位元組|  
|**short**|**long**|正負號擴充|  
|**short**|**unsigned char**|保留低序位位元組|  
|**short**|**unsigned short**|保留位元模式，高序位位元會遺失，做為正負號位元使用|  
|**short**|**unsigned long**|對 **long** 進行正負號擴充，將 **long** 轉換為 **unsigned long**|  
|**short**|**float**|對 **long** 進行正負號擴充，將 **long** 轉換為 **float**|  
|**short**|**double**|對 **long** 進行正負號擴充，將 **long** 轉換為 **double**|  
|**short**|**long double**|對 **long** 進行正負號擴充，將 **long** 轉換為 **double**|  
|**long**|**char**|保留低序位位元組|  
|**long**|**short**|保留低序位字組|  
|**long**|**unsigned char**|保留低序位位元組|  
|**long**|**unsigned short**|保留低序位字組|  
|**long**|**unsigned long**|保留位元模式，高序位位元會遺失，做為正負號位元使用|  
|**long**|**float**|表示為 **float**。 如果無法正確地表示 **long**，則會遺失一些精確度。|  
|**long**|**double**|表示為 **double**。 如果無法將 **long** 表示為與 **double** 完全相同，則會遺失一些精確度。|  
|**long**|**long double**|表示為 **double**。 如果無法將 **long** 表示為與 **double** 完全相同，則會遺失一些精確度。|  
  
 1. 所有 **char** 項目都假設 **char** 類型預設為帶正負號值。  
  
 **Microsoft 特定的**  
  
 對於 Microsoft 32 位元 C 編譯器，整數相當於 **long**。 **int** 值進行的轉換與 **long** 的轉換相同。  
  
 **END Microsoft 特定的**  
  
## <a name="see-also"></a>另請參閱  
 [指派轉換](../c-language/assignment-conversions.md)
