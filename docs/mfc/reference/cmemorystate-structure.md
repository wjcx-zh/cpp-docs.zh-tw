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
ms.openlocfilehash: 823d424620e205d14f247a147bbf7dcb40a626b9
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87222910"
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
|[CMemoryState：： CMemoryState](#cmemorystate)|建立可控制記憶體檢查點的類似類別結構。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CMemoryState：： Checkpoint](#checkpoint)|取得目前記憶體狀態的快照集 (檢查點) 。|
|[CMemoryState：:D ifference](#difference)|計算類型中兩個物件之間的差異 `CMemoryState` 。|
|[CMemoryState：:D umpAllObjectsSince](#dumpallobjectssince)|從先前的檢查點起，傾印所有目前已設定物件的摘要。|
|[CMemoryState：:D umpStatistics](#dumpstatistics)|列印物件的記憶體配置統計資料 `CMemoryState` 。|

## <a name="remarks"></a>備註

`CMemoryState` 是一個結構，而且沒有基類。

當物件的記憶體配置在堆積上，但不再需要解除配置時，就會發生「記憶體流失」。 這類記憶體流失最終可能會導致記憶體不足的錯誤。 有幾種方式可以在您的程式中配置和解除配置記憶體：

- `malloc` /  `free` 從執行時間程式庫使用函數系列。

- 使用 Windows API 記憶體管理功能 `LocalAlloc` /  `LocalFree` 和 `GlobalAlloc` /  `GlobalFree` 。

- 使用 c + + **`new`** 和 **`delete`** 運算子。

`CMemoryState`診斷只會在使用運算子配置的記憶體 **`new`** 未使用解除配置時，協助偵測記憶體流失所造成 **`delete`** 。 另外兩個記憶體管理函式群組適用于非 C + + 程式，並 **`new`** **`delete`** 不建議在相同的程式中混用它們。 **`new`** 當您需要記憶體配置的檔案和行號追蹤時，會提供額外的宏 DEBUG_NEW，以取代運算子。 當您通常使用運算子時，會使用 DEBUG_NEW **`new`** 。

如同其他診斷， `CMemoryState` 診斷僅適用于程式的偵錯工具版本。 Debug 版本必須定義 _DEBUG 常數。

如果您懷疑程式有記憶體流失，您可以使用 `Checkpoint` 、和函式， `Difference` `DumpStatistics` 來探索在程式執行的兩個不同點上配置) 的記憶體狀態 (物件之間的差異。 這項資訊有助於判斷函式是否清除其配置的所有物件。

如果只知道配置和解除配置的不平衡發生的情況並不會提供足夠的資訊，您可以使用 `DumpAllObjectsSince` 函數來傾印自上一次呼叫之後配置的所有物件 `Checkpoint` 。 此傾印會顯示配置的順序、原始程式檔 (設定物件的來源檔案和行，如果您使用 DEBUG_NEW 進行配置) ，以及物件的衍生、其位址和大小。 `DumpAllObjectsSince` 也會呼叫每個物件的 `Dump` 函數，以提供其目前狀態的相關資訊。

如需如何使用 `CMemoryState` 和其他診斷的詳細資訊，請參閱將 [MFC 應用程式偵錯工具](/visualstudio/debugger/mfc-debugging-techniques)。

> [!NOTE]
> 類型的物件宣告和成員函式的 `CMemoryState` 呼叫，應以指示詞括住 `#if defined(_DEBUG)/#endif` 。 這會導致記憶體診斷僅包含在程式的偵錯工具中。

## <a name="inheritance-hierarchy"></a>繼承階層架構

`CMemoryState`

## <a name="requirements"></a>規格需求

**標頭：** afx。h

## <a name="cmemorystatecheckpoint"></a><a name="checkpoint"></a> CMemoryState：： Checkpoint

取得記憶體的快照摘要，並將它儲存在此 `CMemoryState` 物件中。

```cpp
void Checkpoint();
```

### <a name="remarks"></a>備註

`CMemoryState`成員函式[差異](#difference)和[DumpAllObjectsSince](#dumpallobjectssince)會使用此快照集資料。

### <a name="example"></a>範例

  請參閱 [CMemoryState](#cmemorystate) 函式的範例。

## <a name="cmemorystatecmemorystate"></a><a name="cmemorystate"></a> CMemoryState：： CMemoryState

建立 `CMemoryState` 必須由 [檢查點](#checkpoint) 或 [差異](#difference) 成員函式填入的空物件。

```
CMemoryState();
```

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_Utilities#18](../../mfc/codesnippet/cpp/cmemorystate-structure_1.cpp)]

## <a name="cmemorystatedifference"></a><a name="difference"></a> CMemoryState：:D ifference

比較兩個 `CMemoryState` 物件，然後將差異儲存至這個 `CMemoryState` 物件。

```
BOOL Difference(
    const CMemoryState& oldState,
    const CMemoryState& newState);
```

### <a name="parameters"></a>參數

*oldState*<br/>
檢查點所定義的初始記憶體狀態 `CMemoryState` 。

*newState*<br/>
檢查點所定義的新記憶體狀態 `CMemoryState` 。

### <a name="return-value"></a>傳回值

如果兩個記憶體狀態不同，則為非零。否則為0。

### <a name="remarks"></a>備註

必須針對兩個記憶體狀態參數呼叫[檢查點](#checkpoint)。

### <a name="example"></a>範例

  請參閱 [CMemoryState](#cmemorystate) 函式的範例。

## <a name="cmemorystatedumpallobjectssince"></a><a name="dumpallobjectssince"></a> CMemoryState：:D umpAllObjectsSince

`Dump`針對衍生自類別的所有類型物件呼叫函式 `CObject` ，這些物件是從配置 (，而且仍會在此物件的最後一個[檢查點](#checkpoint)呼叫之後配置) `CMemoryState` 。

```cpp
void DumpAllObjectsSince() const;
```

### <a name="remarks"></a>備註

`DumpAllObjectsSince`使用未初始化的 `CMemoryState` 物件來呼叫，將會傾印目前在記憶體中的所有物件。

### <a name="example"></a>範例

  請參閱 [CMemoryState](#cmemorystate) 函式的範例。

## <a name="cmemorystatedumpstatistics"></a><a name="dumpstatistics"></a> CMemoryState：:D umpStatistics

從差異成員函式所填滿的物件列印精簡的記憶體統計資料包表 `CMemoryState` 。 [Difference](#difference)

```cpp
void DumpStatistics() const;
```

### <a name="remarks"></a>備註

報表會列印在 [afxDump](diagnostic-services.md#afxdump) 裝置上，如下所示：

範例報表會提供 (或數量) 的資訊：

- 免費區塊

- 一般區塊

- CRT 區塊

- 忽略區塊

- 用戶端區塊

- 程式在任何一次使用的最大記憶體 (位元組) 

- 程式目前使用的記憶體總計 (位元組) 

如果設定為，可用區塊就是其解除配置延遲的區塊數目 `afxMemDF` `delayFreeMemDF` 。 如需詳細資訊，請參閱「MFC 宏和全域」一節中的 [afxMemDF](diagnostic-services.md#afxmemdf)。

### <a name="example"></a>範例

  下列程式碼應該放在 *projname*應用程式 .cpp 中。 定義下列全域變數：

[!code-cpp[NVC_MFC_Utilities#40](../../mfc/codesnippet/cpp/cmemorystate-structure_2.cpp)]

在函式中 `InitInstance` ，加入下列程式程式碼：

[!code-cpp[NVC_MFC_Utilities#41](../../mfc/codesnippet/cpp/cmemorystate-structure_3.cpp)]

新增函式的處理常式 `ExitInstance` ，並使用下列程式碼：

[!code-cpp[NVC_MFC_Utilities#42](../../mfc/codesnippet/cpp/cmemorystate-structure_4.cpp)]

您現在可以在「偵錯工具模式」中執行程式，以查看函式的輸出 `DumpStatistics` 。

## <a name="see-also"></a>另請參閱

[階層架構圖表](../../mfc/hierarchy-chart.md)
