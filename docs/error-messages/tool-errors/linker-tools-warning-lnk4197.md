---
title: 連結器工具警告 LNK4197 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- LNK4197
dev_langs:
- C++
helpviewer_keywords:
- LNK4197
ms.assetid: 8a976fd7-a74b-4c83-ab66-a9e7d7073c4a
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: dfef7f0fe2d9cd50fa6a18ad682c3e4d80df99c8
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33300825"
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