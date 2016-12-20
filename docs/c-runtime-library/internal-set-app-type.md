---
title: "__set_app_type | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "__set_app_type"
  - "_set_app_type"
apilocation: 
  - "msvcr90.dll"
  - "msvcr100.dll"
  - "msvcr110.dll"
  - "msvcr80.dll"
  - "msvcrt.dll"
  - "msvcr120.dll"
  - "msvcr110_clr0400.dll"
  - "api-ms-win-crt-runtime-l1-1-0.dll"
apitype: "DLLExport"
f1_keywords: 
  - "__set_app_type"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "__set_app_type"
ms.assetid: f0ac0f4d-70e6-4e96-9e43-eb9d1515490c
caps.latest.revision: 2
caps.handback.revision: 2
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# __set_app_type
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

設定目前的應用程式類型。  
  
## 語法  
  
```cpp  
void __set_app_type (  
   int at  
   )  
```  
  
#### 參數  
 `at`  
 表示應用程式類型的值。  可能的值為：  
  
|值|說明|  
|-------|--------|  
|\_UNKNOWN\_APP|未知的應用程式類型。|  
|\_CONSOLE\_APP|主控台 \(命令列\) 應用程式。|  
|\_GUI\_APP|Windows 應用程式 \(GUI\)|  
  
## 備註  
  
## 需求  
  
|常式|必要的標頭|  
|--------|-----------|  
|\_\_set\_app\_type|internal.h|