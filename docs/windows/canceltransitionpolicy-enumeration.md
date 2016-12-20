---
title: "CancelTransitionPolicy 列舉 | Microsoft Docs"
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
  - "module/Microsoft::WRL::CancelTransitionPolicy::TransitionFromCanceled"
  - "module/Microsoft::WRL::CancelTransitionPolicy::RemainCanceled"
  - "module/Microsoft::WRL::CancelTransitionPolicy"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CancelTransitionPolicy 列舉"
ms.assetid: 5de49f7d-e5e3-43e9-bbca-666caf226cef
caps.latest.revision: 3
caps.handback.revision: 3
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CancelTransitionPolicy 列舉
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

表示對於一個用戶端要求的取消狀態而言，非同步作業嘗試轉換到完成或錯誤的結束狀態時應該如何行為。  
  
## 語法  
  
```  
enum CancelTransitionPolicy;  
```  
  
## Members  
  
### 值  
  
|名稱|描述|  
|--------|--------|  
|`RemainCanceled`|如果非同步作業目前在一個用戶端要求的已取消的狀態，這表示它將會保持在已取消的狀態而非轉換為終端完成或錯誤狀態。|  
|`TransitionFromCanceled`|如果非同步作業目前在一個用戶端要求的已取消的狀態，這表示狀態必須從取消狀態依照利用這個旗幟的呼叫轉換到完成或錯誤的結束狀態。|  
  
## 需求  
 **標題:** async.h  
  
 **命名空間：**Microsoft::WRL  
  
## 請參閱  
 [Microsoft::WRL 命名空間](../windows/microsoft-wrl-namespace.md)