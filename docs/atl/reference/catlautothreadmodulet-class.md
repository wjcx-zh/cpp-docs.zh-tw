---
title: "CAtlAutoThreadModuleT Class | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "ATL.CAtlAutoThreadModuleT"
  - "ATL::CAtlAutoThreadModuleT"
  - "CAtlAutoThreadModuleT"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CAtlAutoThreadModuleT class"
ms.assetid: ae1667c6-3fb8-47bc-b35d-9ea5e9896d7f
caps.latest.revision: 20
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CAtlAutoThreadModuleT Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

這個類別會實作執行緒集區提供了方法， Apartment Model COM 伺服器。  
  
> [!IMPORTANT]
>  這個類別和其成員不能用於 Windows 執行階段執行的應用程式。  
  
## 語法  
  
```  
  
      template <  
class T,  
class ThreadAllocator= CComSimpleThreadAllocator,  
DWORD dwWait= INFINITE   
>  
class ATL_NO_VTABLE CAtlAutoThreadModuleT :  
public IAtlAutoThreadModule  
```  
  
#### 參數  
 `T`  
 會實作 COM 伺服器的類別。  
  
 `ThreadAllocator`  
 類別會管理執行緒的選取範圍。  預設值為 [CComSimpleThreadAllocator](../../atl/reference/ccomsimplethreadallocator-class.md)。  
  
 `dwWait`  
 指定以毫秒為單位的逾時間隔，。  預設值為 Infinite，表示方法的逾時間隔絕對不會耗用。  
  
## Members  
  
### 公用方法  
  
|名稱|描述|  
|--------|--------|  
|[CAtlAutoThreadModuleT::GetDefaultThreads](../Topic/CAtlAutoThreadModuleT::GetDefaultThreads.md)|這個靜態函式以處理序的數目會動態計算並傳回執行緒的最大數目 EXE 模組的。|  
  
## 備註  
 類別 [CAtlAutoThreadModule](../../atl/reference/catlautothreadmodule-class.md)`CAtlAutoThreadModuleT` 從衍生來實作執行緒集區， Apartment Model COM 伺服器。  它會取代過時的類別 [CComAutoThreadModule](../../atl/reference/ccomautothreadmodule-class.md)。  
  
> [!NOTE]
>  這個類別不應該用於 DLL，，因為預設 `dwWait` 值的無限可能會導致死結，當卸載 DLL 時。  
  
## 繼承階層架構  
 `IAtlAutoThreadModule`  
  
 `CAtlAutoThreadModuleT`  
  
## 需求  
 **Header:** atlbase.h  
  
## 請參閱  
 [IAtlAutoThreadModule Class](../../atl/reference/iatlautothreadmodule-class.md)   
 [Class Overview](../../atl/atl-class-overview.md)   
 [IAtlAutoThreadModule Class](../../atl/reference/iatlautothreadmodule-class.md)   
 [模組類別](../../atl/atl-module-classes.md)