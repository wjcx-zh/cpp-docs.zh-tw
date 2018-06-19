---
title: __based 文法 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- based addressing
ms.assetid: a68ff750-c7fa-4c0c-8d5f-2df76e4686c5
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 20e1c14cd7add01f8583c24541987b2980da794a
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
ms.locfileid: "32409533"
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
 *type-name*  
  
**結束 Microsoft 特定的**  
  
## <a name="see-also"></a>另請參閱  
 [Based 指標](../cpp/based-pointers-cpp.md)