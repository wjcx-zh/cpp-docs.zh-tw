---
title: Win32ThreadTraits 類別 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- Win32ThreadTraits
- ATLBASE/ATL::Win32ThreadTraits
- ATLBASE/ATL::Win32ThreadTraits::CreateThread
dev_langs:
- C++
helpviewer_keywords:
- threading [ATL], Windows threads
- threading [ATL], creation functions
- Win32ThreadTraits class
ms.assetid: 50279c38-eae1-4301-9ea6-97ccea580f3e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: c61ba91fe29610f4b313cf31c65f514ef8e46f96
ms.sourcegitcommit: 7d68f8303e021e27dc8f4d36e764ed836e93d24f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/06/2018
ms.locfileid: "37883670"
---
# <a name="win32threadtraits-class"></a>Win32ThreadTraits 類別
這個類別會提供以 Windows 執行緒的建立函式。 如果執行緒不會使用 CRT 函式，請使用這個類別。  
  
> [!IMPORTANT]
>  此類別和其成員不能在 Windows 執行階段中執行的應用程式。  
  
## <a name="syntax"></a>語法  
  
```
class Win32ThreadTraits
```  
  
## <a name="members"></a>成員  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|描述|  
|----------|-----------------|  
|[Win32ThreadTraits::CreateThread](#createthread)|（靜態）呼叫此函式來建立不應使用 CRT 函式的執行緒。|  
  
## <a name="remarks"></a>備註  
 執行緒的特性是執行緒的提供特定類型建立函式的類別。 為 Windows 建立函式具有相同的簽章和語意[CreateThread](http://msdn.microsoft.com/library/windows/desktop/ms682453)函式。  
  
 下列類別會使用執行緒的特性：  
  
- [CThreadPool](../../atl/reference/cthreadpool-class.md)  
  
- [CWorkerThread](../../atl/reference/cworkerthread-class.md)  
  
 如果執行緒將會使用 CRT 函式，使用[CRTThreadTraits](../../atl/reference/crtthreadtraits-class.md)改。  
  
## <a name="requirements"></a>需求  
 **標頭：** atlbase.h  
  
##  <a name="createthread"></a>  Win32ThreadTraits::CreateThread  
 呼叫此函式來建立不應使用 CRT 函式的執行緒。  
  
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
 *lpsa*  
 新的執行緒安全性屬性。  
  
 *dwStackSize*  
 新的執行緒堆疊大小。  
  
 *pfnThreadProc*  
 新執行緒的執行緒程序。  
  
 *pvParam*  
 要傳遞至執行緒程序的參數。  
  
 *dwCreationFlags*  
 建立旗標 （0 或 CREATE_SUSPENDED）。  
  
 *pdwThreadId*  
 [out]變數的位址 DWORD，成功時，接收新建立的執行緒的執行緒識別碼。  
  
### <a name="return-value"></a>傳回值  
 傳回新建立的執行緒或 NULL 的控制代碼，在失敗。 呼叫[GetLastError](http://msdn.microsoft.com/library/windows/desktop/ms679360)若要取得延伸錯誤資訊。  
  
### <a name="remarks"></a>備註  
 請參閱[CreateThread](http://msdn.microsoft.com/library/windows/desktop/ms682453)更多有關此函數的參數。  
  
 此函式會呼叫`CreateThread`建立執行緒。  
  
## <a name="see-also"></a>另請參閱  
 [類別概觀](../../atl/atl-class-overview.md)
