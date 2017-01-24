---
title: "DeferrableEventArgs::GetDeferral 方法 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
dev_langs: 
  - "C++"
ms.assetid: ef6dc7c5-b0be-4b85-8507-d3fd97f2185d
caps.latest.revision: 3
caps.handback.revision: 3
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# DeferrableEventArgs::GetDeferral 方法
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

取得[延期](http://go.microsoft.com/fwlink/?LinkId=526520)物件的參考，此物件代表延期事件。  
  
## 語法  
  
```cpp  
HRESULT GetDeferral([out, retval] Windows::Foundation::IDeferral** result)  
```  
  
#### 參數  
 `result`  
 將在呼叫完成時參考[延期](http://go.microsoft.com/fwlink/?LinkId=526520)物件的指標。  
  
## 傳回值  
 如果作業成功，會傳送 S\_OK；反之則傳送表示錯誤的 HRESULT 值。  
  
## 備註  
 如需程式碼範例，請參閱 [DeferrableEventArgs 類別](../windows/deferrableeventargs-class.md)。  
  
## 需求  
 **標頭：**event.h  
  
 **命名空間：**Microsoft::WRL  
  
## 請參閱  
 [DeferrableEventArgs 類別](../windows/deferrableeventargs-class.md)