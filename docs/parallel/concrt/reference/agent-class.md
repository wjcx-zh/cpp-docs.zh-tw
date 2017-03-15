---
title: "agent 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- agents/concurrency::agent
dev_langs:
- C++
helpviewer_keywords:
- agent class
ms.assetid: 1b09e3d2-5e37-4966-b016-907ef1512456
caps.latest.revision: 20
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
ms.openlocfilehash: 640e1d66a879e8eb73428b50339d6a325cfd7cb2
ms.lasthandoff: 02/24/2017

---
# <a name="agent-class"></a>agent 類別
適合做為所有獨立代理程式之基底類別的類別。 它用來對其他代理程式隱藏狀態，並使用訊息傳遞互動。  
  
## <a name="syntax"></a>語法  
  
```
class agent;
```  
  
## <a name="members"></a>Members  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|描述|  
|----------|-----------------|  
|[代理程式的建構函式](#ctor)|多載。 建構代理程式。|  
|[~ agent 解構函式](#dtor)|終結代理程式。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|描述|  
|----------|-----------------|  
|[cancel 方法](#cancel)|將代理程式從`agent_created`或`agent_runnable`狀態至`agent_canceled`狀態。|  
|[start 方法](#start)|將代理程式從`agent_created`狀態`agent_runnable`狀態，以及排程執行。|  
|[狀態方法](#status)|從代理程式的狀態資訊的來源同步。|  
|[status_port 方法](#status_port)|從代理程式的狀態資訊的非同步來源。|  
|[wait 方法](#wait)|等候代理程式，以完成其工作。|  
|[wait_for_all 方法](#wait_for_all)|等候所有指定的代理程式，以完成其工作。|  
|[wait_for_one 方法](#wait_for_one)|等候任何一個指定的代理程式，以完成其工作。|  
  
### <a name="protected-methods"></a>受保護的方法  
  
|名稱|描述|  
|----------|-----------------|  
|[done 的方法](#done)|移至代理程式`agent_done`狀態，表示代理程式已完成。|  
|[run 方法](#run)|表示代理程式的主要工作。 `run`在衍生類別中，則必須覆寫，並指定應該執行的代理程式已經啟動。|  
  
## <a name="remarks"></a>備註  
 如需詳細資訊，請參閱[非同步代理程式](../../../parallel/concrt/asynchronous-agents.md)。  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 `agent`  
  
## <a name="requirements"></a>需求  
 **標頭：** agents.h  
  
 **命名空間：** concurrency  
  
##  <a name="a-namectora-agent"></a><a name="ctor"></a>代理程式 

 建構代理程式。  
  
```
agent();

agent(Scheduler& _PScheduler);

agent(ScheduleGroup& _PGroup);
```  
  
### <a name="parameters"></a>參數  
 `_PScheduler`  
 `Scheduler`物件內的 「 代理程式 」 執行工作排程。  
  
 `_PGroup`  
 `ScheduleGroup`物件內的 「 代理程式 」 執行工作排程。 所使用的 `Scheduler` 物件由排程群組所隱含。  
  
### <a name="remarks"></a>備註  
 如果您未指定執行階段會使用預設排程器`_PScheduler`或`_PGroup`參數。  
  
##  <a name="a-namedtora-agent"></a><a name="dtor"></a>~ 代理程式 

 終結代理程式。  
  
```
virtual ~agent();
```  
  
### <a name="remarks"></a>備註  
 它會摧毀不在終止狀態的代理程式發生錯誤 (可能是`agent_done`或`agent_canceled`)。 這可避免等候代理程式才會到達終止狀態的解構函式中的類別繼承自`agent`類別。  
  
##  <a name="a-namecancela-cancel"></a><a name="cancel"></a>[取消] 

 將代理程式從`agent_created`或`agent_runnable`狀態至`agent_canceled`狀態。  
  
```
bool cancel();
```  
  
### <a name="return-value"></a>傳回值  
 `true`如果代理程式已取消，則`false`否則。 代理程式無法取消，如果它已經開始執行或已完成。  
  
##  <a name="a-namedonea-done"></a><a name="done"></a>完成 

 移至代理程式`agent_done`狀態，表示代理程式已完成。  
  
```
bool done();
```  
  
### <a name="return-value"></a>傳回值  
 `true`如果代理程式移至`agent_done`狀態，`false`否則。 已取消的代理程式無法移到`agent_done`狀態。  
  
### <a name="remarks"></a>備註  
 這個方法應該呼叫的結尾`run`方法，當您知道您的代理程式的執行已完成。  
  
##  <a name="a-nameruna-run"></a><a name="run"></a>執行 

 表示代理程式的主要工作。 `run`在衍生類別中，則必須覆寫，並指定應該執行的代理程式已經啟動。  
  
```
virtual void run() = 0;
```  
  
### <a name="remarks"></a>備註  
 代理程式狀態變更為`agent_started`叫用這個方法之前，以滑鼠右鍵。 這個方法應該叫用`done`與適當的狀態後再傳回，代理程式上，且可能擲回任何例外狀況。  
  
##  <a name="a-namestarta-start"></a><a name="start"></a>啟動 

 將代理程式從`agent_created`狀態`agent_runnable`狀態，以及排程執行。  
  
```
bool start();
```  
  
### <a name="return-value"></a>傳回值  
 `true`如果代理程式正確地啟動`false`否則。 已取消的代理程式無法啟動。  
  
##  <a name="a-namestatusa-status"></a><a name="status"></a>狀態 

 從代理程式的狀態資訊的來源同步。  
  
```
agent_status status();
```  
  
### <a name="return-value"></a>傳回值  
 傳回目前狀態的代理程式。 請注意，傳回的狀態無法變更之後立即傳回。  
  
##  <a name="a-namestatusporta-statusport"></a><a name="status_port"></a>status_port 

 從代理程式的狀態資訊的非同步來源。  
  
```
ISource<agent_status>* status_port();
```  
  
### <a name="return-value"></a>傳回值  
 傳回可將代理程式的目前狀態相關的訊息傳送的訊息來源。  
  
##  <a name="a-namewaita-wait"></a><a name="wait"></a>等候 

 等候代理程式，以完成其工作。  
  
```
static agent_status __cdecl wait(
    _Inout_ agent* _PAgent,
    unsigned int _Timeout = COOPERATIVE_TIMEOUT_INFINITE);
```  
  
### <a name="parameters"></a>參數  
 `_PAgent`  
 代理程式所等待的指標。  
  
 `_Timeout`  
 要等待，以毫秒為單位的時間上限。  
  
### <a name="return-value"></a>傳回值  
 `agent_status`等候完成時的代理程式。 這可以是`agent_canceled`或`agent_done`。  
  
### <a name="remarks"></a>備註  
 代理程式工作完成時，代理程式會進入`agent_canceled`或`agent_done`狀態。  
  
 如果參數`_Timeout`常數以外的值`COOPERATIVE_TIMEOUT_INFINITE`，例外狀況[operation_timed_out](operation-timed-out-class.md)如果代理程式已完成其工作之前，已經超過指定的時間量，會擲回。  
  
##  <a name="a-namewaitforalla-waitforall"></a><a name="wait_for_all"></a>wait_for_all 

 等候所有指定的代理程式，以完成其工作。  
  
```
static void __cdecl wait_for_all(
    size_t count,
    _In_reads_(count) agent** _PAgents,
    _Out_writes_opt_(count) agent_status* _PStatus = NULL,
    unsigned int _Timeout = COOPERATIVE_TIMEOUT_INFINITE);
```  
  
### <a name="parameters"></a>參數  
 `count`  
 代理程式出現在陣列的指標的數目`_PAgents`。  
  
 `_PAgents`  
 等候代理程式的指標陣列。  
  
 `_PStatus`  
 代理程式狀態的陣列指標。 每個狀態值方法傳回時，將代表對應的代理程式的狀態。  
  
 `_Timeout`  
 要等待，以毫秒為單位的時間上限。  
  
### <a name="remarks"></a>備註  
 代理程式工作完成時，代理程式會進入`agent_canceled`或`agent_done`狀態。  
  
 如果參數`_Timeout`常數以外的值`COOPERATIVE_TIMEOUT_INFINITE`，例外狀況[operation_timed_out](operation-timed-out-class.md)如果代理程式已完成其工作之前，已經超過指定的時間量，會擲回。  
  
##  <a name="a-namewaitforonea-waitforone"></a><a name="wait_for_one"></a>wait_for_one 

 等候任何一個指定的代理程式，以完成其工作。  
  
```
static void __cdecl wait_for_one(
    size_t count,
    _In_reads_(count) agent** _PAgents,
    agent_status& _Status,
    size_t& _Index,
    unsigned int _Timeout = COOPERATIVE_TIMEOUT_INFINITE);
```  
  
### <a name="parameters"></a>參數  
 `count`  
 代理程式出現在陣列的指標的數目`_PAgents`。  
  
 `_PAgents`  
 等候代理程式的指標陣列。  
  
 `_Status`  
 放置代理程式狀態變數的參考。  
  
 `_Index`  
 代理程式索引放置變數的參考。  
  
 `_Timeout`  
 要等待，以毫秒為單位的時間上限。  
  
### <a name="remarks"></a>備註  
 代理程式工作完成時，代理程式會進入`agent_canceled`或`agent_done`狀態。  
  
 如果參數`_Timeout`常數以外的值`COOPERATIVE_TIMEOUT_INFINITE`，例外狀況[operation_timed_out](operation-timed-out-class.md)如果代理程式已完成其工作之前，已經超過指定的時間量，會擲回。  
  
## <a name="see-also"></a>另請參閱  
 [concurrency 命名空間](concurrency-namespace.md)

