---
title: "Module::MethodReleaseNotifier::MethodReleaseNotifier 建構函式 | Microsoft Docs"
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
  - "module/Microsoft::WRL::Module::MethodReleaseNotifier::MethodReleaseNotifier"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "MethodReleaseNotifier, 建構函式"
ms.assetid: 762e2ca4-0a92-49de-9ff5-d3efa0f067c0
caps.latest.revision: 3
caps.handback.revision: 3
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Module::MethodReleaseNotifier::MethodReleaseNotifier 建構函式
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

初始化 Module::MethodReleaseNotifier 類別的新執行個體。  
  
## 語法  
  
```  
  
MethodReleaseNotifier(  
   _In_ T* object,   
   _In_ void (T::* method)(),   
   bool release) throw() :  
            ReleaseNotifier(release), object_(object),   
            method_(method);  
```  
  
#### 參數  
 `object`  
 成員函式為事件處理常式的物件。  
  
 `method`  
 為事件處理常式的參數 `object` 的成員函式。  
  
 `release`  
 指定 `true` 啟用呼叫基礎 [Module::ReleaseNotifier::Release \(\)](../windows/module-releasenotifier-release.md) 方法;否則，請指定 `false`。  
  
## 需求  
 **標題:** module.h  
  
 **命名空間：**Microsoft::WRL  
  
## 請參閱  
 [Module::MethodReleaseNotifier 類別](../windows/module-methodreleasenotifier-class.md)