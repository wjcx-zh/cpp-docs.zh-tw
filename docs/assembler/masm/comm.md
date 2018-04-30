---
title: COMM |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-masm
ms.topic: reference
f1_keywords:
- COMM
dev_langs:
- C++
helpviewer_keywords:
- COMM directive
ms.assetid: a23548c4-ad04-41fa-91da-945f228de742
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 111dac47089fea13febe787e5b73557b287beea8
ms.sourcegitcommit: dbca5fdd47249727df7dca77de5b20da57d0f544
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/28/2018
---
# <a name="comm"></a>COMM
使用中指定的屬性建立微乎其微變數`definition`。  
  
## <a name="syntax"></a>語法  
  
```  
  
COMM definition [[, definition]] ...  
```  
  
## <a name="remarks"></a>備註  
 每個`definition`具有下列格式：  
  
 [[*langtype*]] [[**NEAR** &#124; **遠**]]*標籤 ***:**`type`[[**:*** 計數*]]  
  
 *標籤*是變數的名稱。 `type`可以是任何類型規範 ([位元組](../../assembler/masm/byte-masm.md)， [WORD](../../assembler/masm/word.md)等等) 或指定的位元組數目的整數。 *計數*指定數目的資料物件 （一個是預設值）。  
  
## <a name="see-also"></a>另請參閱  
 [指示詞參考](../../assembler/masm/directives-reference.md)