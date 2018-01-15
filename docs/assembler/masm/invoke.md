---
title: "叫用 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: Invoke
dev_langs: C++
helpviewer_keywords: INVOKE directive
ms.assetid: 12d9bb40-33b9-411e-b801-45a1d675967e
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: a4e17298c59a1c8620eb2261c44e5bd9c3aaceb0
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="invoke"></a>INVOKE
在指定的位址呼叫程序*運算式*，在堆疊上，或根據語言類型的標準呼叫慣例的暫存器中傳遞的引數。  
  
## <a name="syntax"></a>語法  
  
```  
  
INVOKE   
expression [[, arguments]]  
```  
  
## <a name="remarks"></a>備註  
 每個引數傳遞至程序可能是運算式、 一個暫存器配對或運算式的位址 (運算式前面加上`ADDR`)。  
  
## <a name="see-also"></a>請參閱  
 [指示詞參考](../../assembler/masm/directives-reference.md)