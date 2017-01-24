---
title: "VCPROFILE_ALLOC_SCALE | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VCPROFILE_ALLOC_SCALE"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "VCPROFILE_ALLOC_SCALE 環境變數"
ms.assetid: 5cb5ce27-f9b8-489b-b46c-d6e9bcab2d34
caps.latest.revision: 4
caps.handback.revision: 4
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# VCPROFILE_ALLOC_SCALE
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

修改配置給存放分析資料的記憶體量。  
  
## 語法  
  
```  
VCPROFILE_ALLOC_SCALE=scale_value  
```  
  
#### 參數  
 `scale_value`  
 您要用來執行測試案例之記憶體量的小數位數值。預設值為 1。  
  
## 備註  
 在極為少見的情形下，執行測試案例時支援收集分析資料的可用記憶體量會有不足。此時，您可以使用 `VCPROFILE_ALLOC_SCALE` 增加記憶體量。  
  
 如果您在測試回合期間接到錯誤訊息，表示您的記憶體量不足，請指定較大的值給 `VCPROFILE_ALLOC_SCALE`，直到測試回合在未發生記憶體不足的錯誤下完成為止。  
  
## 範例  
  
```  
set VCPROFILE_ALLOC_SCALE=2  
```  
  
## 請參閱  
 [特性指引最佳化的環境變數](../../build/reference/environment-variables-for-profile-guided-optimizations.md)