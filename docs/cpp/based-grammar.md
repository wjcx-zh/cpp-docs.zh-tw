---
title: "__based 文法 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- based addressing
ms.assetid: a68ff750-c7fa-4c0c-8d5f-2df76e4686c5
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 6a2cb2929fa595ad13746ea929217f41272a8189
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="based-grammar"></a>__based 文法
## <a name="microsoft-specific"></a>Microsoft 特定的  
 基底位址在您需要精確控制配置物件的區段時很實用 (靜態和動態架構資料)。  
  
 在 32 位元和 64 位元編譯中可接受的唯一基底位址形式是「以指標為基礎」，這種形式定義的類型會包含相對於 32 位元或 64 位元基底或以 `void` 為基礎的 32 位元或 64 位元位移。  
  
## <a name="grammar"></a>文法  
 *基礎範圍修飾詞*:  
 **__based (***基底運算式***)**   
  
 *基底運算式*:  
 *based-variablebased-abstract-declaratorsegment-namesegment-cast*  
  
 *根據變數*:  
 *identifier*  
  
 *基礎抽象宣告子*:  
 *抽象宣告子*  
  
 *基底型別*:  
 *型別名稱*  
  
**結束 Microsoft 特定的**  
  
## <a name="see-also"></a>請參閱  
 [Based 的指標](../cpp/based-pointers-cpp.md)