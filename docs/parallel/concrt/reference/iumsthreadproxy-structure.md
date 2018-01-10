---
title: "IUMSThreadProxy 結構 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IUMSThreadProxy
- CONCRTRM/concurrency::IUMSThreadProxy
- CONCRTRM/concurrency::IUMSThreadProxy::IUMSThreadProxy::EnterCriticalRegion
- CONCRTRM/concurrency::IUMSThreadProxy::IUMSThreadProxy::EnterHyperCriticalRegion
- CONCRTRM/concurrency::IUMSThreadProxy::IUMSThreadProxy::ExitCriticalRegion
- CONCRTRM/concurrency::IUMSThreadProxy::IUMSThreadProxy::ExitHyperCriticalRegion
- CONCRTRM/concurrency::IUMSThreadProxy::IUMSThreadProxy::GetCriticalRegionType
dev_langs: C++
helpviewer_keywords: IUMSThreadProxy structure
ms.assetid: 61c69b7e-5c37-4048-bcb4-e75c536afd86
caps.latest.revision: "19"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: d9d9b200db84ddbf25e514e1432fa0915d5ee383
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="iumsthreadproxy-structure"></a>IUMSThreadProxy 結構
執行緒的抽象概念。 如果您想要將可使用者模式排程 (UMS) 的執行緒授與給排程器，請將排程器原則項目 `SchedulerKind` 的值設為 `UmsThreadDefault`，並實作 `IUMSScheduler` 介面。 只有安裝 Windows 7 (含以上) 版本的 64 位元作業系統支援 UMS 執行緒。  
  
## <a name="syntax"></a>語法  
  
```
struct IUMSThreadProxy : public IThreadProxy;
```  
  
## <a name="members"></a>成員  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|描述|  
|----------|-----------------|  
|[Iumsthreadproxy:: Entercriticalregion](#entercriticalregion)|呼叫以輸入關鍵區域。 在關鍵區域中，內部排程器不會發現在區域中發生的非同步封鎖作業。 這表示，排程器將不會因為重新進入分頁錯誤、 執行緒暫止、 核心非同步程序呼叫 （apc） 等和其他等等，UMS 執行緒。|  
|[Iumsthreadproxy:: Enterhypercriticalregion](#enterhypercriticalregion)|呼叫以輸入超關鍵區域。 在 hyper-v 關鍵的區域中，內部排程器不會發現在區域中發生任何封鎖作業。 這表示不會因為 UMS 執行緒的封鎖函式呼叫、鎖定封鎖的擷取嘗試、分頁錯誤、執行緒暫止、核心非同步程序呼叫 (APC) 等，而重新進入排程器。|  
|[Iumsthreadproxy:: Exitcriticalregion](#exitcriticalregion)|呼叫以結束關鍵區域。|  
|[Iumsthreadproxy:: Exithypercriticalregion](#exithypercriticalregion)|呼叫以結束 hyper-v 關鍵區域。|  
|[Iumsthreadproxy:: Getcriticalregiontype](#getcriticalregiontype)|傳回何種執行緒 proxy 是中的關鍵區域。 因為 hyper-v 關鍵區域是關鍵的區域的超集，如果程式碼已進入關鍵區域，然後 hyper-v 關鍵區域，`InsideHyperCriticalRegion`會傳回。|  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 [IThreadProxy](ithreadproxy-structure.md)  
  
 `IUMSThreadProxy`  
  
## <a name="requirements"></a>需求  
 **標頭：** concrtrm.h  
  
 **命名空間：** concurrency  
  
##  <a name="entercriticalregion"></a>Iumsthreadproxy:: Entercriticalregion 方法  
 呼叫以輸入關鍵區域。 在關鍵區域中，內部排程器不會發現在區域中發生的非同步封鎖作業。 這表示，排程器將不會因為重新進入分頁錯誤、 執行緒暫止、 核心非同步程序呼叫 （apc） 等和其他等等，UMS 執行緒。  
  
```
virtual int EnterCriticalRegion() = 0;
```  
  
### <a name="return-value"></a>傳回值  
 關鍵區域的新的深度。 重要的區域是可重新進入。  
  
##  <a name="enterhypercriticalregion"></a>Iumsthreadproxy:: Enterhypercriticalregion 方法  
 呼叫以輸入超關鍵區域。 在 hyper-v 關鍵的區域中，內部排程器不會發現在區域中發生任何封鎖作業。 這表示不會因為 UMS 執行緒的封鎖函式呼叫、鎖定封鎖的擷取嘗試、分頁錯誤、執行緒暫止、核心非同步程序呼叫 (APC) 等，而重新進入排程器。  
  
```
virtual int EnterHyperCriticalRegion() = 0;
```  
  
### <a name="return-value"></a>傳回值  
 新 hyper-v 關鍵區域的深度。 Hyper-v 關鍵區域是可重新進入。  
  
### <a name="remarks"></a>備註  
 排程器必須小心 hierarchy 其所呼叫的方法和它鎖定取得這種區域中，項目。 如果由項目排程器會負責排程持有的鎖定封鎖了這種區域中的程式碼，可能會發生死結。  
  
##  <a name="exitcriticalregion"></a>Iumsthreadproxy:: Exitcriticalregion 方法  
 呼叫以結束關鍵區域。  
  
```
virtual int ExitCriticalRegion() = 0;
```  
  
### <a name="return-value"></a>傳回值  
 關鍵區域的新的深度。 重要的區域是可重新進入。  
  
##  <a name="exithypercriticalregion"></a>Iumsthreadproxy:: Exithypercriticalregion 方法  
 呼叫以結束 hyper-v 關鍵區域。  
  
```
virtual int ExitHyperCriticalRegion() = 0;
```  
  
### <a name="return-value"></a>傳回值  
 新 hyper-v 關鍵區域的深度。 Hyper-v 關鍵區域是可重新進入。  
  
##  <a name="getcriticalregiontype"></a>Iumsthreadproxy:: Getcriticalregiontype 方法  
 傳回何種執行緒 proxy 是中的關鍵區域。 因為 hyper-v 關鍵區域是關鍵的區域的超集，如果程式碼已進入關鍵區域，然後 hyper-v 關鍵區域，`InsideHyperCriticalRegion`會傳回。  
  
```
virtual CriticalRegionType GetCriticalRegionType() const = 0;
```  
  
### <a name="return-value"></a>傳回值  
 執行緒 proxy 是中的重要區域的類型。  
  
## <a name="see-also"></a>請參閱  
 [concurrency 命名空間](concurrency-namespace.md)   
 [IUMSScheduler 結構](iumsscheduler-structure.md)
