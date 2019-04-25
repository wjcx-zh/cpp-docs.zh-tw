---
title: CMemoryState 結構
ms.date: 11/04/2016
f1_keywords:
- CMemoryState
helpviewer_keywords:
- CMemoryState structure [MFC]
- memory leaks [MFC], detecting
- detecting memory leaks [MFC]
ms.assetid: 229d9de7-a6f3-4cc6-805b-5a9d9b1bfe1d
ms.openlocfilehash: a110e1345cb970c117de125bd8105e1bc86eaf94
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62163750"
---
# <a name="cmemorystate-structure"></a>CMemoryState 結構

提供便利的方式來偵測記憶體流失的問題在您的程式。

## <a name="syntax"></a>語法

```
struct CMemoryState
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[CMemoryState::CMemoryState](#cmemorystate)|控制記憶體檢查點的建構類似類別結構。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CMemoryState::Checkpoint](#checkpoint)|取得目前的記憶體狀態快照 （檢查點）。|
|[CMemoryState::Difference](#difference)|計算兩個物件的型別之間的差異`CMemoryState`。|
|[CMemoryState::DumpAllObjectsSince](#dumpallobjectssince)|自上一個檢查點之後，傾印目前配置的所有物件的摘要。|
|[CMemoryState::DumpStatistics](#dumpstatistics)|列印記憶體配置的統計資料`CMemoryState`物件。|

## <a name="remarks"></a>備註

`CMemoryState` 是一種結構，而且沒有基底類別。

物件的記憶體在堆積上配置但未解除配置時已不再需要時，就會發生 「 記憶體遺漏 」。 這類的記憶體流失最終可能會導致記憶體不足錯誤。 有數種方式來配置及解除配置您的程式中的記憶體：

- 使用`malloc` /  `free`系列函式，從執行階段程式庫。

- 使用 Windows API 記憶體管理函式`LocalAlloc` /  `LocalFree`並`GlobalAlloc` /  `GlobalFree`。

- 使用C++**新**並**刪除**運算子。

`CMemoryState`診斷不僅能夠協助偵測記憶體流失時使用的記憶體配置，產生**新**運算子未解除配置使用**刪除**。 記憶體管理函式的其他兩個群組會針對非C++程式，以及混用它們**新**並**刪除**在相同的程式不在建議。 其他巨集，DEBUG_NEW，可用來取代**新**運算子時，您需要的檔案和行號的記憶體配置的追蹤。 每當您通常會使用，會使用 DEBUG_NEW**新**運算子。

如同其他診斷，`CMemoryState`診斷僅適用於您的程式偵錯版本。 偵錯版本必須定義 _DEBUG 常數。

如果您懷疑您的程式有記憶體流失，您可以使用`Checkpoint`， `Difference`，和`DumpStatistics`函式來探索在程式執行的兩個不同點的記憶體狀態 （配置的物件） 之間的差異。 這項資訊可用於判斷函式會清除其所配置的所有物件。

如果只了解配置和解除配置中的發生不平衡的發生位置未提供足夠的資訊，您可以使用`DumpAllObjectsSince`傾印從上一個呼叫所配置的所有物件的函式`Checkpoint`。 此傾印顯示的順序，配置、 原始程式檔和行位置的物件配置 （如果您使用 DEBUG_NEW 配置），和衍生的物件、 它的位址和它的大小。 `DumpAllObjectsSince` 也會呼叫每個物件的`Dump`函式以提供其目前的狀態資訊。

如需有關如何使用`CMemoryState`和其他診斷，請參閱[偵錯 MFC 應用程式](/visualstudio/debugger/mfc-debugging-techniques)。

> [!NOTE]
>  型別之物件的宣告`CMemoryState`及呼叫成員函式應該括住`#if defined(_DEBUG)/#endif`指示詞。 這會導致記憶體診斷，以包含只在偵錯組建的程式。

## <a name="inheritance-hierarchy"></a>繼承階層

`CMemoryState`

## <a name="requirements"></a>需求

**標頭：** afx.h

##  <a name="checkpoint"></a>  CMemoryState::Checkpoint

快照摘要的記憶體，並將它儲存在這個`CMemoryState`物件。

```
void Checkpoint();
```

### <a name="remarks"></a>備註

`CMemoryState`成員函式[差異](#difference)並[DumpAllObjectsSince](#dumpallobjectssince)使用此快照集資料。

### <a name="example"></a>範例

  範例，請參閱[CMemoryState](#cmemorystate)建構函式。

##  <a name="cmemorystate"></a>  CMemoryState::CMemoryState

建構空`CMemoryState`必須要填入的物件[檢查點](#checkpoint)或是[差異](#difference)成員函式。

```
CMemoryState();
```

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_Utilities#18](../../mfc/codesnippet/cpp/cmemorystate-structure_1.cpp)]

##  <a name="difference"></a>  Cmemorystate:: Difference

比較兩個`CMemoryState`物件，則會儲存到這個差異`CMemoryState`物件。

```
BOOL Difference(
    const CMemoryState& oldState,
    const CMemoryState& newState);
```

### <a name="parameters"></a>參數

*oldState*<br/>
所定義的初始記憶體狀態`CMemoryState`檢查點。

*newState*<br/>
所定義的新記憶體狀態`CMemoryState`檢查點。

### <a name="return-value"></a>傳回值

非零值，如果兩個記憶體狀態不同;否則為 0。

### <a name="remarks"></a>備註

[檢查點](#checkpoint)必須針對兩個記憶體狀態參數的每個呼叫。

### <a name="example"></a>範例

  範例，請參閱[CMemoryState](#cmemorystate)建構函式。

##  <a name="dumpallobjectssince"></a>  CMemoryState::DumpAllObjectsSince

呼叫`Dump`類型的所有物件的函式衍生自類別`CObject`所配置 （，仍配置） 自上次[檢查點](#checkpoint)呼叫這個`CMemoryState`物件。

```
void DumpAllObjectsSince() const;
```

### <a name="remarks"></a>備註

呼叫`DumpAllObjectsSince`與 未初始化`CMemoryState`物件會將傾印出目前在記憶體中的所有物件。

### <a name="example"></a>範例

  範例，請參閱[CMemoryState](#cmemorystate)建構函式。

##  <a name="dumpstatistics"></a>  CMemoryState::DumpStatistics

會從精簡的記憶體統計資料報表的列印`CMemoryState`會填入的物件[差異](#difference)成員函式。

```
void DumpStatistics() const;
```

### <a name="remarks"></a>備註

報表中，在列印[afxDump](diagnostic-services.md#afxdump)裝置，顯示下列：

範例報表會提供資訊的數字 （或量）：

- 可用的區塊

- 一般的區塊

- CRT 區塊

- 忽略區塊

- 用戶端區塊

- 在任何一個時間 （以位元組為單位） 程式所使用的最大記憶體

- 目前 （以位元組為單位） 程式所使用的記憶體總計

自由區塊是如果延遲其解除配置的區塊數目`afxMemDF`已設為`delayFreeMemDF`。 如需詳細資訊，請參閱 < [afxMemDF](diagnostic-services.md#afxmemdf)，「 MFC 巨集和全域變數 」 一節。

### <a name="example"></a>範例

  下列程式碼應該置於*projname*app.cpp。 定義下列全域變數：

[!code-cpp[NVC_MFC_Utilities#40](../../mfc/codesnippet/cpp/cmemorystate-structure_2.cpp)]

在 `InitInstance`函式中，加入一行：

[!code-cpp[NVC_MFC_Utilities#41](../../mfc/codesnippet/cpp/cmemorystate-structure_3.cpp)]

加入的處理常式`ExitInstance`函式，並使用下列程式碼：

[!code-cpp[NVC_MFC_Utilities#42](../../mfc/codesnippet/cpp/cmemorystate-structure_4.cpp)]

您現在可以執行程式，以偵錯模式，以查看輸出`DumpStatistics`函式。

## <a name="see-also"></a>另請參閱

[階層架構圖表](../../mfc/hierarchy-chart.md)
