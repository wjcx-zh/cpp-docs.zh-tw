---
title: CSyncObject 類別
ms.date: 11/04/2016
f1_keywords:
- CSyncObject
- AFXMT/CSyncObject
- AFXMT/CSyncObject::CSyncObject
- AFXMT/CSyncObject::Lock
- AFXMT/CSyncObject::Unlock
- AFXMT/CSyncObject::m_hObject
helpviewer_keywords:
- CSyncObject [MFC], CSyncObject
- CSyncObject [MFC], Lock
- CSyncObject [MFC], Unlock
- CSyncObject [MFC], m_hObject
ms.assetid: c62ea6eb-a17b-4e01-aed4-321fc435a5f4
ms.openlocfilehash: ebfbc185cdca2effc96ce2e6d96d05f997c52bf7
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81365976"
---
# <a name="csyncobject-class"></a>CSyncObject 類別

在 Win32 中提供同步處理物件常見功能的純虛擬類別。

## <a name="syntax"></a>語法

```
class CSyncObject : public CObject
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[CSync 物件:CSync物件](#csyncobject)|建構 `CSyncObject` 物件。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CSync 物件:鎖定](#lock)|獲得對同步對象的訪問許可權。|
|[CSync 物件:解鎖](#unlock)|獲得對同步對象的訪問許可權。|

### <a name="public-operators"></a>公用運算子

|名稱|描述|
|----------|-----------------|
|[CSync物件::操作員HANDLE](#operator_handle)|提供對同步對象的訪問。|

### <a name="public-data-members"></a>公用資料成員

|名稱|描述|
|----------|-----------------|
|[CSync 物件:m_hObject](#m_hobject)|基礎同步物件的句柄。|

## <a name="remarks"></a>備註

Microsoft 基礎類庫提供`CSyncObject`來自的多個類。 這些是[CEvent,CMutex,C](../../mfc/reference/cmutex-class.md)[臨界截面](../../mfc/reference/ccriticalsection-class.md),和[CSemaphore。](../../mfc/reference/csemaphore-class.md) [CEvent](../../mfc/reference/cevent-class.md)

有關如何使用同步物件的資訊,請參閱"[多線程:如何使用同步類](../../parallel/multithreading-how-to-use-the-synchronization-classes.md)「一文。

## <a name="inheritance-hierarchy"></a>繼承階層架構

[CObject](../../mfc/reference/cobject-class.md)

`CSyncObject`

## <a name="requirements"></a>需求

**標題:** afxmt.h

## <a name="csyncobjectcsyncobject"></a><a name="csyncobject"></a>CSync 物件:CSync物件

建構具有提供名稱的同步物件。

```
explicit CSyncObject(LPCTSTR pstrName);
virtual ~CSyncObject();
```

### <a name="parameters"></a>參數

*pstrName*<br/>
物件的名稱。 如果為 NULL,*則 pstrName*將為空。

## <a name="csyncobjectlock"></a><a name="lock"></a>CSync 物件:鎖定

調用此函數以訪問由同步物件控制的資源。

```
virtual BOOL Lock(DWORD dwTimeout = INFINITE);
```

### <a name="parameters"></a>參數

*dwTimeout*<br/>
指定等待同步物件可用(信號)的時間量(以毫秒為單位)。 如果 INFINITE,`Lock`將等待物件發出信號後再返回。

### <a name="return-value"></a>傳回值

如果函數成功,則非零;否則 0。

### <a name="remarks"></a>備註

如果同步物件發出信號,`Lock`將成功返回,並且線程現在擁有該物件。 如果同步物件是非信號(不可用),`Lock`則將等待同步物件發出信號,最多達到*dwTimeOut*參數中指定的毫秒數。 如果同步物件未在指定的時間內發出信號,則`Lock`返回失敗。

## <a name="csyncobjectm_hobject"></a><a name="m_hobject"></a>CSync 物件:m_hObject

基礎同步物件的句柄。

```
HANDLE m_hObject;
```

## <a name="csyncobjectoperator-handle"></a><a name="operator_handle"></a>CSync物件::操作員HANDLE

使用此運算元獲取`CSyncObject`物件的句柄。

```
operator HANDLE() const;
```

### <a name="return-value"></a>傳回值

如果成功,則處理同步物件的句柄;否則,NULL。

### <a name="remarks"></a>備註

您可以使用該句柄直接呼叫 Windows API。

## <a name="csyncobjectunlock"></a><a name="unlock"></a>CSync 物件:解鎖

`Unlock`無參數的聲明是純虛擬函數,必須由派生自`CSyncObject`的所有類重寫。

```
virtual BOOL Unlock() = 0; virtual BOOL Unlock(
    LONG lCount,
    LPLONG lpPrevCount = NULL);
```

### <a name="parameters"></a>參數

*l. Count*<br/>
默認情況下不使用實現。

*lpPrev( A) Counts*<br/>
默認情況下不使用實現。

### <a name="return-value"></a>傳回值

預設實現始終返回 TRUE。

### <a name="remarks"></a>備註

具有兩個參數的聲明的預設實現始終返回 TRUE。 調用此函數是為了釋放對調用線程擁有的同步物件的訪問。 第二個聲明用於同步物件,如允許對受控資源的多個訪問許可權的信號量。

## <a name="see-also"></a>另請參閱

[CObject 類別](../../mfc/reference/cobject-class.md)<br/>
[階層架構圖表](../../mfc/hierarchy-chart.md)
