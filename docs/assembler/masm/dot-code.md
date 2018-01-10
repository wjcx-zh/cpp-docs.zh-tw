---
title: ".程式碼 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: .CODE
dev_langs: C++
helpviewer_keywords: .CODE directive
ms.assetid: 2b8c882c-c0d2-4fa3-8335-e6b12717a4f4
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 150b5a0c26be3c3c4d0412157179ebfcbec128e7
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="code"></a>.CODE
當搭配[。模型](../../assembler/masm/dot-model.md)，表示程式碼區段的開頭。  
  
## <a name="syntax"></a>語法  
  
```  
.CODE [[name]]  
```  
  
#### <a name="parameters"></a>參數  
  
|參數|描述|  
|---------------|-----------------|  
|`name`|指定名稱的程式碼區段的選擇性參數。 預設名稱是很小，很小，壓縮和一般 _TEXT[模型](../../assembler/masm/dot-model.md)。 預設名稱是*modulename*_TEXT 其他模型。|  
  
## <a name="see-also"></a>請參閱  
 [指示詞參考](../../assembler/masm/directives-reference.md)   
 [.DATA](../../assembler/masm/dot-data.md)