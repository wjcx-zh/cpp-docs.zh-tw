---
title: "time_base 類別 | Microsoft Docs"
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
  - "std.time_base"
  - "std::time_base"
  - "time_base"
  - "locale/std::time_base"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "time_base 類別"
ms.assetid: 9ae37f0b-9a42-496e-9870-3d9b71bab8fb
caps.latest.revision: 19
caps.handback.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# time_base 類別
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

類別可做為類別的基底類別 \(Base Class\) 範本 Facet 把 time\_get 分類，定義列舉型別 **dateorder** 和型別的常數。  
  
## 語法  
  
```  
class time_base : public locale::facet {  
public:  
    enum dateorder {no_order, dmy, mdy, ymd, ydm};  
    time_base(  
        size_t _Refs = 0  
    )  
    ~time_base();  
};  
```  
  
## 備註  
 每個常數 Draw 一種排序日期的元件。  常數是:  
  
-   **no\_order** 不指定特定順序。  
  
-   **dmy** 在 1979 年 12 月 2 日指定命令天，月，年，然後。  
  
-   **mdy** 在 1979 年 12 月 2 日指定命令月、日，，然後年份，。  
  
-   **ymd** 在 1979\/12\/2. 指定命令，表示月份日期，然後，。  
  
-   **ydm** 在 1979 年指定命令中，日期，然後月份，:2 減一。  
  
## 需求  
 **Header:** \<地區設定\>  
  
 **命名空間:** std  
  
## 請參閱  
 [C\+\+ 標準程式庫中的執行緒安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)