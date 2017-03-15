---
title: "VCPROFILE_PATH | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VCPROFILE_PATH"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "VCPROFILE_PATH 環境變數"
ms.assetid: 25217aa4-7e86-4eba-854d-10b3c457e4df
caps.latest.revision: 4
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 4
---
# VCPROFILE_PATH
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

指定要建立 .pgc 檔案的目錄。  
  
## 語法  
  
```  
VCPROFILE_PATH=path  
```  
  
#### 參數  
 `path`  
 .pgc 檔案要加入的目錄路徑。  
  
## 備註  
 根據預設，.pgc 檔案的建立目錄與被分析的二進位檔案相同。但是，如果沒有二進位的絕對路徑 \(當您在非建置二進位的電腦上執行分析案例時，可能就沒有\)，您可以將 `VCPROFILE_PATH` 設定至既有的路徑。  
  
## 範例  
  
```  
set VCPROFILE_PATH=c:\  
```  
  
## 請參閱  
 [特性指引最佳化的環境變數](../../build/reference/environment-variables-for-profile-guided-optimizations.md)