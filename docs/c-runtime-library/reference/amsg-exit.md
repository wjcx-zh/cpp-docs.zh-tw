---
title: "_amsg_exit | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_amsg_exit"
apilocation: 
  - "msvcrt.dll"
  - "msvcr80.dll"
  - "msvcr90.dll"
  - "msvcr100.dll"
  - "msvcr100_clr0400.dll"
  - "msvcr110.dll"
  - "msvcr110_clr0400.dll"
  - "msvcr120.dll"
  - "msvcr120_clr0400.dll"
  - "ucrtbase.dll"
apitype: "DLLExport"
f1_keywords: 
  - "_amsg_exit"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_amsg_exit"
ms.assetid: 146d4faf-d763-43a4-b264-12711196456b
caps.latest.revision: 2
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 2
---
# _amsg_exit
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

發出指定的執行階段錯誤訊息並結束您的錯誤碼 255 的應用程式。  
  
## 語法  
  
```cpp  
void _amsg_exit (  
   int rterrnum  
   )  
  
```  
  
#### 參數  
 `rterrnum`  
 表示系統定義的執行階段錯誤訊息的識別碼。  
  
## 備註  
 這個函式會發出執行階段錯誤訊息至主控台應用程式的 **stderr** 或顯示 Windows 應用程式的訊息方塊訊息。  在偵錯模式中，您可以選擇在結束之前叫用偵錯工具。  
  
## 需求  
  
|常式|必要的標頭|  
|--------|-----------|  
|\_amsg\_exit|internal.h|