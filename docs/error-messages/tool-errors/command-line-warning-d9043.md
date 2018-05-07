---
title: 命令列警告 D9043 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- D9043
dev_langs:
- C++
helpviewer_keywords:
- D9043
ms.assetid: 9263e28d-217b-414c-bfb6-86efd3c27a77
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 65bf672418b49dbf6017374ab7cd18caa61d7403
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="command-line-warning-d9043"></a>命令列警告 D9043
無效的值 'warning_level' 的 'compiler_option';假設 '4999';程式碼分析警告不會支援警告層級產生關聯  
  
## <a name="example"></a>範例  
 下列範例會產生 C9043。  
  
```  
// D9043.cpp  
// compile with: /analyze /w16001  
// D9043 warning expected  
int main() {}  
```