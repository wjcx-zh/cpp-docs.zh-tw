---
title: "pgomgr | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "pgomgr 程式"
  - "特性指引最佳化, pgomgr"
ms.assetid: 74589126-df18-42c9-8739-26d60e148d6a
caps.latest.revision: 18
caps.handback.revision: 18
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# pgomgr
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

將分析資料從一個或多個 .pgc 檔 加入至 .pgd 檔。  
  
## 語法  
  
```  
pgomgr [options] pgcfiles pgdfile  
```  
  
#### 參數  
 `options`  
 下列選項可以指定給 pgomgr：  
  
 **\/help** \-\- 顯示可用的 pgomgr 選項 \(簡短形式為 \/?\)。  
  
 **\/clear** \-\- 讓 .pgd 檔案清除所有分析資訊。  指定 **\/clear** 時，您不能指定 .pgc 檔。  
  
 **\/detail** \-\- 顯示詳細的統計資訊，其中包括流程圖涵蓋範圍資訊。  
  
 **\/summary** \-\- 顯示每個函式的統計資訊。  
  
 **\/unique** \-\- 配合 **\/summary** 使用時，讓裝飾函式名稱顯示出來。不使用 \/unique 時，預設為顯示未裝飾函式名稱。  
  
 **\/merge**\[**:***n*\] \-\- 讓一個或多個 .pgc 檔案中的資料加入至 .pgd 檔。選擇性參數，*n*，讓您指定資料必須加入 *n* 次。例如，如果案例一般是做 6 次，您可以在測試回合中做 1 次，使用 **pgomgr \/merge:6**，將它加入 .pgd 檔中 6 次。  
  
 `pgcfiles`  
 您要將其中分析資料合併入 .pgd 檔中的一個或多個 .pgc 檔。  您可以指定單一 .pgc 檔或多個 .pgc 檔。  如果您不指定任何 .pgc 檔案，pgomgr 就會合併檔案名稱與 .pgd 檔相同的所有 .pgc 檔案。  
  
 `pgdfile`  
 您要從一個或多個 .pgc 檔案合併入資料的 .pgd 檔。  
  
## 備註  
  
> [!NOTE]
>  您只能從 [!INCLUDE[vsprvs](../../assembler/masm/includes/vsprvs_md.md)] 命令提示字元啟動這個工具。  您不能從系統命令提示字元或從檔案總管來啟動它。  
  
## 範例  
 在下列範例中，.pgd 檔案中的分析資料完全清除。  
  
```  
pgomgr /clear myapp.pgd  
```  
  
 在下列範例中，將 myapp1.pgc 中的分析資料加入至 .pgd 檔中 3 次。  
  
```  
pgomgr /merge:3 myapp1.pgc myapp.pgd  
```  
  
 在下列範例中，從所有 myapp\#.pgc 檔中將所有分析資料都加入至 myapp.pgd 檔。  
  
```  
pgomgr -merge myapp1.pgd  
```  
  
## 請參閱  
 [特性指引最佳化工具](../../build/reference/tools-for-manual-profile-guided-optimization.md)