---
title: structured_task_group 類別 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-concrt
ms.topic: reference
f1_keywords:
- structured_task_group
- PPL/concurrency::structured_task_group
- PPL/concurrency::structured_task_group::structured_task_group
- PPL/concurrency::structured_task_group::cancel
- PPL/concurrency::structured_task_group::is_canceling
- PPL/concurrency::structured_task_group::run
- PPL/concurrency::structured_task_group::run_and_wait
- PPL/concurrency::structured_task_group::wait
dev_langs:
- C++
helpviewer_keywords:
- structured_task_group class
ms.assetid: 742afa8c-c7b6-482c-b0ba-04c809927b22
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 5cca5d20b89df97e27529d656e9a6553fd8a1820
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/07/2018
ms.locfileid: "33694140"
---
# <a name="structuredtaskgroup-class"></a>structured_task_group 類別
`structured_task_group` 類別代表平行工作的高度結構化集合。 您可以使用 `task_handle` 物件，將個別平行工作佇列到 `structured_task_group` 中並等候這些工作完成，也可以在工作完成執行前取消工作群組，這樣會中止所有尚未開始執行的工作。  
  
## <a name="syntax"></a>語法  
  
```
class structured_task_group;
```  
  
## <a name="members"></a>成員  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|描述|  
|----------|-----------------|  
|[structured_task_group](#ctor)|多載。 建構新`structured_task_group`物件。|  
|[~ structured_task_group 解構函式](#dtor)|終結 `structured_task_group` 物件。 您應該呼叫`wait`或`run_and_wait`解構函式執行之前物件上的方法，除非執行解構函式的堆疊回溯，因為發生例外狀況。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|描述|  
|----------|-----------------|  
|[[取消]](#cancel)|會盡力嘗試取消子樹狀結構的根項目在這個工作群組的工作。 在工作群組上排程每項工作，將取得取消可轉移的的話。|  
|[is_canceling](#is_canceling)|通知呼叫端工作群組是目前在取消作業。 這不一定會指出，`cancel`上呼叫方法`structured_task_group`物件 (例如確實符合此方法以傳回雖然`true`)。 可能的情況下，`structured_task_group`物件以內嵌方式執行，而工作群組進一步設定工作樹狀結構中被取消。 在這些位置等情況下，執行階段可以判斷事先取消將通過這`structured_task_group`物件`true`也會傳回。|  
|[run](#run)|多載。 排程的工作上`structured_task_group`物件。 呼叫端負責管理`task_handle`物件傳入`_Task_handle`參數。 採用 `_Placement` 參數的版本會造成工作在該參數指定的位置變成優先執行。|  
|[run_and_wait](#run_and_wait)|多載。 排程工作將被呼叫端內容上執行內嵌的協助`structured_task_group`完整取消支援的物件。 如果`task_handle`物件傳遞為參數，以`run_and_wait`，呼叫端必須負責管理的存留期`task_handle`物件。 函式接著會等候直到所有的工作`structured_task_group`物件已完成或已取消。|  
|[等候](#wait)|等待所有工作`structured_task_group`已完成或取消。|  
  
## <a name="remarks"></a>備註  
 有許多的使用方式的嚴重限制`structured_task_group`才能取得效能物件：  
  
-   單一`structured_task_group`物件無法供多個執行緒。 上的所有作業`structured_task_group`物件必須由建立物件的執行緒執行。 此規則的兩個例外狀況是成員函式`cancel`和`is_canceling`。 物件可能無法在 lambda 運算式的擷取清單中，除非工作使用其中一個取消作業，可用於工作。  
  
-   所有排定工作，`structured_task_group`物件會透過使用的排程`task_handle`物件，您必須明確地管理的存留期。  
  
-   多個群組只用於絕對巢狀順序。 如果兩個`structured_task_group`宣告物件、 第二個宣告 （內部的那一個） 必須解構以外的任何方法之前`cancel`或`is_canceling`呼叫第一個 （外部一）。 此條件成立的只將宣告多個案例中，則為 true`structured_task_group`物件內的相同或功能的巢狀範圍，以及工作已排入佇列的大小寫`structured_task_group`透過`run`或`run_and_wait`方法。  
  
-   不同於一般`task_group`類別中的所有狀態`structured_task_group`都類別是最後一個。 您將工作佇列至群組並等候工作完成之後，就不能再使用同一個群組。  
  
 如需詳細資訊，請參閱[工作平行處理原則](../../../parallel/concrt/task-parallelism-concurrency-runtime.md)。  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 `structured_task_group`  
  
## <a name="requirements"></a>需求  
 **標頭：** ppl.h  
  
 **命名空間：** concurrency  
  
##  <a name="cancel"></a> [取消] 

 會盡力嘗試取消子樹狀結構的根項目在這個工作群組的工作。 在工作群組上排程每項工作，將取得取消可轉移的的話。  
  
```
void cancel();
```  
  
### <a name="remarks"></a>備註  
 如需詳細資訊，請參閱[取消](../../../parallel/concrt/exception-handling-in-the-concurrency-runtime.md#cancellation)。  
  
##  <a name="is_canceling"></a> is_canceling 

 通知呼叫端工作群組是目前在取消作業。 這不一定會指出，`cancel`上呼叫方法`structured_task_group`物件 (例如確實符合此方法以傳回雖然`true`)。 可能的情況下，`structured_task_group`物件以內嵌方式執行，而工作群組進一步設定工作樹狀結構中被取消。 在這些位置等情況下，執行階段可以判斷事先取消將通過這`structured_task_group`物件`true`也會傳回。  
  
```
bool is_canceling();
```  
  
### <a name="return-value"></a>傳回值  
 表示是否`structured_task_group`物件正取消 （或一定會儘速）。  
  
### <a name="remarks"></a>備註  
 如需詳細資訊，請參閱[取消](../../../parallel/concrt/exception-handling-in-the-concurrency-runtime.md#cancellation)。  
  
##  <a name="run"></a> 執行 

 排程的工作上`structured_task_group`物件。 呼叫端負責管理`task_handle`物件傳入`_Task_handle`參數。 採用 `_Placement` 參數的版本會造成工作在該參數指定的位置變成優先執行。  
  
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
 若要執行的工作控制代碼的主體將會叫用的函式物件類型。  
  
 `_Task_handle`  
 這排程的工作控制代碼。 請注意，呼叫端負責此物件的存留期。 執行階段仍要進行即時直到`wait`或`run_and_wait`上呼叫方法`structured_task_group`物件。  
  
 `_Placement`  
 位置的參考，這是 `_Task_handle` 參數代表的工作應該執行的位置。  
  
### <a name="remarks"></a>備註  
 執行階段建立一份工作函式傳遞給這個方法。 您傳遞給這個方法的函式物件中發生的任何狀態變更不會出現在您的函式物件的複本。  
  
 如果`structured_task_group`destructs 堆疊回溯例外狀況的結果，您不需要保證的呼叫或`wait`或`run_and_wait`方法。 在此情況下，解構函式會適當地取消，並等候工作所代表`_Task_handle`參數來完成。  
  
 擲回[invalid_multiple_scheduling](invalid-multiple-scheduling-class.md)例外狀況，如果工作處理給定`_Task_handle`到工作群組物件，透過已排程參數`run`方法，且已沒有中間呼叫可能是`wait`或`run_and_wait`該工作群組上的方法。  
  
##  <a name="run_and_wait"></a> run_and_wait 

 排程工作將被呼叫端內容上執行內嵌的協助`structured_task_group`完整取消支援的物件。 如果`task_handle`物件傳遞為參數，以`run_and_wait`，呼叫端必須負責管理的存留期`task_handle`物件。 函式接著會等候直到所有的工作`structured_task_group`物件已完成或已取消。  
  
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
 呼叫端內容將會執行內嵌工作控制代碼。 請注意，呼叫端負責此物件的存留期。 執行階段仍要進行即時直到`run_and_wait`方法完成執行。  
  
 `_Func`  
 函式呼叫來叫用工作主體。 這可能是 lambda 或其他物件的支援版本的函式呼叫運算子與簽章`void operator()()`。  
  
### <a name="return-value"></a>傳回值  
 表示是否已滿足等候或工作群組已取消，因為明確的取消作業或從其中一個其工作所擲回例外狀況。 如需詳細資訊，請參閱[task_group_status](concurrency-namespace-enums.md)  
  
### <a name="remarks"></a>備註  
 請注意，一部或多個至此已排程的工作`structured_task_group`物件可能會內嵌執行呼叫端內容上。  
  
 如果一或多個至此已排程的工作`structured_task_group`物件擲回例外狀況，執行階段會選取其選擇的一個這類例外狀況，並傳播超出呼叫`run_and_wait`方法。  
  
 這個函式傳回後，就會將 `structured_task_group` 物件視為處於最終狀態而且不應使用。 請注意該之後的使用量`run_and_wait`方法會傳回將會導致未定義的行為。  
  
 在非例外狀況的執行路徑中，您有呼叫可能是這個方法的託管或`wait`方法之前的解構函式`structured_task_group`執行。  
  
##  <a name="ctor"></a> structured_task_group 

 建構新`structured_task_group`物件。  
  
```
structured_task_group();

structured_task_group(cancellation_token _CancellationToken);
```  
  
### <a name="parameters"></a>參數  
 `_CancellationToken`  
 取消語彙基元給與此結構化的工作群組產生關聯。 當取消語彙基元，則會取消結構化的工作群組。  
  
### <a name="remarks"></a>備註  
 使用取消語彙基元的建構函式會建立 `structured_task_group`，當與語彙基元相關聯的來源取消時，它也會一併取消。 提供明確的取消語彙基元也會隔離從父群組具有不同語彙基元或沒有語彙基元的隱含取消加入這個結構化的工作群組。  
  
##  <a name="dtor"></a> ~structured_task_group 

 終結 `structured_task_group` 物件。 您應該呼叫`wait`或`run_and_wait`解構函式執行之前物件上的方法，除非執行解構函式的堆疊回溯，因為發生例外狀況。  
  
```
~structured_task_group();
```  
  
### <a name="remarks"></a>備註  
 如果解構函式執行結果的一般執行 （例如，沒有堆疊回溯因為發生例外狀況） 而且`wait`也`run_and_wait`已呼叫方法、 解構函式可能會擲回[missing_wait](missing-wait-class.md)例外狀況。  
  
##  <a name="wait"></a> 等候 

 等待所有工作`structured_task_group`已完成或取消。  
  
```
task_group_status wait();
```  
  
### <a name="return-value"></a>傳回值  
 表示是否已滿足等候或工作群組已取消，因為明確的取消作業或從其中一個其工作所擲回例外狀況。 如需詳細資訊，請參閱[task_group_status](concurrency-namespace-enums.md)  
  
### <a name="remarks"></a>備註  
 請注意，一部或多個至此已排程的工作`structured_task_group`物件可能會內嵌執行呼叫端內容上。  
  
 如果一或多個至此已排程的工作`structured_task_group`物件擲回例外狀況，執行階段會選取其選擇的一個這類例外狀況，並傳播超出呼叫`wait`方法。  
  
 這個函式傳回後，就會將 `structured_task_group` 物件視為處於最終狀態而且不應使用。 請注意該之後的使用量`wait`方法會傳回將會導致未定義的行為。  
  
 在非例外狀況的執行路徑中，您有呼叫可能是這個方法的託管或`run_and_wait`方法之前的解構函式`structured_task_group`執行。  
  
## <a name="see-also"></a>另請參閱  
 [concurrency 命名空間](concurrency-namespace.md)   
 [task_group 類別](task-group-class.md)   
 [task_handle 類別](task-handle-class.md)
