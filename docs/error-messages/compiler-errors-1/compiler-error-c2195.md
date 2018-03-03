---
title: "編譯器錯誤 C2195 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C2195
dev_langs:
- C++
helpviewer_keywords:
- C2195
ms.assetid: 9f9f035c-9c51-4173-a8ea-c6f907fc5c63
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: fc29ab5ff19a8cca8af0a07ec7af3b8f336be1de
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-error-c2195"></a>編譯器錯誤 C2195
'identifier': 是資料區段  
  
 `code_seg` Pragma 會使用區段名稱搭配使用`data_seg`pragma。  
  
 下列範例會產生 C2195:  
  
```  
// C2195.cpp  
#pragma data_seg("MYDATA")  
#pragma code_seg("MYDATA")   // C2195  
#pragma code_seg("MYDATA2")   // OK  
```