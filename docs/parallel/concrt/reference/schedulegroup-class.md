---
title: "ScheduleGroup 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- ScheduleGroup
- CONCRT/concurrency::ScheduleGroup
- CONCRT/concurrency::ScheduleGroup::Id
- CONCRT/concurrency::ScheduleGroup::Reference
- CONCRT/concurrency::ScheduleGroup::Release
- CONCRT/concurrency::ScheduleGroup::ScheduleTask
dev_langs:
- C++
helpviewer_keywords:
- ScheduleGroup class
ms.assetid: 86d380ff-f2e8-411c-b1a8-22bd3079824a
caps.latest.revision: 20
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
ms.translationtype: Machine Translation
ms.sourcegitcommit: 5faef5bd1be6cc02d6614a6f6193c74167a8ff23
ms.openlocfilehash: dc7a78fd135d56e1243c43672172e433652e34e2
ms.contentlocale: zh-tw
ms.lasthandoff: 03/17/2017

---
# <a name="schedulegroup-class"></a>ScheduleGroup 類別
代表排程群組的抽象概念。 排程群組會將一組相關的工作組織在一起，以讓這些工作獲得暫時緊密排程在一起的優勢，其方法如下：透過在同一個群組中執行另一個工作再移至另一個群組；透過再同一個 NUMA 節點或實體通訊端的同一個群組內執行多個項目。  
  
## <a name="syntax"></a>語法  
  
```
class ScheduleGroup;
```  
  
## <a name="members"></a>Members  
  
### <a name="protected-constructors"></a>受保護的建構函式  
  
|名稱|描述|  
|----------|-----------------|  
|[~ ScheduleGroup 解構函式](#dtor)||  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|描述|  
|----------|-----------------|  
|[識別碼](#id)|傳回群組所屬的排程器內必須是唯一的排程群組的識別碼。|  
|[參考](#reference)|遞增排程器群組的參考計數。|  
|[發行](#release)|遞減排程器群組的參考計數。|  
|[ScheduleTask](#scheduletask)|排程的排程群組中的輕量工作。|  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 `ScheduleGroup`  
  
## <a name="requirements"></a>需求  
 **標頭︰** concrt.h  
  
 **命名空間：** concurrency  
  
##  <a name="id"></a>識別碼 

 傳回群組所屬的排程器內必須是唯一的排程群組的識別碼。  
  
```
virtual unsigned int Id() const = 0;
```  
  
### <a name="return-value"></a>傳回值  
 排程群組的群組所屬的排程器內是唯一的識別項。  
  
##  <a name="operator_delete"></a>delete 運算子 

 A`ScheduleGroup`終結物件內部執行階段時已釋放所有外部參考它。 它不可明確刪除。  
  
```
void operator delete(
    void* _PObject);

void operator delete(
    void* _PObject,
    int,
 const char *,
    int);
```    
  
### <a name="parameters"></a>參數  
 `_PObject`  
 要刪除物件的指標。  
  
##  <a name="reference"></a>參考 

 遞增排程器群組的參考計數。  
  
```
virtual unsigned int Reference() = 0;
```  
  
### <a name="return-value"></a>傳回值  
 新遞增的參考計數。  
  
### <a name="remarks"></a>備註  
 這通常用來管理排程群組組合的存留期。 排程群組的參考次數降為零，當執行階段會刪除排程群組。 建立使用排程群組[currentscheduler:: Createschedulegroup](currentscheduler-class.md#createschedulegroup)方法，或[scheduler:: createschedulegroup](scheduler-class.md#createschedulegroup)方法開頭的其中一個參考計數。  
  
##  <a name="release"></a>發行 

 遞減排程器群組的參考計數。  
  
```
virtual unsigned int Release() = 0;
```  
  
### <a name="return-value"></a>傳回值  
 新遞減參考計數。  
  
### <a name="remarks"></a>備註  
 這通常用來管理排程群組組合的存留期。 排程群組的參考次數降為零，當執行階段會刪除排程群組。 在您呼叫 `Release` 方法特定次數以移除建立參考計數和任何使用 `Reference` 方法所進行的參考後，就不能進一步利用排程群組。 這樣會導致未定義的行為。  
  
 排程群組是特定的排程器執行個體相關聯。 您必須先確定已釋放排程群組的所有參考，才能釋放排程器的所有參考，因為後者可能會使排程器遭到終結。 執行其他原因導致未定義的行為。  
  
##  <a name="dtor"></a>~ ScheduleGroup 

```
virtual ~ScheduleGroup();
```  
  
##  <a name="scheduletask"></a>ScheduleTask 

 排程的排程群組中的輕量工作。  
  
```
virtual void ScheduleTask(
    TaskProc _Proc,
    _Inout_opt_ void* _Data) = 0;
```  
  
### <a name="parameters"></a>參數  
 `_Proc`  
 若要執行的輕量工作主體執行的函式指標。  
  
 `_Data`  
 Void 指標會做為參數傳遞至工作主體的資料。  
  
### <a name="remarks"></a>備註  
 呼叫`ScheduleTask`隱含的參考計數上放置在適當的時間執行工作後執行階段會移除排程群組。  
  
## <a name="see-also"></a>另請參閱  
 [concurrency 命名空間](concurrency-namespace.md)   
 [CurrentScheduler 類別](currentscheduler-class.md)   
 [Scheduler 類別](scheduler-class.md)   
 [工作排程器](../../../parallel/concrt/task-scheduler-concurrency-runtime.md)




