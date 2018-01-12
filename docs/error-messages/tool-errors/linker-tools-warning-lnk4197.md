---
title: "連結器工具警告 LNK4197 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: LNK4197
dev_langs: C++
helpviewer_keywords: LNK4197
ms.assetid: 8a976fd7-a74b-4c83-ab66-a9e7d7073c4a
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: b1fadbf2ba5b18004f0e89142c88a68437842a92
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="linker-tools-warning-lnk4197"></a>連結器工具警告 LNK4197
匯出 'exportname' 指定多次;使用第一個規格  
  
 在多個指定的匯出和不同的方式。 連結器會使用第一個規格，並忽略其餘部分。  
  
 如果您要重建 C 執行階段程式庫，您可以忽略此訊息。  
  
 如果匯出指定完全相同的方法多次，則連結器不會發出警告。  
  
 例如，在.def 檔的下列內容會導致此警告：  
  
```  
EXPORTS  
   functioname      NONAME  
   functioname      @10  
```  
  
### <a name="to-fix-by-checking-the-following-possible-causes"></a>透過檢查下列可能原因進行修正  
  
1.  指定相同的匯出同時在命令列上 (透過匯出:) 和.def 檔案中  
  
2.  相同的匯出會列出兩次.def 檔案中有不同的屬性。