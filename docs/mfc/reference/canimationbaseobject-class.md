---
title: CAnimationBaseObject 類別
ms.date: 03/27/2019
f1_keywords:
- CAnimationBaseObject
- AFXANIMATIONCONTROLLER/CAnimationBaseObject
- AFXANIMATIONCONTROLLER/CAnimationBaseObject::CAnimationBaseObject
- AFXANIMATIONCONTROLLER/CAnimationBaseObject::ApplyTransitions
- AFXANIMATIONCONTROLLER/CAnimationBaseObject::ClearTransitions
- AFXANIMATIONCONTROLLER/CAnimationBaseObject::ContainsVariable
- AFXANIMATIONCONTROLLER/CAnimationBaseObject::CreateTransitions
- AFXANIMATIONCONTROLLER/CAnimationBaseObject::DetachFromController
- AFXANIMATIONCONTROLLER/CAnimationBaseObject::EnableIntegerValueChangedEvent
- AFXANIMATIONCONTROLLER/CAnimationBaseObject::EnableValueChangedEvent
- AFXANIMATIONCONTROLLER/CAnimationBaseObject::GetAutodestroyTransitions
- AFXANIMATIONCONTROLLER/CAnimationBaseObject::GetGroupID
- AFXANIMATIONCONTROLLER/CAnimationBaseObject::GetObjectID
- AFXANIMATIONCONTROLLER/CAnimationBaseObject::GetUserData
- AFXANIMATIONCONTROLLER/CAnimationBaseObject::SetAutodestroyTransitions
- AFXANIMATIONCONTROLLER/CAnimationBaseObject::SetID
- AFXANIMATIONCONTROLLER/CAnimationBaseObject::SetUserData
- AFXANIMATIONCONTROLLER/CAnimationBaseObject::GetAnimationVariableList
- AFXANIMATIONCONTROLLER/CAnimationBaseObject::SetParentAnimationObjects
- AFXANIMATIONCONTROLLER/CAnimationBaseObject::m_bAutodestroyTransitions
- AFXANIMATIONCONTROLLER/CAnimationBaseObject::m_dwUserData
- AFXANIMATIONCONTROLLER/CAnimationBaseObject::m_nGroupID
- AFXANIMATIONCONTROLLER/CAnimationBaseObject::m_nObjectID
- AFXANIMATIONCONTROLLER/CAnimationBaseObject::m_pParentController
helpviewer_keywords:
- CAnimationBaseObject [MFC], CAnimationBaseObject
- CAnimationBaseObject [MFC], ApplyTransitions
- CAnimationBaseObject [MFC], ClearTransitions
- CAnimationBaseObject [MFC], ContainsVariable
- CAnimationBaseObject [MFC], CreateTransitions
- CAnimationBaseObject [MFC], DetachFromController
- CAnimationBaseObject [MFC], EnableIntegerValueChangedEvent
- CAnimationBaseObject [MFC], EnableValueChangedEvent
- CAnimationBaseObject [MFC], GetAutodestroyTransitions
- CAnimationBaseObject [MFC], GetGroupID
- CAnimationBaseObject [MFC], GetObjectID
- CAnimationBaseObject [MFC], GetUserData
- CAnimationBaseObject [MFC], SetAutodestroyTransitions
- CAnimationBaseObject [MFC], SetID
- CAnimationBaseObject [MFC], SetUserData
- CAnimationBaseObject [MFC], GetAnimationVariableList
- CAnimationBaseObject [MFC], SetParentAnimationObjects
- CAnimationBaseObject [MFC], m_bAutodestroyTransitions
- CAnimationBaseObject [MFC], m_dwUserData
- CAnimationBaseObject [MFC], m_nGroupID
- CAnimationBaseObject [MFC], m_nObjectID
- CAnimationBaseObject [MFC], m_pParentController
ms.assetid: 76b25917-940e-4eba-940f-31d270702603
ms.openlocfilehash: 1874ddfdd26b8dd371e32f7e68ea8f668c47d8e1
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/22/2020
ms.locfileid: "81750217"
---
# <a name="canimationbaseobject-class"></a>CAnimationBaseObject 類別

所有動畫物件的基底類別。

## <a name="syntax"></a>語法

```
class CAnimationBaseObject : public CObject;
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[動畫基礎物件::動畫基物件](#canimationbaseobject)|已多載。 構造動畫物件。|
|[動畫基物件::_C動畫基物件](#_dtorcanimationbaseobject)|解構函式。 銷毀動畫物件時調用。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[動畫基礎物件::應用轉換](#applytransitions)|使用封裝的動畫變數將過渡添加到情節提要。|
|[動畫基礎物件::清除轉換](#cleartransitions)|刪除所有相關轉換。|
|[動畫基礎物件::包含變數](#containsvariable)|確定動畫物件是否包含特定的動畫變數。|
|[動畫基礎物件::建立轉換](#createtransitions)|創建與動畫物件關聯的過渡。|
|[動畫基礎物件::D從控制器](#detachfromcontroller)|從父動畫控制器分離動畫物件。|
|[動畫基礎物件::啟用整數值更改事件](#enableintegervaluechangedevent)|設置整數值已更改事件處理程式。|
|[動畫基礎物件::啟用值變更事件](#enablevaluechangedevent)|設置值更改的事件處理程式。|
|[動畫基礎物件::取得自動銷毀轉換](#getautodestroytransitions)|告訴相關轉換是否自動銷毀。|
|[動畫基礎物件:取得群體 ID](#getgroupid)|返回當前組ID。|
|[動畫基礎物件::獲取物件ID](#getobjectid)|返回當前對象識別碼。|
|[動畫基礎物件:取得使用者資料](#getuserdata)|返回用戶定義的數據。|
|[動畫基礎物件::設定自動銷毀轉換](#setautodestroytransitions)|設置標誌以自動銷毀過渡。|
|[動畫基礎物件::SetID](#setid)|設置新指示。|
|[動畫基礎物件::設定使用者資料](#setuserdata)|設置使用者定義的數據。|

### <a name="protected-methods"></a>保護方法

|名稱|描述|
|----------|-----------------|
|[動畫基礎物件::取得動畫變數清單](#getanimationvariablelist)|收集指向包含的動畫變數的指標。|
|[動畫基礎物件::設定父動畫物件](#setparentanimationobjects)|建立動畫物件中包含的動畫變數與其容器之間的關係。|

### <a name="protected-data-members"></a>受保護的資料成員

|名稱|描述|
|----------|-----------------|
|[動畫基礎物件::m_bAutodestroyTransitions](#m_bautodestroytransitions)|指定是否應自動銷毀相關轉換。|
|[動畫基礎物件::m_dwUserData](#m_dwuserdata)|存儲使用者定義的數據。|
|[動畫基礎物件::m_nGroupID](#m_ngroupid)|指定動畫物件的組識別碼。|
|[動畫基礎物件::m_nObjectID](#m_nobjectid)|指定動畫物件的物件識別碼。|
|[動畫基礎物件::m_pParentController](#m_pparentcontroller)|指向父動畫控制器的指標。|

## <a name="remarks"></a>備註

此類為所有動畫對象實現基本方法。 動畫物件可以表示應用程式中的值、點、大小、矩形或顏色,以及任何自定義實體。 動畫物件存儲在動畫組中(請參閱 C 動畫組)。 每個組可以單獨進行動畫處理,也可以被視為情節提要的類比。 動畫物件封裝一個或多個動畫變數(請參閱 CAnvariable),具體取決於其邏輯表示形式。 例如,CAnimationRect 包含四個動畫變數 - 矩形每側一個變數。 每個動畫物件類公開重載的 AddTransition 方法,該方法應用於將過渡應用於封裝的動畫變數。 動畫物件可以通過物件 ID(可選)和組 ID 標識。 要放置動畫物件以更正組,需要組 ID,但如果未指定組 ID,則物件將放置在 ID 0 的預設組中。 如果使用不同的 GroupID 調用 SetID,動畫物件將移動到另一個組(如有必要,將創建新組)。

## <a name="inheritance-hierarchy"></a>繼承階層架構

[CObject](../../mfc/reference/cobject-class.md)

`CAnimationBaseObject`

## <a name="requirements"></a>需求

**標頭：** afxanimationcontroller.h

## <a name="canimationbaseobjectcanimationbaseobject"></a><a name="_dtorcanimationbaseobject"></a>動畫基物件::_C動畫基物件

解構函式。 銷毀動畫物件時調用。

```
virtual ~CAnimationBaseObject();
```

## <a name="canimationbaseobjectapplytransitions"></a><a name="applytransitions"></a>動畫基礎物件::應用轉換

使用封裝的動畫變數將過渡添加到情節提要。

```
virtual BOOL ApplyTransitions(
    IUIAnimationStoryboard* pStoryboard,
    BOOL bDependOnKeyframes);
```

### <a name="parameters"></a>參數

*板*<br/>
指向情節提要的指標。

*bDependon 關鍵幀*<br/>
當 FALSE 時,此方法僅添加不依賴於關鍵幀的轉換。

### <a name="return-value"></a>傳回值

如果成功添加了轉換,則為 TRUE。

### <a name="remarks"></a>備註

將使用 AddTransition(派生類中重載方法)添加到情節提要的相關轉換。

## <a name="canimationbaseobjectcanimationbaseobject"></a><a name="canimationbaseobject"></a>動畫基礎物件::動畫基物件

構造動畫物件。

```
CAnimationBaseObject();

CAnimationBaseObject(
    UINT32 nGroupID,
    UINT32 nObjectID = (UINT32)-1,
    DWORD dwUserData = 0);
```

### <a name="parameters"></a>參數

*n集團ID*<br/>
指定組識別碼。

*nObjectID*<br/>
指定物件識別碼。

*dwUserData*<br/>
使用者定義的數據,這些數據可以與動畫物件關聯,並在運行時稍後檢索。

### <a name="remarks"></a>備註

建構動畫物件並分配預設物件 ID (0) 和組 ID (0)。

## <a name="canimationbaseobjectcleartransitions"></a><a name="cleartransitions"></a>動畫基礎物件::清除轉換

刪除所有相關轉換。

```
virtual void ClearTransitions(BOOL bAutodestroy);
```

### <a name="parameters"></a>參數

*b 自動銷毀*<br/>
指定是自動銷毀過渡物件,還是僅將其從相關列表中刪除。

### <a name="remarks"></a>備註

刪除所有相關轉換,並在 bAuto銷毀或m_bAutodestroyTransitions標誌為 TRUE 時銷毀它們。 僅當轉換未在堆疊上分配時,才應自動銷毀這些轉換。 如果上述標誌為 FALSE,則只會從相關轉換的內部清單中刪除轉換。

## <a name="canimationbaseobjectcontainsvariable"></a><a name="containsvariable"></a>動畫基礎物件::包含變數

確定動畫物件是否包含特定的動畫變數。

```
virtual BOOL ContainsVariable(IUIAnimationVariable* pVariable);
```

### <a name="parameters"></a>參數

*pvariable*<br/>
指向動畫變數的指標。

### <a name="return-value"></a>傳回值

如果動畫變數包含在動畫物件中,則為 TRUE;如果動畫變數包含在動畫物件中,則為 TRUE。否則 FALSE。

### <a name="remarks"></a>備註

此方法可用於確定 pVariable 指定的動畫變數是否包含在動畫物件中。 動畫物件(根據其類型)可能包含多個動畫變數。 例如,CAnimationColor 包含三個變數,每個顏色元件(紅色、綠色和藍色)一個。 當動畫變數的值發生更改時,Windows 動畫 API 將發送 Value"更改"或「整數值更改」事件(如果啟用),此事件的參數是指向動畫變數的介面 IUIAnimationvariable 的指標。 此方法有助於從指標獲取指向包含的 COM 物件的動畫指標。

## <a name="canimationbaseobjectcreatetransitions"></a><a name="createtransitions"></a>動畫基礎物件::建立轉換

創建與動畫物件關聯的過渡。

```
BOOL CreateTransitions();
```

### <a name="return-value"></a>傳回值

如果成功創建轉換,則為 TRUE;否則 FALSE。

### <a name="remarks"></a>備註

迴圈在派生動畫物件中封裝的動畫變數清單,並創建與每個動畫變數關聯的過渡。

## <a name="canimationbaseobjectdetachfromcontroller"></a><a name="detachfromcontroller"></a>動畫基礎物件::D從控制器

從父動畫控制器分離動畫物件。

```cpp
void DetachFromController();
```

### <a name="remarks"></a>備註

此方法在內部使用。

## <a name="canimationbaseobjectenableintegervaluechangedevent"></a><a name="enableintegervaluechangedevent"></a>動畫基礎物件::啟用整數值更改事件

設置整數值已更改事件處理程式。

```
virtual void EnableIntegerValueChangedEvent(
    CAnimationController* pController,
    BOOL bEnable);
```

### <a name="parameters"></a>參數

*pController*<br/>
指向父控制器的指標。

*b 啟用*<br/>
指定是啟用還是禁用整數值更改事件。

### <a name="remarks"></a>備註

如果啟用了整數值更改事件處理程式,則可以在 CAnimationController::onAnimationIntegerValue"更改"方法中處理此事件,該方法應在 CAnimationController 派生類中重寫。 每次更改動畫整數值時,都會調用此方法。

## <a name="canimationbaseobjectenablevaluechangedevent"></a><a name="enablevaluechangedevent"></a>動畫基礎物件::啟用值變更事件

設置值更改的事件處理程式。

```
virtual void EnableValueChangedEvent(
    CAnimationController* pController,
    BOOL bEnable);
```

### <a name="parameters"></a>參數

*pController*<br/>
指向父控制器的指標。

*b 啟用*<br/>
指定是啟用還是禁用"值更改" 事件。

### <a name="remarks"></a>備註

如果啟用了"值更改"事件處理程式,則可以在 CAnimationController::onAnimationValue 更改方法中處理此事件,該方法應在 CAnimationController 派生類中重寫。 每次動畫值更改時,都會調用此方法。

## <a name="canimationbaseobjectgetanimationvariablelist"></a><a name="getanimationvariablelist"></a>動畫基礎物件::取得動畫變數清單

收集指向包含的動畫變數的指標。

```
virtual void GetAnimationVariableList(
    CList<CAnimationVariable*,
    CAnimationVariable*>& list) = 0;
```

### <a name="parameters"></a>參數

list<br/>
必須填充動畫物件中包含的動畫變數的清單。

### <a name="remarks"></a>備註

必須在派生類中重寫此純虛擬方法。 動畫物件(根據其類型)包含一個或多個動畫變數。 例如,CAnimationPoint 包含兩個變數,分別用於 X 和 Y 座標。 基本類 CAnimationBaseObject 實現一些泛型方法,這些方法作用於動畫變數清單:應用轉換、清除轉換、啟用價值更改事件、啟用 IntegerValue 更改事件。 這些方法稱為 GetAnimationvariableList,它填充在派生類中,其中包含特定動畫物件中包含的實際動畫變數,然後迴圈訪問列表並執行必要的操作。 如果創建自定義動畫物件,則必須添加到*列出*該物件中包含的所有動畫變數。

## <a name="canimationbaseobjectgetautodestroytransitions"></a><a name="getautodestroytransitions"></a>動畫基礎物件::取得自動銷毀轉換

告訴相關轉換是否自動銷毀。

```
BOOL GetAutodestroyTransitions() const;
```

### <a name="return-value"></a>傳回值

如果為 TRUE,則相關轉換將自動銷毀;如果為 TRUE,則會自動銷毀相關轉換。如果 FALSE,則轉換物件應通過調用應用程式進行處理。

### <a name="remarks"></a>備註

預設情況下,此標誌為 TRUE。 僅當在堆疊上分配過渡和/或轉換應由調用應用程式處理時,才設置此標誌。

## <a name="canimationbaseobjectgetgroupid"></a><a name="getgroupid"></a>動畫基礎物件:取得群體 ID

返回當前組ID。

```
UINT32 GetGroupID() const;
```

### <a name="return-value"></a>傳回值

當前組 ID。

### <a name="remarks"></a>備註

使用此方法檢索組 ID。 如果組 ID 未在建構函數中或 SetID 中顯式設置,則為 0。

## <a name="canimationbaseobjectgetobjectid"></a><a name="getobjectid"></a>動畫基礎物件::獲取物件ID

返回當前對象識別碼。

```
UINT32 GetObjectID() const;
```

### <a name="return-value"></a>傳回值

當前對象識別碼。

### <a name="remarks"></a>備註

使用此方法檢索對象 ID。 如果物件 ID 未在建構函數中或 SetID 中顯式設置,則為 0。

## <a name="canimationbaseobjectgetuserdata"></a><a name="getuserdata"></a>動畫基礎物件:取得使用者資料

返回用戶定義的數據。

```
DWORD GetUserData() const;
```

### <a name="return-value"></a>傳回值

自定義數據的值。

### <a name="remarks"></a>備註

調用此方法以在運行時檢索自定義數據。 如果在建構函數或使用 SetUserData 中顯式初始化該值,則返回的值將為 0。

## <a name="canimationbaseobjectm_bautodestroytransitions"></a><a name="m_bautodestroytransitions"></a>動畫基礎物件::m_bAutodestroyTransitions

指定是否應自動銷毀相關轉換。

```
BOOL m_bAutodestroyTransitions;
```

## <a name="canimationbaseobjectm_dwuserdata"></a><a name="m_dwuserdata"></a>動畫基礎物件::m_dwUserData

存儲使用者定義的數據。

```
DWORD m_dwUserData;
```

## <a name="canimationbaseobjectm_ngroupid"></a><a name="m_ngroupid"></a>動畫基礎物件::m_nGroupID

指定動畫物件的組識別碼。

```
UINT32 m_nGroupID;
```

## <a name="canimationbaseobjectm_nobjectid"></a><a name="m_nobjectid"></a>動畫基礎物件::m_nObjectID

指定動畫物件的物件識別碼。

```
UINT32 m_nObjectID;
```

## <a name="canimationbaseobjectm_pparentcontroller"></a><a name="m_pparentcontroller"></a>動畫基礎物件::m_pParentController

指向父動畫控制器的指標。

```
CAnimationController* m_pParentController;
```

## <a name="canimationbaseobjectsetautodestroytransitions"></a><a name="setautodestroytransitions"></a>動畫基礎物件::設定自動銷毀轉換

設置標誌以自動銷毀過渡。

```cpp
void SetAutodestroyTransitions(BOOL bValue);
```

### <a name="parameters"></a>參數

*bValue*<br/>
指定自動銷毀標誌。

### <a name="remarks"></a>備註

僅當使用運算符 new 分配過渡物件時,才設置此標誌。 如果由於某種原因在堆疊上分配過渡物件,則自動銷毀標誌應為 FALSE。 預設情況下,此標誌為 TRUE。

## <a name="canimationbaseobjectsetid"></a><a name="setid"></a>動畫基礎物件::SetID

設置新指示。

```cpp
void SetID(
    UINT32 nObjectID,
    UINT32 nGroupID = 0);
```

### <a name="parameters"></a>參數

*nObjectID*<br/>
指定新的物件識別碼。

*n集團ID*<br/>
指定新的組 ID。

### <a name="remarks"></a>備註

允許您更改物件 ID 和組 ID。 如果新的組 ID 與當前 ID 不同,則動畫物件將移動到另一個組(如有必要,將創建新組)。

## <a name="canimationbaseobjectsetparentanimationobjects"></a><a name="setparentanimationobjects"></a>動畫基礎物件::設定父動畫物件

建立動畫物件中包含的動畫變數與其容器之間的關係。

```
virtual void SetParentAnimationObjects();
```

### <a name="remarks"></a>備註

此幫助程式可用於在動畫物件中包含的動畫變數與其容器之間建立關係。 它迴圈在動畫變數上,並將指向父動畫物件的回指標設置到每個動畫變數。 在當前實現中,實際關係在 CAnimationBaseObject::apply 轉換中建立,因此在調用 CAnimateGroup::Animate 之前不會設置回指標。 當您處理事件並且需要從 CAnimationVariable 獲取父動畫物件時,了解關係可能會有所説明。 使用「動畫變數:「獲取父動畫物件。

## <a name="canimationbaseobjectsetuserdata"></a><a name="setuserdata"></a>動畫基礎物件::設定使用者資料

設置使用者定義的數據。

```cpp
void SetUserData (DWORD dwUserData);
```

### <a name="parameters"></a>參數

*dwUserData*<br/>
指定自定義數據。

### <a name="remarks"></a>備註

使用此方法將自定義數據與動畫對象相關聯。 GetUserData可在稍後運行時檢索此數據。

## <a name="see-also"></a>另請參閱

[類別](../../mfc/reference/mfc-classes.md)
