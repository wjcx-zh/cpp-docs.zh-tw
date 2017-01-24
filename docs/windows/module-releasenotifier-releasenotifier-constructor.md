---
title: "Module::ReleaseNotifier::ReleaseNotifier 建構函式 | Microsoft Docs"
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
  - "module/Microsoft::WRL::Module::ReleaseNotifier::ReleaseNotifier"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "ReleaseNotifier, 建構函式"
ms.assetid: 889a3c9a-2366-44a1-ba7d-a59c1885e7f3
caps.latest.revision: 3
caps.handback.revision: 3
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Module::ReleaseNotifier::ReleaseNotifier 建構函式
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

初始化 Module::ReleaseNotifier 類別的新執行個體。  
  
## 語法  
  
```cpp  
ReleaseNotifier(bool release) throw();  
```  
  
#### 參數  
 `release`  
 `true` 當呼叫釋放方法時刪除這個執行個體的， `false` 不要刪除這個執行個體。  
  
## 例外狀況  
  
## 需求  
 **標題:** module.h  
  
 **命名空間：**Microsoft::WRL  
  
## 請參閱  
 [Module::ReleaseNotifier 類別](../windows/module-releasenotifier-class.md)