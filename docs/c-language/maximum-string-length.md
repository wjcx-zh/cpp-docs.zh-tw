---
title: "字串長度上限 | Microsoft Docs"
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
- lengths, strings
- string length, maximum
- maximum string length
- strings [C++], length
ms.assetid: 99a80e4a-6212-47b7-a6bd-bdf99bd44928
caps.latest.revision: 8
author: mikeblome
ms.author: mblome
manager: ghogen
ms.translationtype: HT
ms.sourcegitcommit: 16d1bf59dfd4b3ef5f037aed9c0f6febfdf1a2e8
ms.openlocfilehash: f3defc694e2ac3f859c160a2e34aecefd42627c4
ms.contentlocale: zh-tw
ms.lasthandoff: 10/09/2017

---
# <a name="maximum-string-length"></a>字串長度上限
**Microsoft 特定的**  
  
 ANSI 相容性要求編譯器在串連後，必須在字串常值中接受最多 509 個字元。 Microsoft C 中允許的字串常值長度上限約為 2,048 個位元組。 不過，如果字串常值中包含以雙引號括住的部分，則前置處理器會將這些部分加入至單一字串，並且針對串連的每一行增加額外的位元組至位元組總數。  
  
 例如，假設字串包含 40 行，每一行有 50 個字元 (共 2,000 個字元)，另外還有一行包含 7 個字元，且每一行都以雙引號括住。 這樣相加後為 2,007 個位元組，再加上一個用於結束的 null 字元的位元組，總共是 2,008 個位元組。 在串連時，會針對前 40 行各加入一個額外的字元。 這樣總數就會是 2,048 個位元組。 不過，請注意，如果使用行接續符號 (\\) 取代雙引號，則前置處理器不會為每行增加額外的字元。  
  
 雖然引號括住的個別字串長度不可超過 2048 個位元組，但是藉由串連字串，就可以建構大約 65535 個位元組的字串常值。  
  
 **END Microsoft 特定的**  
  
## <a name="see-also"></a>另請參閱  
 [C 字串常值](../c-language/c-string-literals.md)
