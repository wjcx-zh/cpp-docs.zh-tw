---
title: "CCriticalSection 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CCriticalSection
- AFXMT/CCriticalSection
- AFXMT/CCriticalSection::CCriticalSection
- AFXMT/CCriticalSection::Lock
- AFXMT/CCriticalSection::Unlock
- AFXMT/CCriticalSection::m_sect
dev_langs:
- C++
helpviewer_keywords:
- synchronization objects, critical section
- CCriticalSection class
- critical sections
- synchronization classes, CCriticalSection class
ms.assetid: f776f74b-5b0b-4f32-9c13-2b8e4a0d7b2b
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
ms.translationtype: Machine Translation
ms.sourcegitcommit: 0e0c08ddc57d437c51872b5186ae3fc983bb0199
ms.openlocfilehash: 25d4b124d089441503e9cb457e648695fc54660d
ms.contentlocale: zh-tw
ms.lasthandoff: 02/24/2017

---
# <a name="ccriticalsection-class"></a>CCriticalSection 類別
代表 「 關鍵區段 」 — 讓一個執行緒存取資源或程式碼區段的一次的同步處理物件。  
  
## <a name="syntax"></a>語法  
  
```  
class CCriticalSection : public CSyncObject  
```  
  
## <a name="members"></a>Members  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|說明|  
|----------|-----------------|  
|[CCriticalSection::CCriticalSection](#ccriticalsection)|建構 `CCriticalSection` 物件。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|說明|  
|----------|-----------------|  
|[CCriticalSection::Lock](#lock)|用來存取`CCriticalSection`物件。|  
|[CCriticalSection::Unlock](#unlock)|釋出 `CCriticalSection` 物件。|  
  
### <a name="public-operators"></a>公用運算子  
  
|名稱|說明|  
|----------|-----------------|  
|[CCriticalSection::operator CRITICAL_SECTION *](#operator_critical_section_star)|擷取到內部指標**CRITICAL_SECTION**物件。|  
  
### <a name="public-data-members"></a>公用資料成員  
  
|名稱|說明|  
|----------|-----------------|  
|[CCriticalSection::m_sect](#m_sect)|A **CRITICAL_SECTION**物件。|  
  
## <a name="remarks"></a>備註  
 可允許一次只有一個執行緒修改資料或其他一些受控制的資源時，重要區段會非常有用。 例如，將節點加入至連結的清單是應只允許一個執行緒一次的處理程序。 使用`CCriticalSection`物件，以控制連結的清單中，只有一次一個執行緒可以存取清單。  
  
> [!NOTE]
>  功能`CCriticalSection`類別提供實際的 Win32 **CRITICAL_SECTION**物件。  
  
 關鍵區段代替 mutex (請參閱[CMutex](../../mfc/reference/cmutex-class.md)) 時速度非常重要，且不會跨處理序界限使用的資源。  
  
 有兩種方法使用`CCriticalSection`物件︰ 獨立和內嵌在類別中。  
  
-   若要使用獨立的獨立方法`CCriticalSection`物件，建構`CCriticalSection`物件會在需要時。 從建構函式成功傳回之後, 明確地鎖定的物件呼叫[鎖定](#lock)。 呼叫[Unlock](#unlock)完成存取重要區段。 這個方法，同時清楚給其他人讀取程式碼中，是更容易發生錯誤時，您必須記得鎖定和解除鎖定重要區段之前和之後存取。  
  
     更佳的方法是使用[CSingleLock](../../mfc/reference/csinglelock-class.md)類別。 它也有`Lock`和`Unlock`方法，但您不需要擔心解除鎖定資源，如果發生例外狀況。  
  
-   內嵌方法，您也可以共用多個執行緒的類別，藉由新增`CCriticalSection`-類別和鎖定時所需的資料成員的型別資料成員。  
  
 如需有關使用`CCriticalSection`物件，請參閱文章[多執行緒︰ 如何使用同步類別](../../parallel/multithreading-how-to-use-the-synchronization-classes.md)。  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CSyncObject](../../mfc/reference/csyncobject-class.md)  
  
 `CCriticalSection`  
  
## <a name="requirements"></a>需求  
 **標頭︰** afxmt.h  
  
##  <a name="ccriticalsection"></a>CCriticalSection::CCriticalSection  
 建構 `CCriticalSection` 物件。  
  
```  
CCriticalSection();
```  
  
### <a name="remarks"></a>備註  
 若要存取，或發行`CCriticalSection`物件，請建立[CSingleLock](../../mfc/reference/csinglelock-class.md)物件，然後呼叫其[鎖定](../../mfc/reference/csinglelock-class.md#lock)和[解除鎖定](../../mfc/reference/csinglelock-class.md#unlock)成員函式。 如果`CCriticalSection`獨立使用物件，請呼叫其[Unlock](#unlock)成員函式來釋放它。  
  
 如果建構函式，就無法配置所需的系統記憶體，記憶體例外狀況 (型別[Afxthrowmemoryexception](../../mfc/reference/cmemoryexception-class.md)) 會自動擲回。  
  
### <a name="example"></a>範例  
  請參閱範例[CCriticalSection::Lock](#lock)。  
  
##  <a name="lock"></a>CCriticalSection::Lock  
 呼叫此成員函式，以取得重要區段物件的存取權。  
  
```  
BOOL Lock();  
BOOL Lock(DWORD dwTimeout);
```  
  
### <a name="parameters"></a>參數  
 `dwTimeout`  
 `Lock`會忽略此參數值。  
  
### <a name="return-value"></a>傳回值  
 如果函式成功則為非零否則為 0。  
  
### <a name="remarks"></a>備註  
 `Lock`已封鎖的呼叫，直到收到信號的重要區段物件將不會傳回 （可用）。  
  
 如果已逾時的等候是必要的您可以使用[CMutex](../../mfc/reference/cmutex-class.md)物件而非`CCriticalSection`物件。  
  
 如果`Lock`無法配置必要的系統記憶體，記憶體例外狀況 (型別[Afxthrowmemoryexception](../../mfc/reference/cmemoryexception-class.md)) 會自動擲回。  
  
### <a name="example"></a>範例  
 這個範例會示範巢狀的重要區段法藉由控制共用資源的存取權 (靜態`_strShared`物件) 使用共用`CCriticalSection`物件。 `SomeMethod`函式示範，如何以安全的方式更新共用的資源。  
  
 [!code-cpp[NVC_MFC_Utilities #&11;](../../mfc/codesnippet/cpp/ccriticalsection-class_1.h)]  
  
##  <a name="m_sect"></a>CCriticalSection::m_sect  
 包含所有使用的重要區段物件`CCriticalSection`方法。  
  
```  
CRITICAL_SECTION m_sect;  
```  
  
##  <a name="operator_critical_section_star"></a>CCriticalSection::operator CRITICAL_SECTION *  
 擷取**CRITICAL_SECTION**物件。  
  
```  
operator CRITICAL_SECTION*();
```   
  
### <a name="remarks"></a>備註  
 呼叫此函式可擷取內部指標**CRITICAL_SECTION**物件。  
  
##  <a name="unlock"></a>CCriticalSection::Unlock  
 版本`CCriticalSection`以供另一個執行緒的物件。  
  
```  
BOOL Unlock();
```  
  
### <a name="return-value"></a>傳回值  
 如果為非零`CCriticalSection`物件之擁有者執行緒和發行已成功，否則為 0。  
  
### <a name="remarks"></a>備註  
 如果`CCriticalSection`正在使用獨立的`Unlock`必須完成使用重要區段所控制的資源之後，立即呼叫。 如果[CSingleLock](../../mfc/reference/csinglelock-class.md)使用物件時，`CCriticalSection::Unlock`鎖定物件會呼叫`Unlock`成員函式。  
  
### <a name="example"></a>範例  
  請參閱範例[CCriticalSection::Lock](#lock)。  
  
## <a name="see-also"></a>另請參閱  
 [CSyncObject 類別](../../mfc/reference/csyncobject-class.md)   
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [CMutex 類別](../../mfc/reference/cmutex-class.md)

