---
title: "整數降級 | Microsoft Docs"
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
- demoting integers
ms.assetid: 51fb3654-60b0-4de7-80eb-bd910086c18a
caps.latest.revision: 6
author: mikeblome
ms.author: mblome
manager: ghogen
ms.translationtype: HT
ms.sourcegitcommit: 16d1bf59dfd4b3ef5f037aed9c0f6febfdf1a2e8
ms.openlocfilehash: e09a81ca21f6e00777322178dcdf1c09ef22dd5b
ms.contentlocale: zh-tw
ms.lasthandoff: 10/09/2017

---
# <a name="demotion-of-integers"></a>整數降級
**ANSI 3.2.1.2**：將整數轉換為較短的帶正負號整數的結果，或將不帶正負號的整數轉換為長度相等的帶正負號整數的結果 (如果值無法表示的話)。  
  
 當 **long** 整數轉換為 **short**，或者 **short** 轉換為 `char` 時，會保留最小顯著性位元組。  
  
 例如，在下列程式碼中  
  
```  
short x = (short)0x12345678L;  
```  
  
 指派值 0x5678 給 `x`，以及下列程式碼  
  
```  
char y = (char)0x1234;  
```  
  
 指派值 0x34 給 `y`。  
  
 當帶正負號的變數轉換為不帶正負號的變數 (反之亦然) 時，其位元模式會保持不變。 例如，將 -2 (0xFE) 轉換為不帶正負號的值會產生 254 (亦為 0xFE)。  
  
## <a name="see-also"></a>另請參閱  
 [整數](../c-language/integers.md)
