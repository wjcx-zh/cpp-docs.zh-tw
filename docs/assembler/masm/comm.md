---
title: COMM | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- COMM
dev_langs:
- C++
helpviewer_keywords:
- COMM directive
ms.assetid: a23548c4-ad04-41fa-91da-945f228de742
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 6258a584d39f598b32c43affc0ef2569b77b2047
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/14/2018
---
# <a name="comm"></a>COMM
使用中指定的屬性建立微乎其微變數`definition`。  
  
## <a name="syntax"></a>語法  
  
```  
  
COMM definition [[, definition]] ...  
```  
  
## <a name="remarks"></a>備註  
 每個`definition`具有下列格式：  
  
 [[*langtype*]] [[**NEAR** &#124;**遠**]]*標籤***:**`type`[[**:***計數*]]  
  
 *標籤*是變數的名稱。 `type`可以是任何類型規範 ([位元組](../../assembler/masm/byte-masm.md)， [WORD](../../assembler/masm/word.md)等等) 或指定的位元組數目的整數。 *計數*指定數目的資料物件 （一個是預設值）。  
  
## <a name="see-also"></a>請參閱  
 [指示詞參考](../../assembler/masm/directives-reference.md)