---
title: "InvokeHelper 結構 | Microsoft Docs"
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
  - "event/Microsoft::WRL::Details::InvokeHelper"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "InvokeHelper 結構"
ms.assetid: 555ad2bc-4dd6-4e65-a2e2-1242c395f0e5
caps.latest.revision: 5
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# InvokeHelper 結構
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

支援 WRL 基礎結構，而且不是為了要直接從您的程式碼中使用而設計。  
  
## 語法  
  
```  
template<  
   typename TDelegateInterface,  
   typename TCallback,  
   unsigned int argCount  
>  
struct InvokeHelper;  
template<  
   typename TDelegateInterface,  
   typename TCallback  
>  
struct InvokeHelper<TDelegateInterface, TCallback, 0> : public Microsoft::WRL::RuntimeClass<RuntimeClassFlags<Delegate>, TDelegateInterface>;  
template<  
   typename TDelegateInterface,  
   typename TCallback  
>  
struct InvokeHelper<TDelegateInterface, TCallback, 1> : public Microsoft::WRL::RuntimeClass<RuntimeClassFlags<Delegate>, TDelegateInterface>;  
template<  
   typename TDelegateInterface,  
   typename TCallback  
>  
struct InvokeHelper<TDelegateInterface, TCallback, 2> : public Microsoft::WRL::RuntimeClass<RuntimeClassFlags<Delegate>, TDelegateInterface>;  
template<  
   typename TDelegateInterface,  
   typename TCallback  
>  
struct InvokeHelper<TDelegateInterface, TCallback, 3> : public Microsoft::WRL::RuntimeClass<RuntimeClassFlags<Delegate>, TDelegateInterface>;  
template<  
   typename TDelegateInterface,  
   typename TCallback  
>  
struct InvokeHelper<TDelegateInterface, TCallback, 4> : Microsoft::WRL::RuntimeClass<RuntimeClassFlags<Delegate>, TDelegateInterface>;  
template<  
   typename TDelegateInterface,  
   typename TCallback  
>  
struct InvokeHelper<TDelegateInterface, TCallback, 5> : Microsoft::WRL::RuntimeClass<RuntimeClassFlags<Delegate>, TDelegateInterface>;  
template<  
   typename TDelegateInterface,  
   typename TCallback  
>  
struct InvokeHelper<TDelegateInterface, TCallback, 6> : Microsoft::WRL::RuntimeClass<RuntimeClassFlags<Delegate>, TDelegateInterface>;  
template<  
   typename TDelegateInterface,  
   typename TCallback  
>  
struct InvokeHelper<TDelegateInterface, TCallback, 7> : Microsoft::WRL::RuntimeClass<RuntimeClassFlags<Delegate>, TDelegateInterface>;  
template<  
   typename TDelegateInterface,  
   typename TCallback  
>  
struct InvokeHelper<TDelegateInterface, TCallback, 8> : Microsoft::WRL::RuntimeClass<RuntimeClassFlags<Delegate>, TDelegateInterface>;  
template<  
   typename TDelegateInterface,  
   typename TCallback  
>  
struct InvokeHelper<TDelegateInterface, TCallback, 9> : Microsoft::WRL::RuntimeClass<RuntimeClassFlags<Delegate>, TDelegateInterface>;  
```  
  
#### 參數  
 `TDelegateInterface`  
 `TCallback`  
 事件處理函式的型別。  
  
 `argCount`  
 InvokeHelper 特製化的中的引數數目。  
  
## 備註  
 提供根據指定引數的數目和類型的 Invoke\(\) 方法的實作。  
  
## Members  
  
### 公用 Typedefs  
  
|名稱|描述|  
|--------|--------|  
|`Traits`|定義每個事件處理常式之引數的型別之類別的一個同義資料表。|  
  
### 公用建構函式  
  
|名稱|描述|  
|--------|--------|  
|[InvokeHelper::InvokeHelper 建構函式](../windows/invokehelper-invokehelper-constructor.md)|初始化 InvokeHelper 類別的新執行個體。|  
  
### 公用方法  
  
|名稱|描述|  
|--------|--------|  
|[InvokeHelper::Invoke 方法](../windows/invokehelper-invoke-method.md)|呼叫其簽章包含指定數目引數的事件處理常式。|  
  
### 公用資料成員  
  
|名稱|描述|  
|--------|--------|  
|[InvokeHelper::callback\_ 資料成員](../windows/invokehelper-callback-data-member.md)|表示事件發生時鎖鑰呼叫的事件處理常式。|  
  
## 繼承階層架構  
 `InvokeHelper`  
  
## 需求  
 **標題:** event.h  
  
 **命名空間：** Microsoft::WRL::Details  
  
## 請參閱  
 [Microsoft::WRL::Details 命名空間](../windows/microsoft-wrl-details-namespace.md)