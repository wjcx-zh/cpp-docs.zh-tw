---
title: "task_continuation_context 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- task_continuation_context
- PPLTASKS/concurrency::task_continuation_context
- PPLTASKS/concurrency::task_continuation_context::get_current_winrt_context
- PPLTASKS/concurrency::task_continuation_context::use_arbitrary
- PPLTASKS/concurrency::task_continuation_context::use_current
- PPLTASKS/concurrency::task_continuation_context::use_default
- PPLTASKS/concurrency::task_continuation_context::use_synchronous_execution
dev_langs:
- C++
helpviewer_keywords:
- task_continuation_context class
ms.assetid: 1fb5a76a-3682-45c2-a615-8b6b527741f0
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 1b78688493bbb8d8bdad0696a7c8fcf467519000
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/14/2018
---
# <a name="taskcontinuationcontext-class"></a>task_continuation_context 類別
`task_continuation_context` 類別可讓您指定您想要執行接續的位置。 僅適用於 Windows 執行階段應用程式從這個類別。 針對非 Windows 執行階段應用程式，工作接續的執行內容會是取決於執行階段，而且不可設定。  
  
## <a name="syntax"></a>語法  
  
```
class task_continuation_context : public details::_ContextCallback;
```  
  
## <a name="members"></a>成員  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|描述|  
|----------|-----------------|  
|[get_current_winrt_context](#get_current_winrt_context)|傳回代表目前的 winrt 執行緒內容的工作接續內容物件。|  
|[use_arbitrary](#use_arbitrary)|建立可讓執行階段選擇接續執行內容的工作接續內容。|  
|[use_current](#use_current)|傳回表示目前執行內容的工作接續內容物件。|  
|[use_default](#use_default)|建立預設工作接續內容。|  
|[use_synchronous_execution](#use_synchronous_execution)|傳回表示同步執行內容的工作接續內容物件。|  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 `_ContextCallback`  
  
 `task_continuation_context`  
  
## <a name="requirements"></a>需求  
 **標頭：** ppltasks.h  
  
 **命名空間：** concurrency  

## <a name="get_current_winrt_context"></a> get_current_winrt_context
 傳回代表目前的 WinRT 執行緒內容的工作接續內容物件。  
  
## <a name="syntax"></a>語法  
  
```  
static task_continuation_context get_current_winrt_context();  
```  
  
## <a name="return-value"></a>傳回值  
 目前的 Windows 執行階段執行緒內容。 如果從非 Windows 執行階段內容中呼叫會傳回空的 task_continuation_context。  
  
## <a name="remarks"></a>備註  
 `get_current_winrt_context`方法會擷取呼叫端的 Windows 執行階段執行緒內容。 非 Windows 執行階段呼叫端，它就會傳回空的內容。  
  
 所傳回的值`get_current_winrt_context`可以用來向執行階段，執行接續 apartment 模型中的擷取的內容 (STA vs MTA)，不論前項工作是感知的 apartment。 注意工作是解除包裝 Windows 執行階段的工作 apartment`IAsyncInfo`介面或從這類工作繼承而來的工作。  
  
 這個方法是類似於`use_current`方法，但它也會提供原生 c + + 程式碼沒有 C + + /CX 延伸模組支援。 它適用於供進階使用者撰寫 C + + /CX 無從驗證原生和 Windows 執行階段呼叫端的程式庫程式碼。 除非您需要這項功能，我們建議`use_current`方法，才可以使用 C + /CX 用戶端。  
  
  
##  <a name="use_arbitrary"></a> use_arbitrary 

 建立可讓執行階段選擇接續執行內容的工作接續內容。  
  
```
static task_continuation_context use_arbitrary();
```  
  
### <a name="return-value"></a>傳回值  
 表示任意位置的工作接續內容。  
  
### <a name="remarks"></a>備註  
 使用此接續內容時將會執行階段會選擇即使前項工作為 apartment 注意內容中執行接續。  
  
 `use_arbitrary` 可用來關閉 建立在 STA apartment 知道工作的接續的預設行為  
  
 這個方法僅供 Windows 執行階段應用程式。  
  
##  <a name="use_current"></a> use_current 

 傳回表示目前執行內容的工作接續內容物件。  
  
```
static task_continuation_context use_current();
```  
  
### <a name="return-value"></a>傳回值  
 目前執行內容。  
  
### <a name="remarks"></a>備註  
 這個方法會擷取呼叫端的 Windows 執行階段內容，以便可以在右邊的 apartment 中執行接續。  
  
 所傳回的值`use_current`可以用來向執行階段，不論前項工作為 apartment 注意擷取的內容 (STA vs MTA) 在執行接續。 注意工作是解除包裝 Windows 執行階段的工作 apartment`IAsyncInfo`介面或從這類工作繼承而來的工作。  
  
 這個方法僅供 Windows 執行階段應用程式。  
  
##  <a name="use_default"></a> use_default 

 建立預設工作接續內容。  
  
```
static task_continuation_context use_default();
```  
  
### <a name="return-value"></a>傳回值  
 預設接續內容。  
  
### <a name="remarks"></a>備註  
 如果您不指定接續內容呼叫時使用的預設內容`then`方法。 在 Windows 應用程式中的，使用 Windows 7 和其下，以及桌面應用程式在 Windows 8 和更新版本，執行階段會決定執行的工作接續。 不過，在 Windows 執行階段應用程式 apartment 知道工作的接續的預設接續內容會在 apartment 其中`then`叫用。  
  
 注意工作是解除包裝 Windows 執行階段的工作 apartment`IAsyncInfo`介面或從這類工作繼承而來的工作。 因此，如果您排程在 Windows 執行階段 STA apartment 知道工作的接續，接續會執行在該 sta。  
  
 非 apartment 知道工作的接續會在執行階段會選擇的內容中執行。  

## <a name="use_synchronous_execution"></a> task_continuation_context::use_synchronous_execution  
傳回表示同步執行內容的工作接續內容物件。  
  
## <a name="syntax"></a>語法  
  
```  
static task_continuation_context use_synchronous_execution();  
```  
  
## <a name="return-value"></a>傳回值  
 同步執行內容。  
  
## <a name="remarks"></a>備註  
 `use_synchronous_execution`方法會強制執行以同步方式上的內容，導致其前項工作完成接續工作。  
  
 如果附加接續時前項工作已完成，接續將會在附加接續的內容以同步方式執行。  
  
 
## <a name="see-also"></a>請參閱  
 [concurrency 命名空間](concurrency-namespace.md)
