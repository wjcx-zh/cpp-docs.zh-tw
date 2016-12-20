---
title: "/APPCONTAINER | Microsoft Docs"
ms.custom: ""
ms.date: "12/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "/APPCONTAINER"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "/APPCONTAINER editbin 選項"
  - "APPCONTAINER editbin 選項"
  - "-APPCONTAINER editbin 選項"
ms.assetid: 0ca4f1ec-c8de-4a37-b3e2-deda7af0bb88
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# /APPCONTAINER
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

標記必須在應用程式容器中執行的可執行檔；例如 [!INCLUDE[win8_appname_long](../../build/includes/win8_appname_long_md.md)] 或通用 Windows 應用程式。  
  
```  
  
/APPCONTAINER[:NO]  
```  
  
## 備註  
 已設定 **\/APPCONTAINER** 選項的可執行檔只能在應用程式容器中執行，這是在 Windows 8 中引進的處理序隔離環境。 若為 [!INCLUDE[win8_appname_long](../../build/includes/win8_appname_long_md.md)] 和通用 Windows 應用程式，必須設定這個選項。  
  
## 請參閱  
 [EDITBIN 選項](../../build/reference/editbin-options.md)   
 [通用 Windows 應用程式是什麼？](http://go.microsoft.com/fwlink/p/?LinkID=522074)