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
ms.openlocfilehash: 2c89647afc8a9a8c6564d25afe20d48818a643f2
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62385374"
---
# <a name="ccriticalsection-class"></a>CCriticalSection 類別

代表 「 關鍵區段 」 — 允許一個執行緒存取資源或程式碼區段，一次同步處理物件。

## <a name="syntax"></a>語法

```
class CCriticalSection : public CSyncObject
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[CCriticalSection::CCriticalSection](#ccriticalsection)|建構 `CCriticalSection` 物件。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CCriticalSection::Lock](#lock)|用來存取`CCriticalSection`物件。|
|[CCriticalSection::Unlock](#unlock)|釋出 `CCriticalSection` 物件。|

### <a name="public-operators"></a>公用運算子

|名稱|描述|
|----------|-----------------|
|[CCriticalSection::operator CRITICAL_SECTION *](#operator_critical_section_star)|擷取內部的 CRITICAL_SECTION 物件的指標。|

### <a name="public-data-members"></a>公用資料成員

|名稱|描述|
|----------|-----------------|
|[CCriticalSection::m_sect](#m_sect)|CRITICAL_SECTION 物件。|

## <a name="remarks"></a>備註

一次只有一個執行緒可以修改資料或其他一些受控制的資源時，則關鍵區段會很有用。 例如，將節點新增至連結的清單是應該只能由一個執行緒使用，一次的處理程序。 使用`CCriticalSection`控制連結的清單中，只有一次一個執行緒可以存取清單的物件。

> [!NOTE]
>  功能`CCriticalSection`類別由實際的 Win32 CRITICAL_SECTION 物件提供。

Mutex 不會使用的重要區段 (請參閱[CMutex](../../mfc/reference/cmutex-class.md)) 時的速度非常重要，且資源將不會使用跨處理序界限。

有兩種方法使用`CCriticalSection`物件： 獨立和內嵌類別中。

- 獨立的方法，以使用獨立`CCriticalSection`物件，建構`CCriticalSection`物件時需要它。 之後從建構函式成功傳回時，明確地鎖定的物件呼叫[鎖定](#lock)。 呼叫[Unlock](#unlock)完成時存取重要區段。 此方法，並清楚給其他人讀取您的原始程式碼，是更容易發生錯誤，您必須記得鎖定和解除鎖定重要區段之前, 和之後存取。

   更適合的方法是使用[CSingleLock](../../mfc/reference/csinglelock-class.md)類別。 它也有`Lock`和`Unlock`方法，但您不需要擔心如何解除鎖定的資源，如果發生例外狀況。

- 內嵌方法，您也可以共用多個執行緒的類別，藉由新增`CCriticalSection`-類別和鎖定時所需的資料成員的型別資料成員。

如需有關使用`CCriticalSection`物件，請參閱文章[多執行緒：如何使用同步類別](../../parallel/multithreading-how-to-use-the-synchronization-classes.md)。

## <a name="inheritance-hierarchy"></a>繼承階層

[CObject](../../mfc/reference/cobject-class.md)

[CSyncObject](../../mfc/reference/csyncobject-class.md)

`CCriticalSection`

## <a name="requirements"></a>需求

**標頭：** afxmt.h

##  <a name="ccriticalsection"></a>  CCriticalSection::CCriticalSection

建構 `CCriticalSection` 物件。

```
CCriticalSection();
```

### <a name="remarks"></a>備註

存取或釋放`CCriticalSection`物件，建立[CSingleLock](../../mfc/reference/csinglelock-class.md)物件，然後呼叫其[鎖定](../../mfc/reference/csinglelock-class.md#lock)並[解除鎖定](../../mfc/reference/csinglelock-class.md#unlock)成員函式。 如果`CCriticalSection`物件正在使用獨立的工作，請呼叫其[Unlock](#unlock)釋放它的成員函式。

如果建構函式，就無法配置所需的系統記憶體，而記憶體的例外狀況 (型別的[CMemoryException](../../mfc/reference/cmemoryexception-class.md)) 會自動擲回。

### <a name="example"></a>範例

  範例，請參閱[CCriticalSection::Lock](#lock)。

##  <a name="lock"></a>  CCriticalSection::Lock

呼叫此成員函式，以取得重要區段物件的存取權。

```
BOOL Lock();
BOOL Lock(DWORD dwTimeout);
```

### <a name="parameters"></a>參數

*dwTimeout*<br/>
`Lock` 會忽略此參數值。

### <a name="return-value"></a>傳回值

如果函式時成功則為非零否則為 0。

### <a name="remarks"></a>備註

`Lock` 是一個封鎖呼叫，直到收到信號的重要區段物件將不會傳回 （會變成可用）。

如果逾時的等待時間是必要的您可以使用[CMutex](../../mfc/reference/cmutex-class.md)物件，而不是`CCriticalSection`物件。

如果`Lock`無法配置所需的系統記憶體，記憶體的例外狀況 (型別的[CMemoryException](../../mfc/reference/cmemoryexception-class.md)) 會自動擲回。

### <a name="example"></a>範例

此範例會示範巢狀的重要區段法藉由控制共用資源的存取權 (靜態`_strShared`物件) 使用共用`CCriticalSection`物件。 `SomeMethod`函式示範，如何以安全的方式更新共用的資源。

[!code-cpp[NVC_MFC_Utilities#11](../../mfc/codesnippet/cpp/ccriticalsection-class_1.h)]

##  <a name="m_sect"></a>  CCriticalSection::m_sect

包含所有使用的重要區段物件`CCriticalSection`方法。

```
CRITICAL_SECTION m_sect;
```

##  <a name="operator_critical_section_star"></a>  CCriticalSection::operator CRITICAL_SECTION *

擷取一個 CRITICAL_SECTION 物件。

```
operator CRITICAL_SECTION*();
```

### <a name="remarks"></a>備註

呼叫此函式可擷取內部的 CRITICAL_SECTION 物件的指標。

##  <a name="unlock"></a>  CCriticalSection::Unlock

版本`CCriticalSection`以供另一個執行緒的物件。

```
BOOL Unlock();
```

### <a name="return-value"></a>傳回值

非零`CCriticalSection`物件由執行緒自己所擁有並發行已成功，否則為 0。

### <a name="remarks"></a>備註

如果`CCriticalSection`正在使用獨立式、`Unlock`必須完成使用重要區段所控制的資源之後立即呼叫。 如果[CSingleLock](../../mfc/reference/csinglelock-class.md)正在使用物件，`CCriticalSection::Unlock`鎖定物件會呼叫`Unlock`成員函式。

### <a name="example"></a>範例

  範例，請參閱[CCriticalSection::Lock](#lock)。

## <a name="see-also"></a>另請參閱

[CSyncObject 類別](../../mfc/reference/csyncobject-class.md)<br/>
[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[CMutex 類別](../../mfc/reference/cmutex-class.md)
