---
title: "space_info 結構 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "filesystem/std::tr2::sys::space_info"
dev_langs: 
  - "C++"
ms.assetid: f2b35b42-06ff-45bd-8617-39a0f5358a54
caps.latest.revision: 13
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 13
---
# space_info 結構
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

保留磁碟區的相關資訊。  
  
## 語法  
  
```  
struct space_info;  
```  
  
## Members  
  
### 公用資料成員  
  
|名稱|描述|  
|--------|--------|  
|`unsigned long long available`|表示可用來代表磁碟區資料的位元組數目。|  
|`unsigned long long capacity`|表示磁碟區可以表示的總位元組數目。|  
|`unsigned long long free`|表示不用來代表磁碟區資料的位元組數目。|  
  
## 需求  
 **標頭：**filesystem  
  
 **命名空間：**std::tr2::sys  
  
## 請參閱  
 [標頭檔參考](../standard-library/cpp-standard-library-header-files.md)   
 [\<filesystem\>](../standard-library/filesystem.md)   
 [space 函式](http://msdn.microsoft.com/zh-tw/7fce0b0e-523b-4598-b218-47245d0204ca)   
 [檔案系統巡覽 \(C\+\+\)](../standard-library/file-system-navigation.md)