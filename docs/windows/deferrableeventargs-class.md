---
title: "DeferrableEventArgs 類別 | Microsoft Docs"
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
ms.assetid: ece89267-7b72-40e1-8185-550c865b070a
caps.latest.revision: 3
caps.handback.revision: 3
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# DeferrableEventArgs 類別
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

範本類別，用於延期的事件引數類型。  
  
## 語法  
  
```cpp  
template <  
typename TEventArgsInterface,  
typename TEventArgsClass  
>  
class DeferrableEventArgs : public TEventArgsInterface  
  
```  
  
#### 參數  
 `TEventArgsInterface`  
 宣告延期事件之引數的介面類別。  
  
 `TEventArgsClass`  
 會實作 `TEventArgsInterface` 的類別。  
  
## 成員  
  
### 公用方法  
  
|名稱|描述|  
|--------|--------|  
|[DeferrableEventArgs::GetDeferral 方法](../windows/deferrableeventargs-getdeferral-method.md)|取得[延期](http://go.microsoft.com/fwlink/?LinkId=526520)物件的參考，此物件代表延期事件。|  
|[DeferrableEventArgs::InvokeAllFinished 方法](../windows/deferrableeventargs-invokeallfinished-method.md)|呼叫此方法，表示已完成延期事件的所有處理。|  
  
## 備註  
 這個類別的執行個體會傳遞至延期事件的事件處理常式。  範本參數代表定義延期事件特定類型之事件引數詳細資料的介面，以及實作該介面的類別。  
  
 此類別會顯示為延期事件之事件處理常式的第一個引數。  您可以呼叫 [GetDeferral](../windows/deferrableeventargs-getdeferral-method.md) 方法來取得[延期](http://go.microsoft.com/fwlink/?LinkId=526520)物件，並且可以從中取得有關延期事件的所有資訊。  完成事件處理之後，您應該在延期物件上呼叫 Complete。  您應該在事件處理常式方法的結尾接著呼叫 [InvokeAllFinished](../windows/deferrableeventargs-invokeallfinished-method.md)，以確保所有延期事件的完成都正確通訊。  
  
## 需求  
 **標頭：**event.h  
  
 **命名空間：**Microsoft::WRL  
  
## 請參閱  
 [Microsoft::WRL 命名空間](../windows/microsoft-wrl-namespace.md)