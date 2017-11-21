---
title: "DispatchState 結構 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- DispatchState
- CONCRTRM/concurrency::DispatchState
- CONCRTRM/concurrency::DispatchState::DispatchState::DispatchState
- CONCRTRM/concurrency::DispatchState::DispatchState::m_dispatchStateSize
- CONCRTRM/concurrency::DispatchState::DispatchState::m_fIsPreviousContextAsynchronouslyBlocked
- CONCRTRM/concurrency::DispatchState::DispatchState::m_reserved
dev_langs: C++
helpviewer_keywords: DispatchState structure
ms.assetid: 8c52546e-1650-48a0-985f-7e4a0fc26a90
caps.latest.revision: "17"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: a6997596876f080ea00611af90d05eb4fddd2857
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/24/2017
---
# <a name="dispatchstate-structure"></a>DispatchState 結構
`DispatchState` 結構用來將狀態傳輸至 `IExecutionContext::Dispatch` 方法。 它描述在 `IExecutionContext` 介面上叫用 `Dispatch` 方法的情況。  
  
## <a name="syntax"></a>語法  
  
```
struct DispatchState;
```  
  
## <a name="members"></a>Members  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|說明|  
|----------|-----------------|  
|[Dispatchstate:: Dispatchstate](#ctor)|建構新`DispatchState`物件。|  
  
### <a name="public-data-members"></a>公用資料成員  
  
|名稱|說明|  
|----------|-----------------|  
|[Dispatchstate:: M_dispatchstatesize](#m_dispatchstatesize)|此結構中，用來進行版本控制的大小。|  
|[Dispatchstate:: M_fispreviouscontextasynchronouslyblocked](#m_fispreviouscontextasynchronouslyblocked)|指示此內容是否已進入`Dispatch`方法因為先前的內容以非同步方式封鎖。 這只適用於 UMS 排程內容，並設定為值`0`之所有其他執行內容。|  
|[Dispatchstate:: M_reserved](#m_reserved)|保留供未來資訊傳遞時，位元。|  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 `DispatchState`  
  
## <a name="requirements"></a>需求  
 **標頭：** concrtrm.h  
  
 **命名空間：** concurrency  
  
##  <a name="ctor"></a>Dispatchstate:: Dispatchstate 建構函式  
 建構新`DispatchState`物件。  
  
```
DispatchState();
```  
  
##  <a name="m_dispatchstatesize"></a>Dispatchstate:: M_dispatchstatesize 資料成員  
 此結構中，用來進行版本控制的大小。  
  
```
unsigned long m_dispatchStateSize;
```  
  
##  <a name="m_fispreviouscontextasynchronouslyblocked"></a>Dispatchstate:: M_fispreviouscontextasynchronouslyblocked 資料成員  
 指示此內容是否已進入`Dispatch`方法因為先前的內容以非同步方式封鎖。 這只適用於 UMS 排程內容，並設定為值`0`之所有其他執行內容。  
  
```
unsigned int m_fIsPreviousContextAsynchronouslyBlocked : 1;
```  
  
##  <a name="m_reserved"></a>Dispatchstate:: M_reserved 資料成員  
 保留供未來資訊傳遞時，位元。  
  
```
unsigned int m_reserved : 31;
```  
  
## <a name="see-also"></a>另請參閱  
 [concurrency 命名空間](concurrency-namespace.md)
