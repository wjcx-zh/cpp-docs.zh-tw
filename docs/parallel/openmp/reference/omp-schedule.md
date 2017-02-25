---
title: "OMP_SCHEDULE | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "OMP_SCHEDULE"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "OMP_SCHEDULE OpenMP environment variable"
ms.assetid: 2295a801-e584-4d2f-826f-7ca4c88846a6
caps.latest.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 8
---
# OMP_SCHEDULE
[!INCLUDE[vs2017banner](../../../assembler/inline/includes/vs2017banner.md)]

可修改[schedule](../../../parallel/openmp/reference/schedule.md)子句時`schedule(runtime)`中所指定`for`或`parallel for`指示詞。  
  
## 語法  
  
```  
set OMP_SCHEDULE[=type[,size]]  
```  
  
## 備註  
 其中，  
  
 `size` \(選擇項\)  
 指定反覆項目的大小。  `size`必須是正整數。  預設值為 1，但是下列情況除外`type`是靜態的。  Not valid when `type` is `runtime`.  
  
 `type`  
 排程的類型：  
  
-   `dynamic`  
  
-   `guided`  
  
-   `runtime`  
  
-   `static`  
  
## 備註  
 在 Visual C\+\+ 實作 OpenMP 標準的預設值是`OMP_SCHEDULE=static,0`。  
  
 如需詳細資訊，請參閱 [4.1 OMP\_SCHEDULE](../../../parallel/openmp/4-1-omp-schedule.md)。  
  
## 範例  
 下列指令集 **OMP\_SCHEDULE** 環境變數：  
  
```  
set OMP_SCHEDULE="guided,2"  
```  
  
 下列命令會顯示目前設定的 **OMP\_SCHEDULE** 環境變數：  
  
```  
set OMP_SCHEDULE  
```  
  
## 請參閱  
 [Environment Variables](../../../parallel/openmp/reference/openmp-environment-variables.md)