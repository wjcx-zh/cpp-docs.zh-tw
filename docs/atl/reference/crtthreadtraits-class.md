---
title: "CRTThreadTraits 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CRTThreadTraits
- ATLBASE/ATL::CRTThreadTraits
- ATLBASE/ATL::CRTThreadTraits::CreateThread
dev_langs: C++
helpviewer_keywords:
- CRTThreadTraits class
- threading [ATL], creation functions
- threading [ATL], CRT threads
ms.assetid: eb6e20b0-c2aa-4170-8e34-aaeeacc86343
caps.latest.revision: "21"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: d6fbe71ff23db8dba431b9d46d71fc6c924fbc5e
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="crtthreadtraits-class"></a>CRTThreadTraits 類別
這個類別會提供 CRT 執行緒建立函式。 如果執行緒會使用 CRT 函式，請使用這個類別。  
  
> [!IMPORTANT]
>  這個類別及其成員不能在 Windows 執行階段中執行的應用程式。  
  
## <a name="syntax"></a>語法  
  
```
class CRTThreadTraits
```  
  
## <a name="members"></a>成員  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|描述|  
|----------|-----------------|  
|[CRTThreadTraits::CreateThread](#createthread)|（靜態）呼叫此函式可建立的執行緒，可以使用 CRT 函式。|  
  
## <a name="remarks"></a>備註  
 執行緒特性是執行緒的提供特定類型建立函式的類別。 建立函式有相同的簽章和語意與 Windows [CreateThread](http://msdn.microsoft.com/library/windows/desktop/ms682453)函式。  
  
 下列類別會使用執行緒特性：  
  
- [CThreadPool](../../atl/reference/cthreadpool-class.md)  
  
- [CWorkerThread](../../atl/reference/cworkerthread-class.md)  
  
 如果執行緒將不會使用 CRT 函式，使用[Win32ThreadTraits](../../atl/reference/win32threadtraits-class.md)改為。  
  
## <a name="requirements"></a>需求  
 **標頭：** atlbase.h  
  
##  <a name="createthread"></a>CRTThreadTraits::CreateThread  
 呼叫此函式可建立的執行緒，可以使用 CRT 函式。  
  
```
static HANDLE CreateThread(
    LPSECURITY_ATTRIBUTES lpsa,
    DWORD dwStackSize,
    LPTHREAD_START_ROUTINE pfnThreadProc,
    void* pvParam,
    DWORD dwCreationFlags,
    DWORD* pdwThreadId) throw();
```  
  
### <a name="parameters"></a>參數  
 `lpsa`  
 新的執行緒安全性屬性。  
  
 `dwStackSize`  
 新執行緒的堆疊大小。  
  
 `pfnThreadProc`  
 新執行緒的執行緒程序。  
  
 `pvParam`  
 要傳遞給執行緒的程序的參數。  
  
 `dwCreationFlags`  
 建立旗標 （0 或 CREATE_SUSPENDED）。  
  
 `pdwThreadId`  
 [out]DWORD 變數的成功時，接收新建立執行緒的執行緒 ID 的位址。  
  
### <a name="return-value"></a>傳回值  
 傳回新建立的執行緒或 NULL 的控制代碼失敗。 呼叫[GetLastError](http://msdn.microsoft.com/library/windows/desktop/ms679360)若要取得延伸錯誤資訊。  
  
### <a name="remarks"></a>備註  
 請參閱[CreateThread](http://msdn.microsoft.com/library/windows/desktop/ms682453)更多有關這個函式的參數。  
  
 此函數會呼叫[_beginthreadex](../../c-runtime-library/reference/beginthread-beginthreadex.md)建立執行緒。  
  
## <a name="see-also"></a>請參閱  
 [類別概觀](../../atl/atl-class-overview.md)
