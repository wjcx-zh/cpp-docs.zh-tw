---
title: CCriticalSection 類別
ms.date: 11/04/2016
f1_keywords:
- CCriticalSection
- AFXMT/CCriticalSection
- AFXMT/CCriticalSection::CCriticalSection
- AFXMT/CCriticalSection::Lock
- AFXMT/CCriticalSection::Unlock
- AFXMT/CCriticalSection::m_sect
helpviewer_keywords:
- CCriticalSection [MFC], CCriticalSection
- CCriticalSection [MFC], Lock
- CCriticalSection [MFC], Unlock
- CCriticalSection [MFC], m_sect
ms.assetid: f776f74b-5b0b-4f32-9c13-2b8e4a0d7b2b
ms.openlocfilehash: d79199a332f6930619e6b4995b04bc590b6ea580
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81369369"
---
# <a name="ccriticalsection-class"></a>CCriticalSection 類別

表示「關鍵部分」 - 一個同步物件,允許一次一個線程存取資源或代碼部分。

## <a name="syntax"></a>語法

```
class CCriticalSection : public CSyncObject
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[C關鍵部份:C關鍵節](#ccriticalsection)|建構 `CCriticalSection` 物件。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[C 關鍵部份:鎖定](#lock)|用於訪問`CCriticalSection`物件。|
|[C關鍵部份:解鎖](#unlock)|釋出 `CCriticalSection` 物件。|

### <a name="public-operators"></a>公用運算子

|名稱|描述|
|----------|-----------------|
|[C關鍵部分::操作員CRITICAL_SECTION*](#operator_critical_section_star)|檢索指向內部CRITICAL_SECTION物件的指標。|

### <a name="public-data-members"></a>公用資料成員

|名稱|描述|
|----------|-----------------|
|[C關鍵節::m_sect](#m_sect)|物件CRITICAL_SECTION。|

## <a name="remarks"></a>備註

當一次只允許一個線程修改數據或其他受控資源時,關鍵部分非常有用。 例如,將節點添加到連結清單是一個一次只能由一個線程允許的過程。 通過使用`CCriticalSection`物件來控制連結清單,一次只能訪問一個線程。

> [!NOTE]
> `CCriticalSection`類的功能由實際的 Win32 CRITICAL_SECTION物件提供。

當速度至關重要且資源不會跨進程邊界使用時,將使用關鍵部分代替互斥(請參閱[CMutex)。](../../mfc/reference/cmutex-class.md)

使用`CCriticalSection`物件有兩種方法:獨立和嵌入類。

- 獨立方法 使用`CCriticalSection`獨立 物件,在需要時`CCriticalSection`構造 該物件。 從建構函數成功傳回後,顯示式鎖定物件,呼叫[鎖定](#lock)。 存取關鍵部份後,呼[叫解鎖](#unlock)。 此方法雖然對讀取原始程式碼的人更清晰,但更容易出錯,因為您必須記住在訪問前後鎖定和解鎖關鍵部分。

   更可取的方法是使用[CSingleLock](../../mfc/reference/csinglelock-class.md)類。 它還具有`Lock``Unlock`和方法,但如果發生異常,您不必擔心解鎖資源。

- 嵌入式方法 您還可以透過向類中`CCriticalSection`添加 -type 資料成員並在需要時鎖定數據成員,與多個線程共用類。

有關使用`CCriticalSection`物件的詳細資訊,請參閱"[多線程:如何使用同步類](../../parallel/multithreading-how-to-use-the-synchronization-classes.md)「一文。

## <a name="inheritance-hierarchy"></a>繼承階層架構

[CObject](../../mfc/reference/cobject-class.md)

[CSyncObject](../../mfc/reference/csyncobject-class.md)

`CCriticalSection`

## <a name="requirements"></a>需求

**標題:** afxmt.h

## <a name="ccriticalsectionccriticalsection"></a><a name="ccriticalsection"></a>C關鍵部份:C關鍵節

建構 `CCriticalSection` 物件。

```
CCriticalSection();
```

### <a name="remarks"></a>備註

要存`CCriticalSection`取 或釋放物件,請創建一個[CSingleLock](../../mfc/reference/csinglelock-class.md)物件,並調用其[鎖定](../../mfc/reference/csinglelock-class.md#lock)和[解鎖](../../mfc/reference/csinglelock-class.md#unlock)成員函數。 如果對`CCriticalSection`像是獨立使用的,請調用其[Unlock](#unlock)成員函數以釋放它。

如果建構函數無法分配所需的系統記憶體,將自動引發記憶體異常[(CMemoryException](../../mfc/reference/cmemoryexception-class.md)類型)。

### <a name="example"></a>範例

  請參考[C 關鍵節的範例:鎖定](#lock)。

## <a name="ccriticalsectionlock"></a><a name="lock"></a>C 關鍵部份:鎖定

調用此成員函數以訪問關鍵部分物件。

```
BOOL Lock();
BOOL Lock(DWORD dwTimeout);
```

### <a name="parameters"></a>參數

*dwTimeout*<br/>
`Lock`忽略此參數值。

### <a name="return-value"></a>傳回值

如果函數成功,則非零;否則 0。

### <a name="remarks"></a>備註

`Lock`是阻塞調用,在關鍵截面物件發出信號(變為可用)之前不會返回。

如果需要時等待時間,可以使用[CMutex](../../mfc/reference/cmutex-class.md)`CCriticalSection`物件而不是 物件。

如果`Lock`無法分配必要的系統記憶體,將自動引發記憶體異常[(CMemory Exception](../../mfc/reference/cmemoryexception-class.md)類型)。

### <a name="example"></a>範例

此示例演示嵌套關鍵部分方法,方法是使用共用`_strShared``CCriticalSection`物件控制對共用資源(靜態物件)的訪問。 該`SomeMethod`函數演示以安全的方式更新共享資源。

[!code-cpp[NVC_MFC_Utilities#11](../../mfc/codesnippet/cpp/ccriticalsection-class_1.h)]

## <a name="ccriticalsectionm_sect"></a><a name="m_sect"></a>C關鍵節::m_sect

包含所有`CCriticalSection`方法使用的關鍵節物件。

```
CRITICAL_SECTION m_sect;
```

## <a name="ccriticalsectionoperator-critical_section"></a><a name="operator_critical_section_star"></a>C關鍵部分::操作員CRITICAL_SECTION*

檢索CRITICAL_SECTION物件。

```
operator CRITICAL_SECTION*();
```

### <a name="remarks"></a>備註

調用此函數以檢索指向內部CRITICAL_SECTION物件的指標。

## <a name="ccriticalsectionunlock"></a><a name="unlock"></a>C關鍵部份:解鎖

釋放`CCriticalSection`物件以供另一個線程使用。

```
BOOL Unlock();
```

### <a name="return-value"></a>傳回值

如果`CCriticalSection`物件為線程所有且釋放成功,則非零;否則 0。

### <a name="remarks"></a>備註

如果正在`CCriticalSection`獨立使用`Unlock`, 則必須在完成關鍵部分控制的資源的使用後立即調用。 如果使用[CSingleLock](../../mfc/reference/csinglelock-class.md)`CCriticalSection::Unlock`物件,`Unlock`則鎖定物件的成員函數將調用該物件。

### <a name="example"></a>範例

  請參考[C 關鍵節的範例:鎖定](#lock)。

## <a name="see-also"></a>另請參閱

[CSyncObject 類別](../../mfc/reference/csyncobject-class.md)<br/>
[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[CMutex 類別](../../mfc/reference/cmutex-class.md)
