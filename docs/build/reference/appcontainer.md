---
title: "-APPCONTAINER |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- /APPCONTAINER
dev_langs:
- C++
helpviewer_keywords:
- APPCONTAINER editbin option
- -APPCONTAINER editbin option
- /APPCONTAINER editbin option
ms.assetid: 0ca4f1ec-c8de-4a37-b3e2-deda7af0bb88
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 08966cd2b9da434c45750edb57644c182a14baf2
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/14/2018
---
# <a name="appcontainer"></a>/APPCONTAINER
必須在應用程式容器中執行的執行檔標記 — 例如，Microsoft 市集或通用 Windows 應用程式。  
  
```  
  
/APPCONTAINER[:NO]  
```  
  
## <a name="remarks"></a>備註  
 已設定 **/APPCONTAINER** 選項的可執行檔只能在應用程式容器中執行，這是在 Windows 8 中引進的處理序隔離環境。 Microsoft 存放區與通用 Windows 應用程式，必須設定這個選項。  
  
## <a name="see-also"></a>請參閱  
 [EDITBIN 選項](../../build/reference/editbin-options.md)   
 [什麼是通用 Windows 應用程式？](http://go.microsoft.com/fwlink/p/?LinkID=522074)