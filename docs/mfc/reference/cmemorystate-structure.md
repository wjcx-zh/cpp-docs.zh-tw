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
ms.openlocfilehash: 8f49a9faf70673c62167deeaa1bef33e4882378f
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81369993"
---
# <a name="cmemorystate-structure"></a>CMemoryState 結構

提供了一種檢測程式中記憶體洩漏的便捷方法。

## <a name="syntax"></a>語法

```
struct CMemoryState
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[C記憶體狀態::CMemoryState](#cmemorystate)|構造控制記憶體檢查點的類結構。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CMemoryState:檢查點](#checkpoint)|獲取當前記憶體狀態的快照(檢查點)。|
|[CMemoryState::D](#difference)|計算類型`CMemoryState`兩個對象之間的差異。|
|[CMemoryState::D個ump所有物件](#dumpallobjectssince)|轉儲自上次檢查點以來當前分配的所有物件的摘要。|
|[CMemoryState::Dump統計](#dumpstatistics)|列印`CMemoryState`物件的記憶體分配統計資訊。|

## <a name="remarks"></a>備註

`CMemoryState`是一個結構,沒有基類。

當在堆上分配物件的記憶體,但在不再需要物件時未進行處理時,就會發生「記憶體洩漏」。。 此類記憶體洩漏最終可能導致記憶體不足錯誤。 在程式中分配與分配記憶體的方法有多種:

- 使用運行時庫中的函數`free`系列`malloc`/ 。

- 使用 Windows API`LocalAlloc`/ `LocalFree`記憶體`GlobalAlloc`/ `GlobalFree`管理 功能與 。

- 使用C++**新的**運算子和**刪除**運算子。

診斷`CMemoryState`僅有助於檢測使用**新**運算符分配的記憶體未使用**delete**進行定位時導致的記憶體洩漏。 另外兩組記憶體管理功能用於非C++程式,不建議將它們與同一程式中**的新**程式和**刪除**程式混合。 提供了一個額外的宏,DEBUG_NEW,用於在需要記憶體分配的檔和行號跟蹤時替換**新**運算符。 每當您通常使用**新**運算符時,都會使用DEBUG_NEW。

與其他診斷一樣,`CMemoryState`診斷僅在程式的調試版本中可用。 調試版本必須定義_DEBUG常量。

如果您懷疑程式存在記憶體洩漏,則可以使用`Checkpoint`和`Difference``DumpStatistics`函數來發現在程式執行中的兩個不同點記憶體狀態(分配的物件)之間的差異。 此資訊可用於確定函數是否正在清理它分配的所有物件。

如果僅僅知道分配和分配位置的不平衡位置沒有提供足夠的資訊,則可以使用函數`DumpAllObjectsSince`轉儲自上次調`Checkpoint`用 以來分配的所有物件。 此轉儲顯示分配順序、分配物件的源檔和行(如果使用DEBUG_NEW進行分配),以及物件、位址和大小的派生。 `DumpAllObjectsSince`還會調用每個物件的`Dump`函數來提供有關其當前狀態的資訊。

有關如何使用`CMemoryState`和其他診斷的詳細資訊,請參閱[除錯 MFC 應用程式](/visualstudio/debugger/mfc-debugging-techniques)。

> [!NOTE]
> 類型`CMemoryState`物件聲明和對成員函數的調用`#if defined(_DEBUG)/#endif`應用 指令括括弧。 這將導致記憶體診斷僅包含在程序的調試生成中。

## <a name="inheritance-hierarchy"></a>繼承階層架構

`CMemoryState`

## <a name="requirements"></a>需求

**標題:** afx.h

## <a name="cmemorystatecheckpoint"></a><a name="checkpoint"></a>CMemoryState:檢查點

獲取記憶體的快照摘要並將其存儲在此`CMemoryState`物件中。

```
void Checkpoint();
```

### <a name="remarks"></a>備註

成員`CMemoryState`函數[「差異](#difference)」和[「轉儲所有物件」自](#dumpallobjectssince)使用此快照數據。

### <a name="example"></a>範例

  請參閱[CMemoryState](#cmemorystate)建構函數的範例。

## <a name="cmemorystatecmemorystate"></a><a name="cmemorystate"></a>C記憶體狀態::CMemoryState

建構必須由`CMemoryState`[檢查點](#checkpoint)或[差異](#difference)成員函數填充的空物件。

```
CMemoryState();
```

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_Utilities#18](../../mfc/codesnippet/cpp/cmemorystate-structure_1.cpp)]

## <a name="cmemorystatedifference"></a><a name="difference"></a>CMemoryState::D

比較兩`CMemoryState`個物件,然後將差異存儲到此`CMemoryState`物件中。

```
BOOL Difference(
    const CMemoryState& oldState,
    const CMemoryState& newState);
```

### <a name="parameters"></a>參數

*舊州*<br/>
由`CMemoryState`檢查點定義的初始記憶體狀態。

*newState*<br/>
由`CMemoryState`檢查點定義的新記憶體狀態。

### <a name="return-value"></a>傳回值

如果兩個記憶體狀態不同,則非零;否則 0。

### <a name="remarks"></a>備註

必須為兩個記憶體狀態參數中的每一個呼叫[檢查點](#checkpoint)。

### <a name="example"></a>範例

  請參閱[CMemoryState](#cmemorystate)建構函數的範例。

## <a name="cmemorystatedumpallobjectssince"></a><a name="dumpallobjectssince"></a>CMemoryState::D個ump所有物件

調用自`Dump`上次[檢查點](#checkpoint)`CMemoryState`調用此`CObject`對象以來從類 派生(並且仍已分配)的類型的所有物件的函數。

```
void DumpAllObjectsSince() const;
```

### <a name="remarks"></a>備註

使用`DumpAllObjectsSince`未初始`CMemoryState`化的物件調用將轉儲當前記憶體中的所有物件。

### <a name="example"></a>範例

  請參閱[CMemoryState](#cmemorystate)建構函數的範例。

## <a name="cmemorystatedumpstatistics"></a><a name="dumpstatistics"></a>CMemoryState::Dump統計

從由`CMemoryState`[差異](#difference)成員函數填充的物件列印簡明的記憶體統計資訊報表。

```
void DumpStatistics() const;
```

### <a name="remarks"></a>備註

列印在[afxDump](diagnostic-services.md#afxdump)裝置上的報表顯示以下內容:

範例報告提供有關以下數位(或數量)的資訊:

- 自由方塊

- 正常塊

- CRT 區塊

- 忽略區塊

- 用戶端區塊

- 程式在任何一次使用的最大記憶體(以位元組為單位)

- 應用程式目前使用的總記憶體(以位元組為單位)

自由塊是如果設置為`afxMemDF``delayFreeMemDF`延遲的塊數。 有關詳細資訊,請參閱"MFC 宏和全域"部分中的[afxMemDF。](diagnostic-services.md#afxmemdf)

### <a name="example"></a>範例

  以下代碼應放在*projname*App.cpp 中。 定義以下全域變數:

[!code-cpp[NVC_MFC_Utilities#40](../../mfc/codesnippet/cpp/cmemorystate-structure_2.cpp)]

在`InitInstance`函數中,新增行:

[!code-cpp[NVC_MFC_Utilities#41](../../mfc/codesnippet/cpp/cmemorystate-structure_3.cpp)]

函`ExitInstance`數新增處理程式並使用以下代碼:

[!code-cpp[NVC_MFC_Utilities#42](../../mfc/codesnippet/cpp/cmemorystate-structure_4.cpp)]

您現在可以在除錯模式下執行該程式以查看`DumpStatistics`函數的輸出。

## <a name="see-also"></a>另請參閱

[階層架構圖表](../../mfc/hierarchy-chart.md)
