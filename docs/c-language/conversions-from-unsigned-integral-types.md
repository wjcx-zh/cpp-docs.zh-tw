---
title: "從不帶正負號整數類型的轉換 | Microsoft Docs"
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
- integers, converting
- type casts, involving integers
- data type conversion [C++], signed and unsigned integers
- type conversion [C++], signed and unsigned integers
- integral conversions, from unsigned
ms.assetid: 60fb7e10-bff9-4a13-8a48-e19f25a36a02
caps.latest.revision: 10
author: mikeblome
ms.author: mblome
manager: ghogen
ms.translationtype: Human Translation
ms.sourcegitcommit: d6eb43b2e77b11f4c85f6cf7e563fe743d2a7093
ms.openlocfilehash: 937d6cdeacda2abe2dd241e5a8e9463549567444
ms.contentlocale: zh-tw
ms.lasthandoff: 05/18/2017

---
# <a name="conversions-from-unsigned-integral-types"></a>從不帶正負號整數類型的轉換
不帶正負號的整數會藉由截斷高序位位元，轉換為較短的不帶正負號或帶正負號的整數，或是藉由零擴充轉換為較長的不帶正負號或帶正負號的整數 (請參閱[從不帶正負號整數類型的轉換](#_clang_table_4..3)表格)。  
  
 當值使用的是降級至大小較小的帶正負號整數，或者不帶正負號整數時，會將其轉換為對應的帶正負號整數，如果可以由新的類型表示，其值是不變的。 不過，如果設定了正負號位元，則其值會改變，如下列範例所述。  
  
```  
int j;  
unsigned short k = 65533;  
  
j = k;  
printf_s( "%hd\n", j );   // Prints -3  
```  
  
 如果無法表示其值，則結果是由實作定義。 如需 Microsoft C 編譯器處理整數降級的詳細資訊，請參閱[類型轉換](../c-language/type-cast-conversions.md)。 從整數進行轉換，或轉換整數的類型也會導致相同的行為。  
  
 不帶正負號的值會以保留其值的方法進行轉換，且無法直接在 C 中表示。唯一的例外是從 `unsigned long` 轉換為 **float**，此情況下最多只會失去低序位位元。 否則，會將值保存為帶正負號或不帶正負號的值。 當整數類資料類型的值轉換成浮動類型時，且其值無法顯示，則結果會是未定義。 (如需整數類資料和浮點類型範圍的相關資訊，請參閱[基本類型的儲存空間](../c-language/storage-of-basic-types.md))。  
  
 下表摘要說明從不帶正負號整數類資料類型進行轉換。  
  
### <a name="conversions-from-unsigned-integral-types"></a>從不帶正負號整數類型的轉換  
  
|從|以|方法|  
|----------|--------|------------|  
|`unsigned char`|`char`|保留位元模式，高序位位元會變成正負號位元|  
|`unsigned char`|**short**|零擴充|  
|`unsigned char`|**long**|零擴充|  
|`unsigned char`|**unsigned short**|零擴充|  
|`unsigned char`|`unsigned long`|零擴充|  
|`unsigned char`|**float**|轉換為 **long**，將 **long** 轉換為 **float**|  
|`unsigned char`|**double**|轉換為 **long**，將 **long** 轉換為 **double**|  
|`unsigned char`|`long double`|轉換為 **long**，將 **long** 轉換為 **double**|  
|**unsigned short**|`char`|保留低序位位元組|  
|**unsigned short**|**short**|保留位元模式，高序位位元會變成正負號位元|  
|**unsigned short**|**long**|零擴充|  
|**unsigned short**|`unsigned char`|保留低序位位元組|  
|**unsigned short**|`unsigned long`|零擴充|  
|**unsigned short**|**float**|轉換為 **long**，將 **long** 轉換為 **float**|  
|**unsigned short**|**double**|轉換為 **long**，將 **long** 轉換為 **double**|  
|**unsigned short**|`long double`|轉換為 **long**，將 **long** 轉換為 **double**|  
|`unsigned long`|`char`|保留低序位位元組|  
|`unsigned long`|**short**|保留低序位字組|  
|`unsigned long`|**long**|保留位元模式，高序位位元會變成正負號位元|  
|`unsigned long`|`unsigned char`|保留低序位位元組|  
|`unsigned long`|**unsigned short**|保留低序位字組|  
|`unsigned long`|**float**|轉換為 **long**，將 **long** 轉換為 **float**|  
|`unsigned long`|**double**|直接轉換為 **double**|  
|`unsigned long`|`long double`|轉換為 **long**，將 **long** 轉換為 **double**|  
  
 **Microsoft 特定的**  
  
 對於 Microsoft 32 位元 C 編譯器，`unsigned int` 類型相當於 `unsigned long` 類型。 `unsigned int` 值的轉換與 `unsigned long` 的轉換使用相同的方式進行。 如果要轉換的值大於最大的正數帶正負號 **long** 值，則從 `unsigned long` 值轉換為 **float** 會變得不精確。  
  
 **END Microsoft 特定的**  
  
## <a name="see-also"></a>另請參閱  
 [指派轉換](../c-language/assignment-conversions.md)
