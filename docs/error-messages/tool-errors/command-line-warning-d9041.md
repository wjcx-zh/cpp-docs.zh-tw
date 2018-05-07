---
title: 命令列警告 D9041 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- D9041
dev_langs:
- C++
helpviewer_keywords:
- D9041
ms.assetid: ada8815f-4246-4e25-b57d-a7f16fa107cc
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: c22573d26e09e14789f4cbd64d68f4082125c2b3
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="command-line-warning-d9041"></a>命令列警告 D9041
無效的值 'value' 的 '/option';假設 'value';加入 '/analyze' 命令列選項時指定這項警告  
  
 程式碼分析警告數字相加 **/wd**， **/we**， **/wo**，或 **/wl**未同時指定命令列選項 **/ 分析**命令列選項。 若要解決這個錯誤，請新增 **/ 分析**命令列選項，或移除無效的警告編號，從適當 **/w**命令列選項。  
  
## <a name="example"></a>範例  
 下列命令列範例會產生警告 D9041:  
  
```  
cl /EHsc /LD /wd6001 filename.cpp  
```  
  
 若要修正警告，加入 **/ 分析**命令列選項。 如果 **/ 分析**不是支援您的編譯器版本上，移除無效的警告編號，從 **/wd**選項。  
  
## <a name="see-also"></a>另請參閱  
 [命令列錯誤 D8000 至 D9999](../../error-messages/tool-errors/command-line-errors-d8000-through-d9999.md)   
 [編譯器選項](../../build/reference/compiler-options.md)