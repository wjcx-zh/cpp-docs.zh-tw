---
title: "CMemoryState 結構 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CMemoryState
dev_langs:
- C++
helpviewer_keywords:
- CMemoryState structure [MFC]
- memory leaks [MFC], detecting
- detecting memory leaks [MFC]
ms.assetid: 229d9de7-a6f3-4cc6-805b-5a9d9b1bfe1d
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 20f4c2d7d33d07a5eca5a980c376056c3fe68e2d
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="cmemorystate-structure"></a>CMemoryState 結構
提供便利的方式，來偵測記憶體流失的問題在程式中。  
  
## <a name="syntax"></a>語法  
  
```  
struct CMemoryState  
```  
  
## <a name="members"></a>成員  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|描述|  
|----------|-----------------|  
|[CMemoryState::CMemoryState](#cmemorystate)|控制記憶體檢查點的類似類別建構結構。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|描述|  
|----------|-----------------|  
|[CMemoryState::Checkpoint](#checkpoint)|取得目前的記憶體狀態快照 （檢查點）。|  
|[CMemoryState::Difference](#difference)|計算類型的兩個物件之間的差異`CMemoryState`。|  
|[Cmemorystate:: Dumpallobjectssince](#dumpallobjectssince)|自上一個檢查點之後，傾印所有目前已配置物件的摘要。|  
|[CMemoryState::DumpStatistics](#dumpstatistics)|列印記憶體配置的統計資料的`CMemoryState`物件。|  
  
## <a name="remarks"></a>備註  
 `CMemoryState`是一種結構，而且沒有基底類別。  
  
 在堆積上配置但不再需要時取消配置物件記憶體時，就會發生 「 記憶體流失 」。 這類的記憶體流失最後可能會導致記憶體不足錯誤。 有數種方式來配置和解除配置程式的記憶體：  
  
-   使用`malloc` / **可用**系列的函式，從執行階段程式庫。  
  
-   使用 Windows API 記憶體管理函式， **LocalAlloc**/ **LocalFree**和**GlobalAlloc**/ **GlobalFree**.  
  
-   使用 c + +**新**和**刪除**運算子。  
  
 `CMemoryState`診斷只幫助偵測記憶體流失的記憶體配置使用時，產生**新**運算子會取消配置使用**刪除**。 其他兩個群組的記憶體管理函式適用於非 c + + 程式，並混合它們與**新**和**刪除**相同程式中不在建議。 其他的巨集， `DEBUG_NEW`，可用來取代**新**運算子時，您需要的檔案和行號追蹤記憶體配置。 `DEBUG_NEW`您通常會使用時，都會使用**新**運算子。  
  
 如同其他診斷，`CMemoryState`診斷中才有您的程式的偵錯版本。 偵錯版本必須有**_DEBUG**常數定義。  
  
 如果您懷疑程式有記憶體流失，您可以使用`Checkpoint`，**差異**，和`DumpStatistics`記憶體狀態 （已配置的物件） 之間的差異探索在兩個不同的點在程式中的函式執行。 這項資訊可用於判斷函式會清除其所配置的所有物件。  
  
 如果只了解，不平衡配置和解除配置中的發生未提供足夠的資訊，您可以使用`DumpAllObjectsSince`傾印所有配置自上次呼叫物件的函式`Checkpoint`。 這個傾印顯示順序配置、 原始程式檔和列物件配置的位置 (如果您使用`DEBUG_NEW`配置)，和衍生的物件，其位址以及其大小。 `DumpAllObjectsSince`也會呼叫每個物件的`Dump`函式可提供其目前狀態的相關資訊。  
  
 如需有關如何使用`CMemoryState`和其他診斷，請參閱[偵錯 MFC 應用程式](/visualstudio/debugger/mfc-debugging-techniques)。  
  
> [!NOTE]
>  宣告類型的物件`CMemoryState`和成員函式的呼叫應該由括號起來`#if defined(_DEBUG)/#endif`指示詞。 這會導致記憶體診斷，只會納入偵錯程式的組建。  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 `CMemoryState`  
  
## <a name="requirements"></a>需求  
 **標頭：** afx.h  
  
##  <a name="checkpoint"></a>CMemoryState::Checkpoint  
 快照摘要的記憶體，並將它儲存在這個`CMemoryState`物件。  
  
```  
void Checkpoint();
```  
  
### <a name="remarks"></a>備註  
 `CMemoryState`成員函式[差異](#difference)和[DumpAllObjectsSince](#dumpallobjectssince)使用此快照集資料。  
  
### <a name="example"></a>範例  
  請參閱範例的[CMemoryState](#cmemorystate)建構函式。  
  
##  <a name="cmemorystate"></a>CMemoryState::CMemoryState  
 建構空`CMemoryState`必須要填入的物件[檢查點](#checkpoint)或[差異](#difference)成員函式。  
  
```  
CMemoryState();
```  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFC_Utilities#18](../../mfc/codesnippet/cpp/cmemorystate-structure_1.cpp)]  
  
##  <a name="difference"></a>CMemoryState::Difference  
 比較兩個`CMemoryState`物件，則會儲存到這個差異`CMemoryState`物件。  
  
```  
BOOL Difference(
    const CMemoryState& oldState,   
    const CMemoryState& newState);
```  
  
### <a name="parameters"></a>參數  
 *oldState*  
 所定義的初始記憶體狀態`CMemoryState`檢查點。  
  
 *newState*  
 所定義的新記憶體狀態`CMemoryState`檢查點。  
  
### <a name="return-value"></a>傳回值  
 如果兩個記憶體狀態不同則為非零否則便是 0。  
  
### <a name="remarks"></a>備註  
 [檢查點](#checkpoint)必須針對兩個記憶體狀態參數的每個呼叫。  
  
### <a name="example"></a>範例  
  請參閱範例的[CMemoryState](#cmemorystate)建構函式。  
  
##  <a name="dumpallobjectssince"></a>Cmemorystate:: Dumpallobjectssince  
 呼叫`Dump`函式之所有物件的型別衍生自類別`CObject`配置 （而且仍配置） 自上次[檢查點](#checkpoint)呼叫這個`CMemoryState`物件。  
  
```  
void DumpAllObjectsSince() const;

 
```  
  
### <a name="remarks"></a>備註  
 呼叫`DumpAllObjectsSince`以未初始化`CMemoryState`物件會傾印目前在記憶體中的所有物件。  
  
### <a name="example"></a>範例  
  請參閱範例的[CMemoryState](#cmemorystate)建構函式。  
  
##  <a name="dumpstatistics"></a>CMemoryState::DumpStatistics  
 列印精簡記憶體統計資料報告從`CMemoryState`物件，會填入[差異](#difference)成員函式。  
  
```  
void DumpStatistics() const;

 
```  
  
### <a name="remarks"></a>備註  
 報表中，在列印[afxDump](diagnostic-services.md#afxdump)裝置，顯示下列：  
  
 範例報表會提供資訊的數字 （或量）：  
  
-   可用的區塊  
  
-   一般區塊  
  
-   CRT 區塊  
  
-   忽略區塊  
  
-   用戶端區塊  
  
-   在任何一個時間 （以位元組為單位） 程式所使用的最大記憶體  
  
-   （以位元組為單位） 程式正在使用的記憶體總計  
  
 自由區塊是如果延遲其解除配置的區塊數目`afxMemDF`設**delayFreeMemDF**。 如需詳細資訊，請參閱[afxMemDF](diagnostic-services.md#afxmemdf)，「 MFC 巨集和全域變數 」 一節。 請參閱[類型的區塊上進行偵錯堆積](http://msdn.microsoft.com/en-us/db2e7f62-0679-4b39-a23f-26f2c2f407c5)如需詳細資訊，這些區塊類型。  
  
### <a name="example"></a>範例  
  下列程式碼應該放在*projname*app.cpp。 定義下列全域變數：  
  
 [!code-cpp[NVC_MFC_Utilities#40](../../mfc/codesnippet/cpp/cmemorystate-structure_2.cpp)]  
  
 在`InitInstance`函式中，加入一行：  
  
 [!code-cpp[NVC_MFC_Utilities#41](../../mfc/codesnippet/cpp/cmemorystate-structure_3.cpp)]  
  
 加入的處理常式`ExitInstance`函式，並使用下列程式碼：  
  
 [!code-cpp[NVC_MFC_Utilities#42](../../mfc/codesnippet/cpp/cmemorystate-structure_4.cpp)]  
  
 您現在可以看到的輸出偵錯模式執行程式`DumpStatistics`函式。  
  
## <a name="see-also"></a>請參閱  
 [階層架構圖表](../../mfc/hierarchy-chart.md)



