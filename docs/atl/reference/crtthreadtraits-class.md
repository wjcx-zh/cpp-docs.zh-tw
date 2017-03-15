---
title: "CRTThreadTraits 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- ATL::CRTThreadTraits
- ATL.CRTThreadTraits
- CRTThreadTraits
dev_langs:
- C++
helpviewer_keywords:
- CRTThreadTraits class
- threading [ATL], creation functions
- threading [ATL], CRT threads
ms.assetid: eb6e20b0-c2aa-4170-8e34-aaeeacc86343
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
ms.sourcegitcommit: 0e0c08ddc57d437c51872b5186ae3fc983bb0199
ms.openlocfilehash: 24cee5c74819d9a880bedbcebcce4dabfabae960
ms.lasthandoff: 02/24/2017

---
# <a name="crtthreadtraits-class"></a>CRTThreadTraits 類別
這個類別提供建立函數的 CRT 往來文章。 如果執行緒會使用 CRT 函式，請使用這個類別。  
  
> [!IMPORTANT]
>  這個類別及其成員不能在 Windows 執行階段中執行的應用程式。  
  
## <a name="syntax"></a>語法  
  
```
class CRTThreadTraits
```  
  
## <a name="members"></a>Members  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|說明|  
|----------|-----------------|  
|[CRTThreadTraits::CreateThread](#createthread)|（靜態）呼叫此函式建立的執行緒，可以使用 CRT 函式。|  
  
## <a name="remarks"></a>備註  
 執行緒的特點就是執行緒的提供特定類型建立函式的類別。 建立函式有相同的簽章和語意 （semantics） 與 Windows [CreateThread](http://msdn.microsoft.com/library/windows/desktop/ms682453)函式。  
  
 下列類別會使用執行緒特性︰  
  
- [CThreadPool](../../atl/reference/cthreadpool-class.md)  
  
- [CWorkerThread](../../atl/reference/cworkerthread-class.md)  
  
 如果執行緒將不會使用 CRT 函式，使用[Win32ThreadTraits](../../atl/reference/win32threadtraits-class.md)改。  
  
## <a name="requirements"></a>需求  
 **標頭︰** atlbase.h  
  
##  <a name="a-namecreatethreada--crtthreadtraitscreatethread"></a><a name="createthread"></a>CRTThreadTraits::CreateThread  
 呼叫此函式建立的執行緒，可以使用 CRT 函式。  
  
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
 新的執行緒的安全性屬性。  
  
 `dwStackSize`  
 新的執行緒堆疊大小。  
  
 `pfnThreadProc`  
 新執行緒的執行緒程序。  
  
 `pvParam`  
 要傳遞給執行緒的程序的參數。  
  
 `dwCreationFlags`  
 建立旗標 （0 或 CREATE_SUSPENDED）。  
  
 `pdwThreadId`  
 [out]DWORD 接收的變數，成功時，新建立的執行緒的執行緒識別碼的位址。  
  
### <a name="return-value"></a>傳回值  
 傳回新建立的執行緒或 NULL 的控制代碼失敗。 呼叫[GetLastError](http://msdn.microsoft.com/library/windows/desktop/ms679360)取得擴充的錯誤資訊。  
  
### <a name="remarks"></a>備註  
 請參閱[CreateThread](http://msdn.microsoft.com/library/windows/desktop/ms682453)更多有關此函數的參數。  
  
 此函數會呼叫[_beginthreadex](../../c-runtime-library/reference/beginthread-beginthreadex.md)建立執行緒。  
  
## <a name="see-also"></a>另請參閱  
 [類別概觀](../../atl/atl-class-overview.md)

