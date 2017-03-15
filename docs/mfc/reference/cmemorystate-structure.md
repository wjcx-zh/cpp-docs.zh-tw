---
title: "CMemoryState 結構 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CMemoryState
dev_langs:
- C++
helpviewer_keywords:
- CMemoryState structure
- memory leaks, detecting
- detecting memory leaks
ms.assetid: 229d9de7-a6f3-4cc6-805b-5a9d9b1bfe1d
caps.latest.revision: 19
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
ms.openlocfilehash: 037c8f075a14346e3428c5e19bfda662c4f3c2b0
ms.lasthandoff: 02/24/2017

---
# <a name="cmemorystate-structure"></a>CMemoryState 結構
提供一個便利方式來偵測記憶體流失的問題在您的程式。  
  
## <a name="syntax"></a>語法  
  
```  
struct CMemoryState  
```  
  
## <a name="members"></a>Members  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|說明|  
|----------|-----------------|  
|[CMemoryState::CMemoryState](#cmemorystate)|控制記憶體檢查點的建構類似類別結構。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|說明|  
|----------|-----------------|  
|[CMemoryState::Checkpoint](#checkpoint)|取得目前的記憶體狀態快照 （檢查點）。|  
|[CMemoryState::Difference](#difference)|計算兩個物件的型別之間的差異`CMemoryState`。|  
|[CMemoryState::DumpAllObjectsSince](#dumpallobjectssince)|自上一個檢查點之後，傾印目前配置的所有物件的摘要。|  
|[CMemoryState::DumpStatistics](#dumpstatistics)|列印記憶體配置的統計資料的`CMemoryState`物件。|  
  
## <a name="remarks"></a>備註  
 `CMemoryState`是一種結構，而且也沒有基底類別。  
  
 在堆積上配置但不再需要時無法取消配置物件記憶體時，就會發生 「 記憶體遺漏 」。 這類的記憶體流失最後可能會導致記憶體不足錯誤。 有數種方式配置和解除配置程式的記憶體︰  
  
-   使用`malloc` / **免費**系列的函式，執行階段程式庫。  
  
-   使用 Windows API 記憶體管理函式， **LocalAlloc**/ **LocalFree**和**GlobalAlloc**/ **GlobalFree**。  
  
-   使用 c + +**新**和**刪除**運算子。  
  
 `CMemoryState`診斷不僅能夠協助偵測記憶體流失記憶體配置使用時，產生**新**運算子會被解除配置使用**刪除**。 其他兩個群組的記憶體管理函式適用於非 c + + 程式，並混合它們與**新**和**刪除**在同一個程式並不建議。 其他的巨集， `DEBUG_NEW`，可用來取代**新**運算子時，您需要的檔案和行號追蹤記憶體配置。 `DEBUG_NEW`每當您通常會使用就會使用**新**運算子。  
  
 如同其他診斷、`CMemoryState`診斷才會提供您的程式的偵錯版本。 偵錯版本必須**_DEBUG**定義常數。  
  
 如果您懷疑程式有記憶體流失，您可以使用`Checkpoint`，**差異**，和`DumpStatistics`記憶體內部狀態 （已配置的物件） 之間的差異探索在兩個不同的點在程式執行的函式。 這項資訊可用於判斷函式會清除其所配置的所有物件。  
  
 如果只了解在配置和解除配置不平衡的發生位置並不會提供足夠的資訊，您可以使用`DumpAllObjectsSince`傾印從上一個呼叫所配置的所有物件的函式`Checkpoint`。 此傾印顯示配置、 原始程式檔和物件的配置位置的行的順序 (如果您使用`DEBUG_NEW`配置)，以及衍生物件，其位址以及其大小。 `DumpAllObjectsSince`也會呼叫每個物件的`Dump`函式以提供其目前狀態的相關資訊。  
  
 如需有關如何使用`CMemoryState`和其他診斷，請參閱[偵錯 MFC 應用程式](/visualstudio/debugger/mfc-debugging-techniques)。  
  
> [!NOTE]
>  宣告中的物件型別的`CMemoryState`和呼叫成員函式應該括住`#if defined(_DEBUG)/#endif`指示詞。 這會導致記憶體診斷，只包括在偵錯程式的組建。  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 `CMemoryState`  
  
## <a name="requirements"></a>需求  
 **標頭：** afx.h  
  
##  <a name="a-namecheckpointa--cmemorystatecheckpoint"></a><a name="checkpoint"></a>CMemoryState::Checkpoint  
 會建立快照摘要的記憶體，並將它儲存在這個`CMemoryState`物件。  
  
```  
void Checkpoint();
```  
  
### <a name="remarks"></a>備註  
 `CMemoryState`成員函式[差異](#difference)和[DumpAllObjectsSince](#dumpallobjectssince)使用此快照集資料。  
  
### <a name="example"></a>範例  
  請參閱範例[CMemoryState](#cmemorystate)建構函式。  
  
##  <a name="a-namecmemorystatea--cmemorystatecmemorystate"></a><a name="cmemorystate"></a>CMemoryState::CMemoryState  
 建構空`CMemoryState`物件，必須要填入[檢查點](#checkpoint)或[差異](#difference)成員函式。  
  
```  
CMemoryState();
```  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFC_Utilities #&18;](../../mfc/codesnippet/cpp/cmemorystate-structure_1.cpp)]  
  
##  <a name="a-namedifferencea--cmemorystatedifference"></a><a name="difference"></a>CMemoryState::Difference  
 比較兩個`CMemoryState`物件，然後儲存到這個差異`CMemoryState`物件。  
  
```  
BOOL Difference(
    const CMemoryState& oldState,   
    const CMemoryState& newState);
```  
  
### <a name="parameters"></a>參數  
 *oldState*  
 所定義的初始記憶體狀態`CMemoryState`檢查點。  
  
 *newState*  
 由定義新的記憶體狀態`CMemoryState`檢查點。  
  
### <a name="return-value"></a>傳回值  
 如果兩個記憶體狀態不同則為非零否則為 0。  
  
### <a name="remarks"></a>備註  
 [檢查點](#checkpoint)必須針對兩個記憶體狀態參數的每個呼叫。  
  
### <a name="example"></a>範例  
  請參閱範例[CMemoryState](#cmemorystate)建構函式。  
  
##  <a name="a-namedumpallobjectssincea--cmemorystatedumpallobjectssince"></a><a name="dumpallobjectssince"></a>CMemoryState::DumpAllObjectsSince  
 呼叫`Dump`函式的所有物件的型別衍生自類別`CObject`的配置 （和仍然已配置） 自上次[檢查點](#checkpoint)這個呼叫`CMemoryState`物件。  
  
```  
void DumpAllObjectsSince() const;

 
```  
  
### <a name="remarks"></a>備註  
 呼叫`DumpAllObjectsSince`以未初始化`CMemoryState`物件會傾印出目前在記憶體中的所有物件。  
  
### <a name="example"></a>範例  
  請參閱範例[CMemoryState](#cmemorystate)建構函式。  
  
##  <a name="a-namedumpstatisticsa--cmemorystatedumpstatistics"></a><a name="dumpstatistics"></a>CMemoryState::DumpStatistics  
 列印簡潔記憶體統計資料報告從`CMemoryState`物件的填滿[差異](#difference)成員函式。  
  
```  
void DumpStatistics() const;

 
```  
  
### <a name="remarks"></a>備註  
 報表中，在列印[afxDump](http://msdn.microsoft.com/library/4b3cfa3f-fb75-456a-9d99-a5601acbcb11)裝置，會顯示下列︰  
  
 範例報表會提供資訊的數字 （或量）︰  
  
-   可用的區塊  
  
-   一般區塊  
  
-   CRT 區塊  
  
-   忽略區塊  
  
-   用戶端區塊  
  
-   在任何一個時間 （以位元組為單位） 程式所使用的最大記憶體  
  
-   （以位元組為單位） 的程式目前使用的記憶體總數  
  
 自由區塊是如果延遲的取消配置的區塊數目`afxMemDF`設為**delayFreeMemDF**。 如需詳細資訊，請參閱[afxMemDF](diagnostic-services.md#afxmemdf)，「 MFC 巨集和全域變數 」 一節。 請參閱[類型的偵錯堆積上區塊](http://msdn.microsoft.com/en-us/db2e7f62-0679-4b39-a23f-26f2c2f407c5)詳細資訊，在這些區塊型別。  
  
### <a name="example"></a>範例  
  下列程式碼應該放在*projname*app.cpp。 定義下列全域變數︰  
  
 [!code-cpp[NVC_MFC_Utilities #&40;](../../mfc/codesnippet/cpp/cmemorystate-structure_2.cpp)]  
  
 在`InitInstance`函式中，加入這一行︰  
  
 [!code-cpp[NVC_MFC_Utilities #&41;](../../mfc/codesnippet/cpp/cmemorystate-structure_3.cpp)]  
  
 加入的處理常式`ExitInstance`函式，並使用下列程式碼︰  
  
 [!code-cpp[NVC_MFC_Utilities #&42;](../../mfc/codesnippet/cpp/cmemorystate-structure_4.cpp)]  
  
 您現在可以看到的輸出的偵錯模式執行程式`DumpStatistics`函式。  
  
## <a name="see-also"></a>另請參閱  
 [階層架構圖表](../../mfc/hierarchy-chart.md)




