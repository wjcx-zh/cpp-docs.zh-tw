---
title: Win32ThreadTraits 類別 |Microsoft 文件
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
ms.openlocfilehash: 9b863808a2367cae8878728403dbf11265b9e819
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
ms.locfileid: "32362012"
---
# <a name="win32threadtraits-class"></a>Win32ThreadTraits 類別
這個類別提供 Windows 執行緒建立函式。 如果執行緒不會使用 CRT 函式，請使用這個類別。  
  
> [!IMPORTANT]
>  這個類別及其成員不能在 Windows 執行階段中執行的應用程式。  
  
## <a name="syntax"></a>語法  
  
```
class Win32ThreadTraits
```  
  
## <a name="members"></a>成員  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|描述|  
|----------|-----------------|  
|[Win32ThreadTraits::CreateThread](#createthread)|（靜態）呼叫此函式可建立的執行緒，不應該使用 CRT 函式。|  
  
## <a name="remarks"></a>備註  
 執行緒特性是執行緒的提供特定類型建立函式的類別。 建立函式有相同的簽章和語意與 Windows [CreateThread](http://msdn.microsoft.com/library/windows/desktop/ms682453)函式。  
  
 下列類別會使用執行緒特性：  
  
- [CThreadPool](../../atl/reference/cthreadpool-class.md)  
  
- [CWorkerThread](../../atl/reference/cworkerthread-class.md)  
  
 如果執行緒將會使用 CRT 函式，使用[CRTThreadTraits](../../atl/reference/crtthreadtraits-class.md)改為。  
  
## <a name="requirements"></a>需求  
 **標頭：** atlbase.h  
  
##  <a name="createthread"></a>  Win32ThreadTraits::CreateThread  
 呼叫此函式可建立的執行緒，不應該使用 CRT 函式。  
  
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
  
 此函數會呼叫`CreateThread`建立執行緒。  
  
## <a name="see-also"></a>另請參閱  
 [類別概觀](../../atl/atl-class-overview.md)
