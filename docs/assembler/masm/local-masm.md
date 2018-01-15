---
title: "本機 (MASM) |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: Local
dev_langs: C++
helpviewer_keywords: LOCAL directive
ms.assetid: 76147e2d-23ca-4f1e-8817-81428becd113
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 45ee0a98d614ee10cb7393c0e616459526b37531
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="local-masm"></a>LOCAL (MASM)
在巨集內的第一個指示詞**本機**定義巨集的每個執行個體是唯一的標籤。  
  
## <a name="syntax"></a>語法  
  
```  
  
      LOCAL localname [[, localname]]...  
LOCAL label [[ [count ] ]] [[:type]] [[, label [[ [count] ]] [[type]]]]...  
```  
  
## <a name="remarks"></a>備註  
 在程序定義中的第二個指示詞 (**PROC**)，**本機**建立堆疊式變數中所存在的程序的持續時間。 *標籤*可能是簡單的變數，或此陣列包含*計數*項目。  
  
## <a name="see-also"></a>請參閱  
 [指示詞參考](../../assembler/masm/directives-reference.md)