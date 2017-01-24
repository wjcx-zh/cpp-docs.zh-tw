---
title: "AsyncBase 類別 | Microsoft Docs"
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
  - "async/Microsoft::WRL::AsyncBase"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "AsyncBase 類別"
ms.assetid: 64259b9b-f427-4ffd-a611-e7a2f82362b2
caps.latest.revision: 3
caps.handback.revision: 3
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# AsyncBase 類別
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

實作 Windows 執行階段非同步系統。  
  
## 語法  
  
```  
  
template <  
   typename TComplete,  
   typename TProgress = Details::Nil,  
   AsyncResultType resultType = SingleResult  
>  
class AsyncBase : public AsyncBase< TComplete, Details::Nil, resultType >;  
  
template <  
   typename TComplete,  
   AsyncResultType resultType  
>  
class AsyncBase< TComplete, Details::Nil, resultType > : public Microsoft::WRL::Implements< IAsyncInfo >;  
```  
  
#### 參數  
 `TComplete`  
 當非同步作業完成時要呼叫的事件處理常式。  
  
 `TProgress`  
 當執行中的非同步作業報告作業的目前進度時要呼叫的事件處理常式。  
  
 `resultType`  
 必須是 [AsyncResultType](../windows/asyncresulttype-enumeration.md) 列舉型別 \(Enumeration\) 當中的任一值。  根據預設， SingleResult。  
  
## Members  
  
### 公用建構函式  
  
|名稱|描述|  
|--------|--------|  
|[AsyncBase::AsyncBase 建構函式](../windows/asyncbase-asyncbase-constructor.md)|初始化 AsyncBase 類別的執行個體。|  
  
### 公用方法  
  
|名稱|描述|  
|--------|--------|  
|[AsyncBase::Cancel 方法](../windows/asyncbase-cancel-method.md)|取消非同步的作業。|  
|[AsyncBase::Close 方法](../windows/asyncbase-close-method.md)|結束非同步作業。|  
|[AsyncBase::FireCompletion 方法](../windows/asyncbase-firecompletion-method.md)|叫用完成事件處理常式或重設內部進度委派。|  
|[AsyncBase::FireProgress 方法](../windows/asyncbase-fireprogress-method.md)|叫用目前進度事件處理常式。|  
|[AsyncBase::get\_ErrorCode 方法](../windows/asyncbase-get-errorcode-method.md)|擷取目前的非同步作業的錯誤碼。|  
|[AsyncBase::get\_Id 方法](../windows/asyncbase-get-id-method.md)|擷取這個非同步作業的控制代碼。|  
|[AsyncBase::get\_Status 方法](../windows/asyncbase-get-status-method.md)|擷取表示非同步作業的狀態的值。|  
|[AsyncBase::GetOnComplete 方法](../windows/asyncbase-getoncomplete-method.md)|複製目前完成事件處理常式的位址所指定的變數。|  
|[AsyncBase::GetOnProgress 方法](../windows/asyncbase-getonprogress-method.md)|複製目前進度事件處理常式的位址至所指定的變數。|  
|[AsyncBase::put\_Id 方法](../windows/asyncbase-put-id-method.md)|設定這個非同步作業的控制代碼。|  
|[AsyncBase::PutOnComplete 方法](../windows/asyncbase-putoncomplete-method.md)|設定完成事件處理常式的位址為指定的值。|  
|[AsyncBase::PutOnProgress 方法](../windows/asyncbase-putonprogress-method.md)|設定進度事件處理常式的位址為指定的值。|  
|[AsyncBase::Start 方法](../windows/asyncbase-start-method.md)|啟動非同步作業。|  
  
### 受保護的方法  
  
|名稱|描述|  
|--------|--------|  
|[AsyncBase::CheckValidStateForDelegateCall 方法](../windows/asyncbase-checkvalidstatefordelegatecall-method.md)|測試委派屬性是否在目前非同步狀態進行修改。|  
|[AsyncBase::CheckValidStateForResultsCall 方法](../windows/asyncbase-checkvalidstateforresultscall-method.md)|測試一個非同步作業的結果是否可以在目前非同步狀態收集。|  
|[AsyncBase::ContinueAsyncOperation 方法](../windows/asyncbase-continueasyncoperation-method.md)|判斷非同步作業是否應該繼續處理或應該中止。|  
|[AsyncBase::CurrentStatus 方法](../windows/asyncbase-currentstatus-method.md)|擷取目前的非同步作業的狀態。|  
|[AsyncBase::ErrorCode 方法](../windows/asyncbase-errorcode-method.md)|擷取目前的非同步作業的錯誤碼。|  
|[AsyncBase::OnCancel 方法](../windows/asyncbase-oncancel-method.md)|在衍生類別中覆寫時，取消同步作業。|  
|[AsyncBase::OnClose 方法](../windows/asyncbase-onclose-method.md)|在衍生類別中覆寫時，關閉非同步作業。|  
|[AsyncBase::OnStart 方法](../windows/asyncbase-onstart-method.md)|在衍生類別中覆寫時，啟動非同步作業。|  
|[AsyncBase::TryTransitionToCompleted 方法](../windows/asyncbase-trytransitiontocompleted-method.md)|指出目前非同步作業是否已經完成。|  
|[AsyncBase::TryTransitionToError 方法](../windows/asyncbase-trytransitiontoerror-method.md)|指示指定的錯誤碼是否可以修改內部錯誤狀態。|  
  
## 繼承階層架構  
 `AsyncBase`  
  
 `AsyncBase`  
  
## 需求  
 **標題:** async.h  
  
 **命名空間：**Microsoft::WRL  
  
## 請參閱  
 [Microsoft::WRL 命名空間](../windows/microsoft-wrl-namespace.md)