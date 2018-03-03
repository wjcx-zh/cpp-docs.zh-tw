---
title: "命令列警告 D9041 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- D9041
dev_langs:
- C++
helpviewer_keywords:
- D9041
ms.assetid: ada8815f-4246-4e25-b57d-a7f16fa107cc
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 307d290bb525ee879f29853c6823d5b9565aba4b
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="command-line-warning-d9041"></a>命令列警告 D9041
無效的值 'value' 的 '/option';假設 'value';加入 '/analyze' 命令列選項時指定這項警告  
  
 程式碼分析警告數字相加**/wd**， **/we**， **/wo**，或**/wl**未同時指定命令列選項**/ 分析**命令列選項。 若要解決這個錯誤，請新增**/ 分析**命令列選項，或移除無效的警告編號，從適當**/w**命令列選項。  
  
## <a name="example"></a>範例  
 下列命令列範例會產生警告 D9041:  
  
```  
cl /EHsc /LD /wd6001 filename.cpp  
```  
  
 若要修正警告，加入**/ 分析**命令列選項。 如果**/ 分析**不是支援您的編譯器版本上，移除無效的警告編號，從**/wd**選項。  
  
## <a name="see-also"></a>請參閱  
 [命令列錯誤 D8000 至 D9999](../../error-messages/tool-errors/command-line-errors-d8000-through-d9999.md)   
 [編譯器選項](../../build/reference/compiler-options.md)