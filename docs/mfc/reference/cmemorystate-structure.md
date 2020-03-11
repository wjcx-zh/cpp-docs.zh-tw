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
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/06/2020
ms.locfileid: "78855262"
---
# <a name="cmemorystate-structure"></a>CMemoryState 結構

提供便利的方式來偵測程式中的記憶體流失。

## <a name="syntax"></a>語法

```
struct CMemoryState
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[CMemoryState：： CMemoryState](#cmemorystate)|結構控制記憶體檢查點的類似類別結構。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CMemoryState：： Checkpoint](#checkpoint)|取得目前記憶體狀態的快照集（檢查點）。|
|[CMemoryState：:D ifference](#difference)|計算 `CMemoryState`類型的兩個物件之間的差異。|
|[CMemoryState：:D umpAllObjectsSince](#dumpallobjectssince)|從先前的檢查點開始，傾印所有目前已設定物件的摘要。|
|[CMemoryState：:D umpStatistics](#dumpstatistics)|列印 `CMemoryState` 物件的記憶體配置統計資料。|

## <a name="remarks"></a>備註

`CMemoryState` 是一個結構，而且沒有基類。

當物件的記憶體配置在堆積上，但不再需要取消配置時，就會發生「記憶體流失」。 這類記憶體流失最後可能會導致記憶體不足的錯誤。 有數種方式可以配置和解除配置程式中的記憶體：

- 從執行時間程式庫使用 `malloc`/ `free` 系列的函式。

- 使用 Windows API 記憶體管理功能，`LocalAlloc`/ `LocalFree` 和 `GlobalAlloc`/ `GlobalFree`。

- C++使用**new**和**delete**運算子。

當使用**new**運算子配置的記憶體未使用**delete**解除配置時，`CMemoryState` 診斷只會協助偵測記憶體流失。 另兩個記憶體管理函式群組適用于非C++程式，不建議將它們與相同程式中的**new**和**delete**混用。 當您需要記憶體配置的檔案和行號追蹤時，會提供額外的宏 DEBUG_NEW，以取代**新**的運算子。 每當您通常會使用**NEW**運算子時，就會使用 DEBUG_NEW。

如同其他診斷，`CMemoryState` 診斷僅適用于您程式的 debug 版本。 Debug 版本必須定義 _DEBUG 常數。

如果您懷疑程式發生記憶體流失，您可以使用 `Checkpoint`、`Difference`和 `DumpStatistics` 函式，探索程式執行中兩個不同點的記憶體狀態（已配置的物件）之間的差異。 這項資訊可用於判斷函式是否正在清除它所配置的所有物件。

如果只知道配置和解除配置的不平衡發生的位置不會提供足夠的資訊，您可以使用 `DumpAllObjectsSince` 函式來傾印自先前呼叫 `Checkpoint`之後所配置的所有物件。 此傾印會顯示配置的順序、原始程式檔和已設定物件的程式程式碼（如果您使用 DEBUG_NEW 進行配置），以及物件的衍生、其位址和大小。 `DumpAllObjectsSince` 也會呼叫每個物件的 `Dump` 函數，以提供其目前狀態的相關資訊。

如需如何使用 `CMemoryState` 和其他診斷的詳細資訊，請參閱[偵錯工具 MFC 應用程式](/visualstudio/debugger/mfc-debugging-techniques)。

> [!NOTE]
>  `CMemoryState` 類型的物件宣告和成員函式的呼叫，應由 `#if defined(_DEBUG)/#endif` 指示詞括住。 這會導致記憶體診斷僅包含在程式的偵錯工具組建中。

## <a name="inheritance-hierarchy"></a>繼承階層

`CMemoryState`

## <a name="requirements"></a>需求

**標頭：** afx.h

##  <a name="checkpoint"></a>CMemoryState：： Checkpoint

會取得記憶體的快照摘要，並將其儲存在這個 `CMemoryState` 物件中。

```
void Checkpoint();
```

### <a name="remarks"></a>備註

`CMemoryState` 成員函式[差異](#difference)和[DumpAllObjectsSince](#dumpallobjectssince)會使用此快照集資料。

### <a name="example"></a>範例

  請參閱[CMemoryState](#cmemorystate)函式的範例。

##  <a name="cmemorystate"></a>CMemoryState：： CMemoryState

建立必須由[檢查點](#checkpoint)或[差異](#difference)成員函式填入的空 `CMemoryState` 物件。

```
CMemoryState();
```

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_Utilities#18](../../mfc/codesnippet/cpp/cmemorystate-structure_1.cpp)]

##  <a name="difference"></a>CMemoryState：:D ifference

比較兩個 `CMemoryState` 物件，然後將差異儲存到這個 `CMemoryState` 物件中。

```
BOOL Difference(
    const CMemoryState& oldState,
    const CMemoryState& newState);
```

### <a name="parameters"></a>參數

*oldState*<br/>
`CMemoryState` 檢查點所定義的初始記憶體狀態。

*newState*<br/>
`CMemoryState` 檢查點所定義的新記憶體狀態。

### <a name="return-value"></a>傳回值

如果兩個記憶體狀態不同，則為非零。否則為0。

### <a name="remarks"></a>備註

必須針對兩個記憶體狀態參數呼叫[檢查點](#checkpoint)。

### <a name="example"></a>範例

  請參閱[CMemoryState](#cmemorystate)函式的範例。

##  <a name="dumpallobjectssince"></a>CMemoryState：:D umpAllObjectsSince

從這個 `CMemoryState` 物件的最後一個[檢查點](#checkpoint)呼叫之後，呼叫衍生自類別 `CObject` （且仍會配置）之類型的所有物件的 `Dump` 函數。

```
void DumpAllObjectsSince() const;
```

### <a name="remarks"></a>備註

使用未初始化的 `CMemoryState` 物件來呼叫 `DumpAllObjectsSince`，將會傾印出目前在記憶體中的所有物件。

### <a name="example"></a>範例

  請參閱[CMemoryState](#cmemorystate)函式的範例。

##  <a name="dumpstatistics"></a>CMemoryState：:D umpStatistics

從[差異](#difference)成員函式所填滿的 `CMemoryState` 物件，列印精簡的記憶體統計資料包表。

```
void DumpStatistics() const;
```

### <a name="remarks"></a>備註

在[afxDump](diagnostic-services.md#afxdump)裝置上列印的報表會顯示下列內容：

範例報表會提供的數位（或數量）的資訊：

- 免費區塊

- 一般區塊

- CRT 區塊

- 忽略區塊

- 用戶端區塊

- 程式在任何一次使用的最大記憶體（以位元組為單位）

- 程式目前使用的記憶體總計（以位元組為單位）

「可用區塊」是當 `afxMemDF` 設定為 `delayFreeMemDF`時，其解除配置已延遲的區塊數目。 如需詳細資訊，請參閱 < MFC 宏和 Globals 一節中的[afxMemDF](diagnostic-services.md#afxmemdf)。

### <a name="example"></a>範例

  下列程式碼應該放在*projname*的 .cpp 中。 定義下列全域變數：

[!code-cpp[NVC_MFC_Utilities#40](../../mfc/codesnippet/cpp/cmemorystate-structure_2.cpp)]

在 `InitInstance` 函式中，新增下列程式程式碼：

[!code-cpp[NVC_MFC_Utilities#41](../../mfc/codesnippet/cpp/cmemorystate-structure_3.cpp)]

新增 `ExitInstance` 函式的處理常式，並使用下列程式碼：

[!code-cpp[NVC_MFC_Utilities#42](../../mfc/codesnippet/cpp/cmemorystate-structure_4.cpp)]

您現在可以在 [Debug] 模式中執行程式，以查看 `DumpStatistics` 函數的輸出。

## <a name="see-also"></a>另請參閱

[階層架構圖表](../../mfc/hierarchy-chart.md)
