---
title: "task_continuation_context 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- ppltasks/concurrency::task_continuation_context
dev_langs:
- C++
helpviewer_keywords:
- task_continuation_context class
ms.assetid: 1fb5a76a-3682-45c2-a615-8b6b527741f0
caps.latest.revision: 15
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Machine Translation
ms.sourcegitcommit: fc190feb08d9b221cd1cc21a9c91ad567c86c848
ms.openlocfilehash: 627c2adc60c143ef7cd9be62f71a4365eed5aed5
ms.lasthandoff: 02/24/2017

---
# <a name="taskcontinuationcontext-class"></a>task_continuation_context 類別
`task_continuation_context` 類別可讓您指定要執行接續的位置。 只有從 Windows 市集應用程式使用這個類別才有用。 對於非 Windows 市集應用程式，工作接續的執行內容取決於執行階段，而且不可設定。  
  
## <a name="syntax"></a>語法  
  
```
class task_continuation_context : public details::_ContextCallback;
```  
  
## <a name="members"></a>Members  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|說明|  
|----------|-----------------|  
|[get_current_winrt_context 方法](#get_current_winrt_context)|傳回代表目前的 winrt 執行緒內容的工作接續內容物件。|  
|[use_arbitrary 方法](#use_arbitrary)|建立可讓執行階段選擇接續執行內容的工作接續內容。|  
|[use_current 方法](#use_current)|傳回表示目前執行內容的工作接續內容物件。|  
|[use_default 方法](#use_default)|建立預設工作接續內容。|  
|[use_synchronous_execution 方法](#use_synchronous_execution)|傳回表示同步執行內容的工作接續內容物件。|  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 `_ContextCallback`  
  
 `task_continuation_context`  
  
## <a name="requirements"></a>需求  
 **標頭︰** ppltasks.h  
  
 **命名空間：** concurrency  

## <a name="a-namegetcurrentwinrtcontexta-getcurrentwinrtcontext"></a><a name="get_current_winrt_context"></a>get_current_winrt_context
 傳回代表目前的 WinRT 執行緒內容的工作接續內容物件。  
  
## <a name="syntax"></a>語法  
  
```  
static task_continuation_context get_current_winrt_context();  
```  
  
## <a name="return-value"></a>傳回值  
 目前的 Windows 執行階段執行緒內容。 如果從非 Windows 執行階段內容呼叫會傳回空的 task_continuation_context。  
  
## <a name="remarks"></a>備註  
 `get_current_winrt_context`方法會擷取呼叫端的 Windows 執行階段的執行緒內容。 它會傳回空的內容給非 Windows 執行階段呼叫者。  
  
 所傳回的值`get_current_winrt_context`可以用來向執行階段，執行接續公寓模型中的擷取內容 (STA vs MTA)，而不論前項工作是否 apartment 注意。 瞭解工作是解除包裝 Windows 執行階段的工作 apartment`IAsyncInfo`介面或從這類工作繼承而來的工作。  
  
 這個方法很類似`use_current`方法，但它也會提供原生 c + + 程式碼，而不需要 C + + /cli CX 延伸支援。 它適用於使用進階使用者撰寫 C + + /cli CX 無從原生和 Windows 執行階段呼叫端的程式庫程式碼。 除非您需要這項功能，我們建議`use_current`方法，只會提供給 C + + /cli CX 用戶端。  
  
  
##  <a name="a-nameusearbitrarya-usearbitrary"></a><a name="use_arbitrary"></a>use_arbitrary 

 建立可讓執行階段選擇接續執行內容的工作接續內容。  
  
```
static task_continuation_context use_arbitrary();
```  
  
### <a name="return-value"></a>傳回值  
 代表任意位置的工作接續內容。  
  
### <a name="remarks"></a>備註  
 當使用這個接續內容接續會執行在執行階段會選擇即使前項工作為 apartment 感知的內容中。  
  
 `use_arbitrary`可以用來關閉 建立在 STA apartment 知道工作的接續的預設行為  
  
 這個方法只適用於 Windows 市集應用程式。  
  
##  <a name="a-nameusecurrenta-usecurrent"></a><a name="use_current"></a>use_current 

 傳回表示目前執行內容的工作接續內容物件。  
  
```
static task_continuation_context use_current();
```  
  
### <a name="return-value"></a>傳回值  
 目前執行內容。  
  
### <a name="remarks"></a>備註  
 這個方法會擷取呼叫端的 Windows 執行階段內容，以便可以正確 apartment 中執行接續。  
  
 所傳回的值`use_current`可以用來向執行階段，不論前項工作是否為 apartment 注意擷取的內容 (STA vs MTA) 中執行的接續。 瞭解工作是解除包裝 Windows 執行階段的工作 apartment`IAsyncInfo`介面或從這類工作繼承而來的工作。  
  
 這個方法只適用於 Windows 市集應用程式。  
  
##  <a name="a-nameusedefaulta-usedefault"></a><a name="use_default"></a>use_default 

 建立預設工作接續內容。  
  
```
static task_continuation_context use_default();
```  
  
### <a name="return-value"></a>傳回值  
 預設接續內容。  
  
### <a name="remarks"></a>備註  
 如果您不指定接續內容呼叫時使用的預設內容`then`方法。 在 Windows 應用程式的 Windows 7 及之前的版本，以及桌面應用程式在 Windows 8 和更新版本，執行階段會決定執行的工作接續。 不過，在 Windows 市集應用程式 apartment 知道工作的接續的預設接續內容是在 apartment 其中`then`叫用。  
  
 瞭解工作是解除包裝 Windows 執行階段的工作 apartment`IAsyncInfo`介面或從這類工作繼承而來的工作。 因此，如果您排程在 Windows 執行階段 STA apartment 知道工作的接續，接續會執行在該 sta。  
  
 在執行階段會選擇的內容中，將會執行非 apartment 知道工作的接續。  

## <a name="a-nameusesynchronousexecutiona-taskcontinuationcontextusesynchronousexecution"></a><a name="use_synchronous_execution"></a>task_continuation_context::use_synchronous_execution  
傳回表示同步執行內容的工作接續內容物件。  
  
## <a name="syntax"></a>語法  
  
```  
static task_continuation_context use_synchronous_execution();  
```  
  
## <a name="return-value"></a>傳回值  
 同步執行內容。  
  
## <a name="remarks"></a>備註  
 `use_synchronous_execution`方法會強制執行同步的內容，使其前項工作完成接續工作。  
  
 如果附加接續時前項工作已完成，接續會同步執行接續工作會將附加的內容。  
  
 
## <a name="see-also"></a>另請參閱  
 [concurrency 命名空間](concurrency-namespace.md)

