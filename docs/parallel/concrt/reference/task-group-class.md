`task_group`類別代表可在等候或取消平行工作的集合。  
  
## <a name="syntax"></a>語法  
  
```  
class task_group;  
```  
  
## <a name="members"></a>Members  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|說明|  
|----------|-----------------|  
|[task_group 建構函式](#ctor)|多載。 建構新`task_group`物件。|  
|[~ task_group 解構函式](#dtor)|終結 `task_group` 物件。 您應該呼叫`wait`或`run_and_wait`解構函式在執行之前，除非解構函式會執行堆疊回溯，因為例外狀況的結果物件的方法。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|描述|  
|----------|-----------------|  
|[cancel 方法](#cancel)|會盡力嘗試取消工作，這個工作群組為根目錄的子樹狀結構。 排定的工作群組上的每項工作將會取得取消間接的話。|  
|[is_canceling 方法](#is_canceling)|通知呼叫端工作群組是目前在取消作業。 這不一定表示，`cancel`上呼叫方法`task_group`物件 (雖然這類確實符合此方法以傳回`true`)。 它可能是因為，`task_group`物件正在執行內嵌和工作群組，進一步設定工作樹狀結構中已取消。 例如這些位置的情況下，執行階段可以判斷事先取消作業將會流經此`task_group`物件，`true`也會傳回。|  
|[run 方法](#run)|多載。 排程的工作上`task_group`物件。 如果`task_handle`物件做為參數傳遞`run`，呼叫端會負責管理的存留期`task_handle`物件。 版本的函式物件的參考當成參數包含堆積配置，它可能是在執行階段內的方法執行較少也比使用接受以參考的版本`task_handle`物件。 採用 `_Placement` 參數的版本會造成工作在該參數指定的位置變成優先執行。|  
|[run_and_wait 方法](#run_and_wait)|多載。 排程的工作上呼叫的內容要執行的內嵌的協助`task_group`完整取消支援的物件。 函式接著會等候直到所有處理`task_group`物件已完成或已取消。 如果`task_handle`物件做為參數傳遞`run_and_wait`，呼叫端會負責管理的存留期`task_handle`物件。|  
|[wait 方法](#wait)|等候所有處理`task_group`物件已完成或已取消。|  
  
## <a name="remarks"></a>備註  
 不同於高度限制`structured_task_group`類別，`task_group`類別是應用範圍更為廣泛的建構。 它沒有任何所描述的限制[structured_task_group](structured-task-group-class.md)。 `task_group`物件可能安全地使用多個執行緒和使用量過高的自由格式的方式。 缺點`task_group`建構是它可能無法執行，以及`structured_task_group`建構用來執行少量工作的工作。  
  
 如需詳細資訊，請參閱[工作平行處理原則](../task-parallelism-concurrency-runtime.md)。  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 `task_group`  
  
## <a name="requirements"></a>需求  
 **標頭︰** ppl.h  
  
 **命名空間：** concurrency  
  
##  <a name="a-namecancela-cancel"></a><a name="cancel"></a>[取消] 

 會盡力嘗試取消工作，這個工作群組為根目錄的子樹狀結構。 排定的工作群組上的每項工作將會取得取消間接的話。  
  
```  
void cancel();  
```  
  
### <a name="remarks"></a>備註  
 如需詳細資訊，請參閱[取消](../cancellation-in-the-ppl.md)。  
  
##  <a name="a-nameiscancelinga-iscanceling"></a><a name="is_canceling"></a>is_canceling 

 通知呼叫端工作群組是目前在取消作業。 這不一定表示，`cancel`上呼叫方法`task_group`物件 (雖然這類確實符合此方法以傳回`true`)。 它可能是因為，`task_group`物件正在執行內嵌和工作群組，進一步設定工作樹狀結構中已取消。 例如這些位置的情況下，執行階段可以判斷事先取消作業將會流經此`task_group`物件，`true`也會傳回。  
  
```  
bool is_canceling();  
```  
  
### <a name="return-value"></a>傳回值  
 表示是否`task_group`物件是在取消 （或一定會在短時間內）。  
  
### <a name="remarks"></a>備註  
 如需詳細資訊，請參閱[取消](../cancellation-in-the-ppl.md)。  
  
##  <a name="a-nameruna-run"></a><a name="run"></a>執行 

 排程的工作上`task_group`物件。 如果`task_handle`物件做為參數傳遞`run`，呼叫端會負責管理的存留期`task_handle`物件。 版本的函式物件的參考當成參數包含堆積配置，它可能是在執行階段內的方法執行較少也比使用接受以參考的版本`task_handle`物件。 採用 `_Placement` 參數的版本會造成工作在該參數指定的位置變成優先執行。  
  
```  
template<  
   typename _Function  
>  
void run(  
   const _Function& _Func  
);  
  
template<  
   typename _Function  
>  
void run(  
   const _Function& _Func,  
   location& _Placement  
);  
  
template<  
   typename _Function  
>  
void run(  
   task_handle<_Function>& _Task_handle  
);  
  
template<  
   typename _Function  
>  
void run(  
   task_handle<_Function>& _Task_handle,  
   location& _Placement  
);  
```  
  
### <a name="parameters"></a>參數  
 `_Function`  
 若要執行的工作控制代碼的主體就會叫用的函式物件類型。  
  
 `_Func`  
 要叫用工作主體所呼叫函式。 這可能是 lambda 運算式或其他物件支援的版本與簽章的函式呼叫運算子`void operator()()`。  
  
 `_Placement`  
 位置的參考，這是 `_Func` 參數代表的工作應該執行的位置。  
  
 `_Task_handle`  
 這排程的工作控制代碼。 請注意，呼叫端負責此物件的存留期。 執行階段會繼續直到存留預期`wait`或`run_and_wait`呼叫這個方法`task_group`物件。  
  
### <a name="remarks"></a>備註  
 執行階段排程提供更新的時間，可以呼叫的函式傳回之後執行的工作函式。 這個方法會使用[task_handle](task-handle-class.md)物件來保存一份提供工作函式。 因此，您傳遞給這個方法的函式物件中發生的任何狀態變更不會出現該函式物件的複本中。 此外，請確定您傳遞指標或參考的工作函式的任何物件的存留期保持有效，直到工作函式傳回。  
  
 如果`task_group`destructs 堆疊回溯例外狀況的結果，您不需要保證，呼叫為`wait`或`run_and_wait`方法。 在此情況下，解構函式會適當地取消並且等候工作由`_Task_handle`參數來完成。  
  
 方法會擲回[invalid_multiple_scheduling](invalid-multiple-scheduling-class.md)例外狀況，如果工作處理給定`_Task_handle`到透過工作群組物件的參數已排定`run`方法已經沒有介入呼叫`wait`或`run_and_wait`該工作群組上的方法。  
  
##  <a name="a-namerunandwaita-runandwait"></a><a name="run_and_wait"></a>run_and_wait 

 排程的工作上呼叫的內容要執行的內嵌的協助`task_group`完整取消支援的物件。 函式接著會等候直到所有處理`task_group`物件已完成或已取消。 如果`task_handle`物件做為參數傳遞`run_and_wait`，呼叫端會負責管理的存留期`task_handle`物件。  
  
```  
template<  
   class _Function  
>  
task_group_status run_and_wait(  
   task_handle<_Function>& _Task_handle  
);  
  
template<  
   class _Function  
>  
task_group_status run_and_wait(  
   const _Function& _Func  
);  
```  
  
### <a name="parameters"></a>參數  
 `_Function`  
 函式物件的類型，將會叫用它來執行工作主體。  
  
 `_Task_handle`  
 控制代碼呼叫的內容將會執行內嵌工作。 請注意，呼叫端負責此物件的存留期。 執行階段會繼續存留預期`run_and_wait`方法完成執行。  
  
 `_Func`  
 函式來叫用的工作內容時呼叫。 這可能是 lambda 運算式或其他物件支援的版本與簽章的函式呼叫運算子`void operator()()`。  
  
### <a name="return-value"></a>傳回值  
 表示是否滿意等待結果或工作群組已取消，因為明確取消作業或從某個工作擲回例外狀況。 如需詳細資訊，請參閱[task_group_status](concurrency-namespace-enums.md#task_group_status)。  

  
### <a name="remarks"></a>備註  
 請注意，其中一個或多個此排程的工作`task_group`物件可能會執行內嵌上呼叫的內容。  
  
 如果一或多個排定的工作至此`task_group`物件就會擲回例外狀況、 執行階段會選取其選擇的一個這類例外狀況，並將它散佈到呼叫`run_and_wait`方法。  
  
 傳回從時`run_and_wait`方法`task_group`物件時，執行階段重設為可重複使用的初始狀態的物件。 這包括在其中`task_group`物件已取消。  
  
 在非例外狀況的執行路徑中，您有呼叫這個方法的託管或`wait`方法的解構函式之前`task_group`執行。  
  
##  <a name="a-namectora-taskgroup"></a><a name="ctor"></a>task_group 

 建構新`task_group`物件。  
  
```  
task_group();  
  
task_group(  
   cancellation_token _CancellationToken  
);  
```  
  
### <a name="parameters"></a>參數  
 `_CancellationToken`  
 取消與這個工作群組相關聯的語彙基元。 取消語彙基元時，工作群組也會取消。  
  
### <a name="remarks"></a>備註  
 使用取消語彙基元的建構函式會建立 `task_group`，當與語彙基元相關聯的來源取消時，它也會一併取消。 提供明確的取消語彙基元也會將這個工作群組隔離，使其無法參與具有不同語彙基元或沒有語彙基元之父群組的隱含取消。  
  
##  <a name="a-namedtora-taskgroup"></a><a name="dtor"></a>~ task_group 

 終結 `task_group` 物件。 您應該呼叫`wait`或`run_and_wait`解構函式在執行之前，除非解構函式會執行堆疊回溯，因為例外狀況的結果物件的方法。  
  
```  
~task_group();  
```  
  
### <a name="remarks"></a>備註  
 如果解構函式而執行的一般執行 （例如，沒有堆疊回溯，因為例外狀況） 而且`wait`或`run_and_wait`方法呼叫、 解構函式可能會擲回[missing_wait](missing-wait-class.md)例外狀況。  
  
##  <a name="a-namewaita-wait"></a><a name="wait"></a>等候 

 等候所有處理`task_group`物件已完成或已取消。  
  
```  
task_group_status wait();  
```  
  
### <a name="return-value"></a>傳回值  
 表示是否滿意等待結果或工作群組已取消，因為明確取消作業或從某個工作擲回例外狀況。 如需詳細資訊，請參閱[task_group_status](concurrency-namespace-enums.md#task_group_status)。  

  
### <a name="remarks"></a>備註  
 請注意，其中一個或多個此排程的工作`task_group`物件可能會執行內嵌上呼叫的內容。  
  
 如果一或多個排定的工作至此`task_group`物件就會擲回例外狀況、 執行階段會選取其選擇的一個這類例外狀況，並將它散佈到呼叫`wait`方法。  
  
 呼叫`wait`上`task_group`物件將它重設為可重複使用的初始狀態。 這包括在其中`task_group`物件已取消。  
  
 在非例外狀況的執行路徑中，您有呼叫這個方法的託管或`run_and_wait`方法的解構函式之前`task_group`執行。  
  
## <a name="see-also"></a>另請參閱  
 [concurrency 命名空間](concurrency-namespace.md)   
 [structured_task_group 類別](structured-task-group-class.md)   
 [task_handle 類別](task-handle-class.md)