---
title: "HString::HString 建構函式 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "corewrappers/Microsoft::WRL::Wrappers::HString::HString"
dev_langs: 
  - "C++"
ms.assetid: 6da12785-ed01-4720-a004-667db60298f1
caps.latest.revision: 2
caps.handback.revision: 2
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# HString::HString 建構函式
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

初始化 HString 類別的新執行個體。  
  
## 語法  
  
```cpp  
  
HString(HSTRING hstr = nullptr) throw();  
HString(HString&& other) throw();  
```  
  
#### 參數  
 `hstr`  
 HSTRING 控制代碼。  
  
 `other`  
 現有的 HString 物件。  
  
## 備註  
 第一個建構函式初始化空白的新 HString 物件。  
  
 第二個建構函式初始化至現有 `other` 參數的值建立新的 HString 物件，然後終結 `other` 參數。  
  
## 需求  
 **標題:** corewrappers.h  
  
 **命名空間：**Microsoft::WRL::Wrappers  
  
## 請參閱  
 [HString 類別](../windows/hstring-class.md)