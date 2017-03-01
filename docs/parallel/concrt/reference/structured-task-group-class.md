---
title: "structured_task_group 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- ppl/concurrency::structured_task_group
dev_langs:
- C++
helpviewer_keywords:
- structured_task_group class
ms.assetid: 742afa8c-c7b6-482c-b0ba-04c809927b22
caps.latest.revision: 21
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: fc190feb08d9b221cd1cc21a9c91ad567c86c848
ms.openlocfilehash: ef20ff7fef8683cec4a3856c80c09846aa69a89a
ms.lasthandoff: 02/24/2017

---
# <a name="structuredtaskgroup-class"></a>structured_task_group 類別
`structured_task_group` 類別代表平行工作的高度結構化集合。 您可以使用 `task_handle` 物件，將個別平行工作佇列到 `structured_task_group` 中並等候這些工作完成，也可以在工作完成執行前取消工作群組，這樣會中止所有尚未開始執行的工作。  
  
## <a name="syntax"></a>語法  
  
```
class structured_task_group;
```  
  
## <a name="members"></a>Members  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|描述|  
|----------|-----------------|  
|[structured_task_group 建構函式](#ctor)|多載。 建構新`structured_task_group`物件。|  
|[~ structured_task_group 解構函式](#dtor)|終結 `structured_task_group` 物件。 您應該呼叫`wait`或`run_and_wait`物件解構函式執行之前的方法，除非執行解構函式可能是堆疊回溯，因為例外狀況。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|描述|  
|----------|-----------------|  
|[cancel 方法](#cancel)|會盡力嘗試取消工作，這個工作群組為根目錄的子樹狀結構。 排定的工作群組上的每項工作將會取得取消間接的話。|  
|[is_canceling 方法](#is_canceling)|通知呼叫端工作群組是目前在取消作業。 這不一定表示，`cancel`上呼叫方法`structured_task_group`物件 (雖然這類確實符合此方法以傳回`true`)。 它可能是因為，`structured_task_group`物件正在執行內嵌和工作群組，進一步設定工作樹狀結構中已取消。 例如這些位置的情況下，執行階段可以判斷事先取消作業將會流經此`structured_task_group`物件，`true`也會傳回。|  
|[run 方法](#run)|多載。 排程的工作上`structured_task_group`物件。 呼叫端管理的存留期間`task_handle`物件傳入`_Task_handle`參數。 採用 `_Placement` 參數的版本會造成工作在該參數指定的位置變成優先執行。|  
|[run_and_wait 方法](#run_and_wait)|多載。 排程的工作上呼叫的內容要執行的內嵌的協助`structured_task_group`完整取消支援的物件。 如果`task_handle`物件做為參數傳遞`run_and_wait`，呼叫端會負責管理的存留期`task_handle`物件。 函式接著會等候直到所有處理`structured_task_group`物件已完成或已取消。|  
|[wait 方法](#wait)|等候所有處理`structured_task_group`已完成或取消。|  
  
## <a name="remarks"></a>備註  
 有嚴重的使用方式的限制數目`structured_task_group`才能獲得的效能物件︰  
  
-   單一`structured_task_group`物件無法供多個執行緒。 上的所有作業`structured_task_group`物件只能由建立物件的執行緒。 此規則的兩個例外狀況是成員函式`cancel`和`is_canceling`。 物件可能無法在 lambda 運算式的擷取清單中，除非工作使用其中一個取消作業，可用於工作。  
  
-   所有排定的工作`structured_task_group`物件透過使用的排程`task_handle`物件，您必須明確管理的存留期。  
  
-   多個群組只能用於絕對巢狀順序。 如果有兩個`structured_task_group`宣告物件，第二個宣告 （內部的那一個） 必須解構以外的任何方法之前`cancel`或`is_canceling`上第一個呼叫 （外部的那一個）。 在這兩個案例中的只將宣告多個這種情況成立`structured_task_group`物件內的相同或功能的巢狀範圍，以及工作已排入佇列的大小寫`structured_task_group`透過`run`或`run_and_wait`方法。  
  
-   不同於一般`task_group`類別中的所有狀態`structured_task_group`都類別是最後一個。 您將工作佇列至群組並等候工作完成之後，就不能再使用同一個群組。  
  
 如需詳細資訊，請參閱[工作平行處理原則](../../../parallel/concrt/task-parallelism-concurrency-runtime.md)。  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 `structured_task_group`  
  
## <a name="requirements"></a>需求  
 **標頭︰** ppl.h  
  
 **命名空間：** concurrency  
  
##  <a name="a-namecancela-cancel"></a><a name="cancel"></a>[取消] 

 會盡力嘗試取消工作，這個工作群組為根目錄的子樹狀結構。 排定的工作群組上的每項工作將會取得取消間接的話。  
  
```
void cancel();
```  
  
### <a name="remarks"></a>備註  
 如需詳細資訊，請參閱[取消](../../../parallel/concrt/exception-handling-in-the-concurrency-runtime.md#cancellation)。  
  
##  <a name="a-nameiscancelinga-iscanceling"></a><a name="is_canceling"></a>is_canceling 

 通知呼叫端工作群組是目前在取消作業。 這不一定表示，`cancel`上呼叫方法`structured_task_group`物件 (雖然這類確實符合此方法以傳回`true`)。 它可能是因為，`structured_task_group`物件正在執行內嵌和工作群組，進一步設定工作樹狀結構中已取消。 例如這些位置的情況下，執行階段可以判斷事先取消作業將會流經此`structured_task_group`物件，`true`也會傳回。  
  
```
bool is_canceling();
```  
  
### <a name="return-value"></a>傳回值  
 表示是否`structured_task_group`物件是在取消 （或一定會在短時間內）。  
  
### <a name="remarks"></a>備註  
 如需詳細資訊，請參閱[取消](../../../parallel/concrt/exception-handling-in-the-concurrency-runtime.md#cancellation)。  
  
##  <a name="a-nameruna-run"></a><a name="run"></a>執行 

 排程的工作上`structured_task_group`物件。 呼叫端管理的存留期間`task_handle`物件傳入`_Task_handle`參數。 採用 `_Placement` 參數的版本會造成工作在該參數指定的位置變成優先執行。  
  
```
template<class _Function>
void run(
    task_handle<_Function>& _Task_handle);

template<class _Function>
void run(
    task_handle<_Function>& _Task_handle,
    location& _Placement);
```  
  
### <a name="parameters"></a>參數  
 `_Function`  
 若要執行的工作控制代碼的主體就會叫用的函式物件類型。  
  
 `_Task_handle`  
 這排程的工作控制代碼。 請注意，呼叫端負責此物件的存留期。 執行階段會繼續直到存留預期`wait`或`run_and_wait`呼叫這個方法`structured_task_group`物件。  
  
 `_Placement`  
 位置的參考，這是 `_Task_handle` 參數代表的工作應該執行的位置。  
  
### <a name="remarks"></a>備註  
 執行階段會建立一份工作函式，傳遞給這個方法。 傳遞給這個方法的函式物件中發生的任何狀態變更不會出現該函式物件的複本中。  
  
 如果`structured_task_group`destructs 堆疊回溯例外狀況的結果，您不需要保證，呼叫為`wait`或`run_and_wait`方法。 在此情況下，解構函式會適當地取消並且等候工作由`_Task_handle`參數來完成。  
  
 擲回[invalid_multiple_scheduling](invalid-multiple-scheduling-class.md)如果工作處理的例外狀況提供`_Task_handle`到透過工作群組物件的參數已排定`run`方法已經沒有介入呼叫`wait`或`run_and_wait`該工作群組上的方法。  
  
##  <a name="a-namerunandwaita-runandwait"></a><a name="run_and_wait"></a>run_and_wait 

 排程的工作上呼叫的內容要執行的內嵌的協助`structured_task_group`完整取消支援的物件。 如果`task_handle`物件做為參數傳遞`run_and_wait`，呼叫端會負責管理的存留期`task_handle`物件。 函式接著會等候直到所有處理`structured_task_group`物件已完成或已取消。  
  
```
template<class _Function>
task_group_status run_and_wait(task_handle<_Function>& _Task_handle);

template<class _Function>
task_group_status run_and_wait(const _Function& _Func);
```  
  
### <a name="parameters"></a>參數  
 `_Function`  
 將要叫用以執行工作的函式物件類型。  
  
 `_Task_handle`  
 控制代碼呼叫的內容將會執行內嵌工作。 請注意，呼叫端負責此物件的存留期。 執行階段會繼續存留預期`run_and_wait`方法完成執行。  
  
 `_Func`  
 函式來叫用的工作內容時呼叫。 這可能是 lambda 或其他物件支援的版本與簽章的函式呼叫運算子`void operator()()`。  
  
### <a name="return-value"></a>傳回值  
 表示是否滿意等待結果或工作群組已取消，因為明確取消作業或從某個工作擲回例外狀況。 如需詳細資訊，請參閱[task_group_status](concurrency-namespace-enums.md)  
  
### <a name="remarks"></a>備註  
 請注意，其中一個或多個此排程的工作`structured_task_group`物件可能會執行內嵌上呼叫的內容。  
  
 如果一或多個排定的工作至此`structured_task_group`物件就會擲回例外狀況、 執行階段會選取其選擇的一個這類例外狀況，並將它散佈到呼叫`run_and_wait`方法。  
  
 這個函式傳回後，就會將 `structured_task_group` 物件視為處於最終狀態而且不應使用。 請注意該之後的使用量`run_and_wait`方法會傳回將會導致未定義的行為。  
  
 在非例外狀況的執行路徑中，您有呼叫這個方法的託管或`wait`方法的解構函式之前`structured_task_group`執行。  
  
##  <a name="a-namectora-structuredtaskgroup"></a><a name="ctor"></a>structured_task_group 

 建構新`structured_task_group`物件。  
  
```
structured_task_group();

structured_task_group(cancellation_token _CancellationToken);
```  
  
### <a name="parameters"></a>參數  
 `_CancellationToken`  
 與此結構化的工作群組相關聯的取消語彙基元。 取消語彙基元時，將會取消結構化的工作群組。  
  
### <a name="remarks"></a>備註  
 使用取消語彙基元的建構函式會建立 `structured_task_group`，當與語彙基元相關聯的來源取消時，它也會一併取消。 提供明確的取消語彙基元也會隔離無法參與具有不同的語彙基元或沒有語彙基元之父群組的隱含取消此結構化的工作群組。  
  
##  <a name="a-namedtora-structuredtaskgroup"></a><a name="dtor"></a>~ structured_task_group 

 終結 `structured_task_group` 物件。 您應該呼叫`wait`或`run_and_wait`物件解構函式執行之前的方法，除非執行解構函式可能是堆疊回溯，因為例外狀況。  
  
```
~structured_task_group();
```  
  
### <a name="remarks"></a>備註  
 如果解構函式而執行的一般執行 （例如，沒有堆疊回溯，因為例外狀況） 而且`wait`或`run_and_wait`方法呼叫、 解構函式可能會擲回[missing_wait](missing-wait-class.md)例外狀況。  
  
##  <a name="a-namewaita-wait"></a><a name="wait"></a>等候 

 等候所有處理`structured_task_group`已完成或取消。  
  
```
task_group_status wait();
```  
  
### <a name="return-value"></a>傳回值  
 表示是否滿意等待結果或工作群組已取消，因為明確取消作業或從某個工作擲回例外狀況。 如需詳細資訊，請參閱[task_group_status](concurrency-namespace-enums.md)  
  
### <a name="remarks"></a>備註  
 請注意，其中一個或多個此排程的工作`structured_task_group`物件可能會執行內嵌上呼叫的內容。  
  
 如果一或多個排定的工作至此`structured_task_group`物件就會擲回例外狀況、 執行階段會選取其選擇的一個這類例外狀況，並將它散佈到呼叫`wait`方法。  
  
 這個函式傳回後，就會將 `structured_task_group` 物件視為處於最終狀態而且不應使用。 請注意該之後的使用量`wait`方法會傳回將會導致未定義的行為。  
  
 在非例外狀況的執行路徑中，您有呼叫這個方法的託管或`run_and_wait`方法的解構函式之前`structured_task_group`執行。  
  
## <a name="see-also"></a>另請參閱  
 [concurrency 命名空間](concurrency-namespace.md)   
 [task_group 類別](task-group-class.md)   
 [task_handle 類別](task-handle-class.md)

