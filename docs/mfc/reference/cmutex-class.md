---
title: "CMutex 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CMutex
- AFXMT/CMutex
- AFXMT/CMutex::CMutex
dev_langs:
- C++
helpviewer_keywords:
- CMutex class
- synchronization classes, CMutex class
- synchronization objects, mutex
- mutex
ms.assetid: 6330c050-4f01-4195-a099-2029b92f8cf1
caps.latest.revision: 22
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
ms.sourcegitcommit: 040985df34f2613b4e4fae29498721aef15d50cb
ms.openlocfilehash: 159f2e02dfe44d74ebcaad687a23cef734b61fc9
ms.lasthandoff: 02/24/2017

---
# <a name="cmutex-class"></a>CMutex 類別
代表 「 mutex 」 — 允許執行緒互斥存取資源的同步處理物件。  
  
## <a name="syntax"></a>語法  
  
```  
class CMutex : public CSyncObject  
```  
  
## <a name="members"></a>Members  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|說明|  
|----------|-----------------|  
|[CMutex::CMutex](#cmutex)|建構 `CMutex` 物件。|  
  
## <a name="remarks"></a>備註  
 可允許一次只有一個執行緒修改資料或其他一些受控制的資源時，Mutex 就很有用。 例如，將節點加入至連結的清單是應只允許一個執行緒一次的處理程序。 使用`CMutex`物件，以控制連結的清單中，只有一次一個執行緒可以存取清單。  
  
 若要使用`CMutex`物件，建構`CMutex`物件會在需要時。 指定您想要等候的 mutex 的名稱和您的應用程式一開始應該擁有它。 然後，建構函式傳回時，您可以存取 mutex。 呼叫[CSyncObject::Unlock](../../mfc/reference/csyncobject-class.md#unlock)完成存取控制的資源。  
  
 使用替代方法`CMutex`物件是新增型別的變數`CMutex`以您想要控制的類別資料成員。 在受控制的物件建構期間呼叫的建構函式`CMutex`資料成員指定是否 mutex 一開始擁有，名稱的 mutex （如果它將會使用跨處理序界限），以及所需的安全性屬性。  
  
 控制存取資源`CMutex`物件以這種方式，先建立這兩種類型的變數[CSingleLock](../../mfc/reference/csinglelock-class.md)或型別[CMultiLock](../../mfc/reference/cmultilock-class.md)在您的資源存取的成員函式。 接著呼叫鎖定物件的`Lock`成員函式 (例如， [CSingleLock::Lock](../../mfc/reference/csinglelock-class.md#lock))。 此時，您的執行緒會取得資源的存取權，等待資源釋出，並存取應用程式，或等待資源釋出及逾時，無法存取的資源。 在任何情況下，您的資源已存取具備執行緒安全的方式。 若要釋放資源，使用鎖定物件的`Unlock`成員函式 (例如， [CSingleLock::Unlock](../../mfc/reference/csinglelock-class.md#unlock))，或允許超出範圍的鎖定物件。  
  
 如需有關使用`CMutex`物件，請參閱文章[多執行緒︰ 如何使用同步類別](../../parallel/multithreading-how-to-use-the-synchronization-classes.md)。  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CSyncObject](../../mfc/reference/csyncobject-class.md)  
  
 `CMutex`  
  
## <a name="requirements"></a>需求  
 **標頭︰** afxmt.h  
  
##  <a name="cmutex"></a>CMutex::CMutex  
 建構具名或未命名的`CMutex`物件。  
  
```  
CMutex(
    BOOL bInitiallyOwn = FALSE,  
    LPCTSTR lpszName = NULL,  
    LPSECURITY_ATTRIBUTES lpsaAttribute = NULL);
```  
  
### <a name="parameters"></a>參數  
 `bInitiallyOwn`  
 指定如果執行緒建立`CMutex`物件一開始會有由 mutex 控制資源的存取權。  
  
 `lpszName`  
 `CMutex` 物件的名稱。 如果具有相同名稱的另一個 mutex 已存在，`lpszName`必須提供，如果該物件會用於跨處理序界限。 如果**NULL**，便會是未命名。 如果名稱符合現有的 mutex，建構函式會建置新`CMutex`會參考該名稱的 mutex 物件。 如果名稱符合現有的同步處理物件不是 mutex，建構將會失敗。  
  
 `lpsaAttribute`  
 Mutex 物件的安全性屬性。 此結構的完整說明，請參閱[ATTRIBUTES](http://msdn.microsoft.com/library/windows/desktop/aa379560)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
### <a name="remarks"></a>備註  
 存取或釋放`CMutex`物件，請建立[CMultiLock](../../mfc/reference/cmultilock-class.md)或[CSingleLock](../../mfc/reference/csinglelock-class.md)物件，然後呼叫其[鎖定](../../mfc/reference/csinglelock-class.md#lock)和[Unlock](../../mfc/reference/csinglelock-class.md#unlock)成員函式。 如果`CMutex`獨立使用物件，請呼叫其`Unlock`成員函式來釋放它。  
  
> [!IMPORTANT]
>  在建立之後`CMutex`物件，請使用[GetLastError](http://msdn.microsoft.com/library/windows/desktop/ms679360)以確保，mutex 原本不存在。 如果存在非預期地 mutex，可能表示處理序佔用，而且可能會想要進行惡意使用 mutex。 在此情況下，建議的注重安全性的程序是關閉此控制代碼，並繼續如同在建立物件時發生錯誤。  
  
## <a name="see-also"></a>另請參閱  
 [CSyncObject 類別](../../mfc/reference/csyncobject-class.md)   
 [階層架構圖表](../../mfc/hierarchy-chart.md)




