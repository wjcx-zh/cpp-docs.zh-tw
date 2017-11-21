`task_group`類別表示可以等候或取消平行工作的集合。  
  
## <a name="syntax"></a>語法  
  
```  
class task_group;  
```  
  
## <a name="members"></a>Members  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|說明|  
|----------|-----------------|  
|[task_group](#ctor)|多載。 建構新`task_group`物件。|  
|[~ task_group 解構函式](#dtor)|終結 `task_group` 物件。 您應該呼叫`wait`或`run_and_wait`解構函式在執行之前，除非解構函式執行而導致堆疊回溯，因為發生例外狀況物件上的方法。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|說明|  
|----------|-----------------|  
|[[取消]](#cancel)|會盡力嘗試取消子樹狀結構的根項目在這個工作群組的工作。 在工作群組上排程每項工作，將取得取消可轉移的的話。|  
|[is_canceling](#is_canceling)|通知呼叫端工作群組是目前在取消作業。 這不一定會指出，`cancel`上呼叫方法`task_group`物件 (例如確實符合此方法以傳回雖然`true`)。 可能的情況下，`task_group`物件以內嵌方式執行，而工作群組進一步設定工作樹狀結構中被取消。 在這些位置等情況下，執行階段可以判斷事先取消將通過這`task_group`物件`true`也會傳回。|  
|[run](#run)|多載。 排程的工作上`task_group`物件。 如果`task_handle`物件傳遞為參數，以`run`，呼叫端必須負責管理的存留期`task_handle`物件。 會將函式物件的參考，當做參數包含堆積配置，這可能在執行階段內方法之版本的執行效能比使用至參考的版本不佳`task_handle`物件。 採用 `_Placement` 參數的版本會造成工作在該參數指定的位置變成優先執行。|  
|[run_and_wait](#run_and_wait)|多載。 排程工作將被呼叫端內容上執行內嵌的協助`task_group`完整取消支援的物件。 函式接著會等候直到所有的工作`task_group`物件已完成或已取消。 如果`task_handle`物件傳遞為參數，以`run_and_wait`，呼叫端必須負責管理的存留期`task_handle`物件。|  
|[等候](#wait)|等待所有工作`task_group`物件已完成或已取消。|  
  
## <a name="remarks"></a>備註  
 不同於嚴重限制`structured_task_group`類別`task_group`類別是建構應用範圍更為廣泛。 它沒有任何所描述的限制[structured_task_group](structured-task-group-class.md)。 `task_group`物件可能安全地使用多個執行緒和自由格式的方式中加以使用。 缺點`task_group`建構是它可能無法執行，以及`structured_task_group`建構執行少量工作的工作。  
  
 如需詳細資訊，請參閱[工作平行處理原則](../task-parallelism-concurrency-runtime.md)。  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 `task_group`  
  
## <a name="requirements"></a>需求  
 **標頭：** ppl.h  
  
 **命名空間：** concurrency  
  
##  <a name="cancel"></a>[取消] 

 會盡力嘗試取消子樹狀結構的根項目在這個工作群組的工作。 在工作群組上排程每項工作，將取得取消可轉移的的話。  
  
```  
void cancel();  
```  
  
### <a name="remarks"></a>備註  
 如需詳細資訊，請參閱[取消](../cancellation-in-the-ppl.md)。  
  
##  <a name="is_canceling"></a>is_canceling 

 通知呼叫端工作群組是目前在取消作業。 這不一定會指出，`cancel`上呼叫方法`task_group`物件 (例如確實符合此方法以傳回雖然`true`)。 可能的情況下，`task_group`物件以內嵌方式執行，而工作群組進一步設定工作樹狀結構中被取消。 在這些位置等情況下，執行階段可以判斷事先取消將通過這`task_group`物件`true`也會傳回。  
  
```  
bool is_canceling();  
```  
  
### <a name="return-value"></a>傳回值  
 表示是否`task_group`物件正取消 （或一定會儘速）。  
  
### <a name="remarks"></a>備註  
 如需詳細資訊，請參閱[取消](../cancellation-in-the-ppl.md)。  
  
##  <a name="run"></a>執行 

 排程的工作上`task_group`物件。 如果`task_handle`物件傳遞為參數，以`run`，呼叫端必須負責管理的存留期`task_handle`物件。 會將函式物件的參考，當做參數包含堆積配置，這可能在執行階段內方法之版本的執行效能比使用至參考的版本不佳`task_handle`物件。 採用 `_Placement` 參數的版本會造成工作在該參數指定的位置變成優先執行。  
  
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
 若要執行的工作控制代碼的主體將會叫用的函式物件類型。  
  
 `_Func`  
 函式來叫用工作的主體時呼叫。 這可能是 lambda 運算式或其他物件的支援版本的函式呼叫運算子與簽章`void operator()()`。  
  
 `_Placement`  
 位置的參考，這是 `_Func` 參數代表的工作應該執行的位置。  
  
 `_Task_handle`  
 這排程的工作控制代碼。 請注意，呼叫端負責此物件的存留期。 執行階段仍要進行即時直到`wait`或`run_and_wait`上呼叫方法`task_group`物件。  
  
### <a name="remarks"></a>備註  
 執行階段排程在稍後的時間，可能會在呼叫函式會傳回執行中所提供的工作函式。 這個方法會使用[task_handle](task-handle-class.md)物件來保存一份所提供的工作函式。 因此，您傳遞給這個方法的函式物件中發生的任何狀態變更不會出現該函式物件的複本中。 此外，請確定您的指標或參考工作函式傳遞任何物件的存留期保持有效，直到工作函式傳回。  
  
 如果`task_group`destructs 堆疊回溯例外狀況的結果，您不需要保證的呼叫或`wait`或`run_and_wait`方法。 在此情況下，解構函式會適當地取消，並等候工作所代表`_Task_handle`參數來完成。  
  
 方法會擲回[invalid_multiple_scheduling](invalid-multiple-scheduling-class.md)例外狀況，如果工作處理給定`_Task_handle`到工作群組物件，透過已排程參數`run`方法和已沒有中間呼叫為`wait`或`run_and_wait`該工作群組上的方法。  
  
##  <a name="run_and_wait"></a>run_and_wait 

 排程工作將被呼叫端內容上執行內嵌的協助`task_group`完整取消支援的物件。 函式接著會等候直到所有的工作`task_group`物件已完成或已取消。 如果`task_handle`物件傳遞為參數，以`run_and_wait`，呼叫端必須負責管理的存留期`task_handle`物件。  
  
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
 呼叫端內容將會執行內嵌工作控制代碼。 請注意，呼叫端負責此物件的存留期。 執行階段仍要進行即時直到`run_and_wait`方法完成執行。  
  
 `_Func`  
 函式呼叫來叫用工作主體。 這可能是 lambda 運算式或其他物件的支援版本的函式呼叫運算子與簽章`void operator()()`。  
  
### <a name="return-value"></a>傳回值  
 表示是否已滿足等候或工作群組已取消，因為明確的取消作業或從其中一個其工作所擲回例外狀況。 如需詳細資訊，請參閱[task_group_status](concurrency-namespace-enums.md#task_group_status)。  

  
### <a name="remarks"></a>備註  
 請注意，一部或多個至此已排程的工作`task_group`物件可能會內嵌執行呼叫端內容上。  
  
 如果一或多個至此已排程的工作`task_group`物件擲回例外狀況，執行階段會選取其選擇的一個這類例外狀況，並傳播超出呼叫`run_and_wait`方法。  
  
 傳回從時`run_and_wait`方法`task_group`物件，執行階段重設為可重複使用的初始狀態的物件。 這包含案例，其中`task_group`物件已取消。  
  
 在非例外狀況的執行路徑中，您有呼叫可能是這個方法的託管或`wait`方法之前的解構函式`task_group`執行。  
  
##  <a name="ctor"></a>task_group 

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
  
##  <a name="dtor"></a>~ task_group 

 終結 `task_group` 物件。 您應該呼叫`wait`或`run_and_wait`解構函式在執行之前，除非解構函式執行而導致堆疊回溯，因為發生例外狀況物件上的方法。  
  
```  
~task_group();  
```  
  
### <a name="remarks"></a>備註  
 如果解構函式執行結果的一般執行 （例如，沒有堆疊回溯因為發生例外狀況） 而且`wait`也`run_and_wait`已呼叫方法、 解構函式可能會擲回[missing_wait](missing-wait-class.md)例外狀況。  
  
##  <a name="wait"></a>等候 

 等待所有工作`task_group`物件已完成或已取消。  
  
```  
task_group_status wait();  
```  
  
### <a name="return-value"></a>傳回值  
 表示是否已滿足等候或工作群組已取消，因為明確的取消作業或從其中一個其工作所擲回例外狀況。 如需詳細資訊，請參閱[task_group_status](concurrency-namespace-enums.md#task_group_status)。  

  
### <a name="remarks"></a>備註  
 請注意，一部或多個至此已排程的工作`task_group`物件可能會內嵌執行呼叫端內容上。  
  
 如果一或多個至此已排程的工作`task_group`物件擲回例外狀況，執行階段會選取其選擇的一個這類例外狀況，並傳播超出呼叫`wait`方法。  
  
 呼叫`wait`上`task_group`物件將它重設為可重複使用的初始狀態。 這包含案例，其中`task_group`物件已取消。  
  
 在非例外狀況的執行路徑中，您有呼叫可能是這個方法的託管或`run_and_wait`方法之前的解構函式`task_group`執行。  
  
## <a name="see-also"></a>另請參閱  
 [concurrency 命名空間](concurrency-namespace.md)   
 [structured_task_group 類別](structured-task-group-class.md)   
 [task_handle 類別](task-handle-class.md)