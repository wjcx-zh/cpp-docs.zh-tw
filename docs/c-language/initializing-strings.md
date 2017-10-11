---
title: "初始化字串 | Microsoft Docs"
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
- character arrays, initializing
- strings [C++], initializing
- initializing arrays, strings
ms.assetid: 0ab8079d-d0d3-48f9-afd1-36a7bb439b29
caps.latest.revision: 9
author: mikeblome
ms.author: mblome
manager: ghogen
ms.translationtype: HT
ms.sourcegitcommit: 16d1bf59dfd4b3ef5f037aed9c0f6febfdf1a2e8
ms.openlocfilehash: 830e959e8cd9e57745d08da3d4184fbe11a5bb6a
ms.contentlocale: zh-tw
ms.lasthandoff: 10/09/2017

---
# <a name="initializing-strings"></a>初始化字串
您可以使用字串常值 (或寬字串常值) 初始化字元 (或寬字元) 陣列。 例如：  
  
```  
char code[ ] = "abc";  
```  
  
 將 `code` 初始化為四元素的字元陣列。 第四個元素為 Null 字元，用於終止所有字串常值。  
  
 識別項清單只能包含將初始化的識別項數目。 如果您指定的陣列大小比字串還短，則會忽略額外的字元。 例如，下列宣告會將 `code` 初始化為三元素字元陣列：  
  
```  
char code[3] = "abcd";  
```  
  
 只有初始設定式的前三個字元會指派給 `code`。 字元 `d` 和字串結尾的 Null 字元會遭捨棄。 請注意，這會建立一個未結束的字串 (也就是說，一個沒有以 0 值標記結尾字串)，並產生一個表示此情況的診斷訊息。  
  
 這個宣告  
  
```  
char s[] = "abc", t[3] = "abc";  
```  
  
 等同於  
  
```  
char s[]  = {'a', 'b', 'c', '\0'},   
     t[3] = {'a', 'b', 'c' };  
```  
  
 如果字串比指定的陣列大小短，會將陣列的剩餘元素初始化為 0。  
  
 **Microsoft 特定的**  
  
 在 Microsoft C 中，字串常值的長度最多可達 2048 個位元組。  
  
 **END Microsoft 特定的**  
  
## <a name="see-also"></a>另請參閱  
 [初始化](../c-language/initialization.md)
