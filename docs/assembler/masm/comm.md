---
title: "COMM |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: COMM
dev_langs: C++
helpviewer_keywords: COMM directive
ms.assetid: a23548c4-ad04-41fa-91da-945f228de742
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: b8feb74f1da11fb6c4205ec1d8381f78789f684f
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/24/2017
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
  
## <a name="see-also"></a>另請參閱  
 [指示詞參考](../../assembler/masm/directives-reference.md)