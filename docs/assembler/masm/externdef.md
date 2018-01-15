---
title: "EXTERNDEF |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: EXTERNDEF
dev_langs: C++
helpviewer_keywords: EXTERNDEF directive
ms.assetid: 95a10de6-c345-4428-a2f2-90f7d411dc86
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: a06378b7cf1217c01f57d7994220bfe5dd585a66
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
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