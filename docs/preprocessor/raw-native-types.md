---
title: "raw_native_types | Microsoft Docs"
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
  - "raw_native_types"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "raw_native_types 屬性"
ms.assetid: 9f38daa8-8dc0-46a5-aff9-f1ff9c1e6f48
caps.latest.revision: 5
caps.handback.revision: 5
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# raw_native_types
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**C\+\+ 專有的**  
  
 停用在高階包裝函式中使用 COM 支援類別，並強制改用低階資料類型。  
  
## 語法  
  
```  
raw_native_types  
```  
  
## 備註  
 根據預設，高階錯誤處理方法會使用 COM 支援類別 [\_bstr\_t](../cpp/bstr-t-class.md) 和 [\_variant\_t](../cpp/variant-t-class.md) 取代 `BSTR` 和 **VARIANT** 資料類型以及一般 COM 介面指標。  這些類別會封裝為這些資料類型配置和解除配置之記憶體儲存區的詳細資料，並且大幅簡化類型轉換和轉換作業。  
  
 **END C\+\+ 特定的**  
  
## 請參閱  
 [\#import 屬性](../preprocessor/hash-import-attributes-cpp.md)   
 [\#import 指示詞](../preprocessor/hash-import-directive-cpp.md)