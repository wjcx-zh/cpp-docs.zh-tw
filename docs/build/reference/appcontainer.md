---
title: "-APPCONTAINER |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: /APPCONTAINER
dev_langs: C++
helpviewer_keywords:
- APPCONTAINER editbin option
- -APPCONTAINER editbin option
- /APPCONTAINER editbin option
ms.assetid: 0ca4f1ec-c8de-4a37-b3e2-deda7af0bb88
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 19e926cbfd1fc58e04c8370825dd83eacff05dfe
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="appcontainer"></a>/APPCONTAINER
標記必須在應用程式容器中執行的可執行檔；例如 [!INCLUDE[win8_appname_long](../../build/includes/win8_appname_long_md.md)] 或通用 Windows 應用程式。  
  
```  
  
/APPCONTAINER[:NO]  
```  
  
## <a name="remarks"></a>備註  
 已設定 **/APPCONTAINER** 選項的可執行檔只能在應用程式容器中執行，這是在 Windows 8 中引進的處理序隔離環境。 若為 [!INCLUDE[win8_appname_long](../../build/includes/win8_appname_long_md.md)] 和通用 Windows 應用程式，必須設定這個選項。  
  
## <a name="see-also"></a>請參閱  
 [EDITBIN 選項](../../build/reference/editbin-options.md)   
 [什麼是通用 Windows 應用程式？](http://go.microsoft.com/fwlink/p/?LinkID=522074)