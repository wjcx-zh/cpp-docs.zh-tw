---
title: "Module::GenericReleaseNotifier::GenericReleaseNotifier 建構函式 | Microsoft Docs"
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
  - "module/Microsoft::WRL::Module::GenericReleaseNotifier::GenericReleaseNotifier"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "GenericReleaseNotifier，建構函式"
ms.assetid: feb5b687-a4b0-4809-9022-8f292181b7a1
caps.latest.revision: 3
caps.handback.revision: 3
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Module::GenericReleaseNotifier::GenericReleaseNotifier 建構函式
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

初始化 Module::GenericReleaseNotifier 類別的新執行個體。  
  
## 語法  
  
```  
GenericReleaseNotifier(  
   T callback,   
   bool release  
) throw() : ReleaseNotifier(release), callback_(callback);  
```  
  
#### 參數  
 `callback`  
 可以叫用括號運算式 \(`()`\) 呼叫Lambda 函式、functor 或函式指標的事件處理常式。  
  
 `release`  
 指定 `true` 來啟用呼叫基礎 [Module::ReleaseNotifier::Release \(\)](../windows/module-releasenotifier-release.md) 方法;否則，請指定 `false`。  
  
## 需求  
 **標題:** module.h  
  
 **命名空間：**Microsoft::WRL  
  
## 請參閱  
 [Module::GenericReleaseNotifier 類別](../windows/module-genericreleasenotifier-class.md)