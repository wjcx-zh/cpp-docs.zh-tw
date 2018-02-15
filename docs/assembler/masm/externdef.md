---
title: EXTERNDEF | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- EXTERNDEF
dev_langs:
- C++
helpviewer_keywords:
- EXTERNDEF directive
ms.assetid: 95a10de6-c345-4428-a2f2-90f7d411dc86
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: a463f4f74f380c6d927419eb498ccd868587ac6d
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/14/2018
---
# <a name="externdef"></a>EXTERNDEF
定義一或多個外部變數、 標籤或符號呼叫*名稱*其型別是`type`。  
  
## <a name="syntax"></a>語法  
  
```  
  
EXTERNDEF [[langtype]] name:type [[, [[langtype]] name:type]]...  
```  
  
## <a name="remarks"></a>備註  
 如果*名稱*定義在模組中，它會被視為[公用](../../assembler/masm/public-masm.md)。 如果*名稱*參考在模組中，它會被視為[EXTERN](../../assembler/masm/extern-masm.md)。 如果*名稱*是未參考，則會忽略它。 `type`可以[ABS](../../assembler/masm/operator-abs.md)，哪些匯入*名稱*為常數。 通常用在 include 檔。  
  
## <a name="see-also"></a>請參閱  
 [指示詞參考](../../assembler/masm/directives-reference.md)