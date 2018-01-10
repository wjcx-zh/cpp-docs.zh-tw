---
title: "字串常值的儲存 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: string literals, storage
ms.assetid: ba5e4d2c-d456-44b3-a8ca-354af547ac50
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: bc3314e569a7229e3cf316b46e1a8df4c9bb722e
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="storage-of-string-literals"></a>字串常值的儲存
常值字串的字元是依順序儲存在連續記憶體位置中。 字串常值內的逸出序列 (例如 **\\\\** 或 **\\"**) 會算是單一字元。 null 字元 (以 **\0** 逸出序列表示) 會自動附加至每個字串常值，而且做為字串常值結尾的標記。 (這會發生在[轉譯階段](../preprocessor/phases-of-translation.md) 7)。請注意，編譯器可能不會將兩個相同的字串儲存在兩個不同的位址。 [/GF](../build/reference/gf-eliminate-duplicate-strings.md) 會強制編譯器將一份相同的字串放入可執行檔中。  
  
## <a name="remarks"></a>備註  
 **Microsoft 特定的**  
  
 字串具有靜態儲存期。 如需儲存期的詳細資訊，請參閱[儲存類別](../c-language/c-storage-classes.md)。  
  
 **結束 Microsoft 特定的**  
  
## <a name="see-also"></a>請參閱  
 [C 字串常值](../c-language/c-string-literals.md)