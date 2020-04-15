---
title: CMenuTearoff 經理類
ms.date: 10/18/2018
f1_keywords:
- CMenuTearOffManager
- AFXMENUTEAROFFMANAGER/CMenuTearOffManager
- AFXMENUTEAROFFMANAGER/CMenuTearOffManager::CMenuTearOffManager
- AFXMENUTEAROFFMANAGER/CMenuTearOffManager::Build
- AFXMENUTEAROFFMANAGER/CMenuTearOffManager::GetRegPath
- AFXMENUTEAROFFMANAGER/CMenuTearOffManager::Initialize
- AFXMENUTEAROFFMANAGER/CMenuTearOffManager::IsDynamicID
- AFXMENUTEAROFFMANAGER/CMenuTearOffManager::Parse
- AFXMENUTEAROFFMANAGER/CMenuTearOffManager::Reset
- AFXMENUTEAROFFMANAGER/CMenuTearOffManager::SetInUse
- AFXMENUTEAROFFMANAGER/CMenuTearOffManager::SetupTearOffMenus
helpviewer_keywords:
- CMenuTearOffManager [MFC], CMenuTearOffManager
- CMenuTearOffManager [MFC], Build
- CMenuTearOffManager [MFC], GetRegPath
- CMenuTearOffManager [MFC], Initialize
- CMenuTearOffManager [MFC], IsDynamicID
- CMenuTearOffManager [MFC], Parse
- CMenuTearOffManager [MFC], Reset
- CMenuTearOffManager [MFC], SetInUse
- CMenuTearOffManager [MFC], SetupTearOffMenus
ms.assetid: ab7ca272-ce42-4678-95f7-6ad75038f5a0
ms.openlocfilehash: f41937179dc055213f3af093e107bcb08c8a8fcc
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81369967"
---
# <a name="cmenutearoffmanager-class"></a>CMenuTearoff 經理類

管理 Tear-Off 功能表。 Tear-Off 功能表是在功能表列上的功能表。 使用者可以取下功能表列中的 Tear-Off 功能表，讓 Tear-Off 功能表浮動。

   有關詳細資訊,請參閱位於 Visual Studio 安裝的**VC\\\\\\atlmfc src mfc**資料夾中的原始程式碼。

## <a name="syntax"></a>語法

```
class CMenuTearOffManager : public CObject
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[CMenuTearoff 管理員::CMenutearoff 管理員](#cmenutearoffmanager)|建構 `CMenuTearOffManager` 物件。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CMenuTearoff 管理員::產生](#build)||
|[CMenuTearoff 經理:取得 RegPath](#getregpath)||
|[CMenuTearoff 管理員:初始化](#initialize)|初始化 `CMenuTearOffManager` 物件。|
|[CMenutearoff 管理員::動態 ID](#isdynamicid)||
|[CMenuTearoff 經理::P](#parse)||
|[CMenuTearoff 管理員:重置](#reset)||
|[CMenutearoff 管理員::Setinuse](#setinuse)||
|[CMenuTearoff 管理器::設置"關閉功能表"](#setuptearoffmenus)||

## <a name="remarks"></a>備註

為了在應用程式中使用分淚功能表,您必須有一個`CMenuTearOffManager`物件。 在大多數情況下,不會直接創建或初始化`CMenuTearOffManager`物件。 當您調用[CWinAppEx::啟用TearOffMenus](../../mfc/reference/cwinappex-class.md#enabletearoffmenus)函數時,將為您處理此操作。

## <a name="example"></a>範例

下面的範例展示如何透過調用`CMenuTearOffManager``CWinAppEX::EnableTearOffMenus`方法建構和初始化物件。 此程式碼片段是 [WordPad 範例](../../overview/visual-cpp-samples.md)的一部分。

[!code-cpp[NVC_MFC_WordPad#12](../../mfc/reference/codesnippet/cpp/cmenutearoffmanager-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>繼承階層架構

[CObject](../../mfc/reference/cobject-class.md)

`CMenuTearOffManager`

## <a name="requirements"></a>需求

**標題:** afxmenutearoff 管理員.h

## <a name="cmenutearoffmanagerbuild"></a><a name="build"></a>CMenuTearoff 管理員::產生

```
void Build(
    UINT uiTearOffBarID,
    CString& strText);
```

### <a name="parameters"></a>參數

[在]*烏伊蒂爾·烏夫巴里德*<br/>

[在]*斯特文字*<br/>

### <a name="remarks"></a>備註

## <a name="cmenutearoffmanagercmenutearoffmanager"></a><a name="cmenutearoffmanager"></a>CMenuTearoff 管理員::CMenutearoff 管理員

構造[CMenuTearOffManager](../../mfc/reference/cmenutearoffmanager-class.md)物件。

```
CMenuTearOffManager();
```

### <a name="remarks"></a>備註

在大多數情況下,不應手動創建。 `CMenuTearOffManager` 當您呼叫 CWinAppEx`CMenuTearOffManager`時,應用程式的框架將建立物件[::啟用TearOffMenus](../../mfc/reference/cwinappex-class.md#enabletearoffmenus)。

## <a name="cmenutearoffmanagergetregpath"></a><a name="getregpath"></a>CMenuTearoff 經理:取得 RegPath

```
LPCTSTR GetRegPath() const;
```

### <a name="return-value"></a>傳回值

### <a name="remarks"></a>備註

## <a name="cmenutearoffmanagerinitialize"></a><a name="initialize"></a>CMenuTearoff 管理員:初始化

初始化[CMenuTearOff 管理員](../../mfc/reference/cmenutearoffmanager-class.md)物件。

```
BOOL Initialize(
    LPCTSTR lpszRegEntry,
    UINT uiTearOffMenuFirst,
    UINT uiTearOffMenuLast);
```

### <a name="parameters"></a>參數

*lpszRegEntry*<br/>
[在]包含註冊表項路徑的字串。 應用程式在此註冊表條目中存儲撕下條的設置。

*烏伊蒂爾·烏梅首先*<br/>
[在]撕掉功能表的第一個功能表 ID。

*uiTearOffMenu 最後*<br/>
[在]撕掉功能表的最後一個功能表 ID。

### <a name="return-value"></a>傳回值

如果成功則為非零；否則為 0。

### <a name="remarks"></a>備註

功能表代碼的範圍從*uiTearOffMenuFirst*到*uiTear OffMenuLast,* 必須是連續間隔。 該間隔定義可在應用程式中同時顯示的撕扯功能表數。

## <a name="cmenutearoffmanagerisdynamicid"></a><a name="isdynamicid"></a>CMenutearoff 管理員::動態 ID

```
BOOL IsDynamicID(UINT uiID) const;
```

### <a name="parameters"></a>參數

[在]*uiID*<br/>

### <a name="return-value"></a>傳回值

### <a name="remarks"></a>備註

## <a name="cmenutearoffmanagerparse"></a><a name="parse"></a>CMenuTearoff 經理::P

```
UINT Parse(CString& str);
```

### <a name="parameters"></a>參數

[在]*斯特*<br/>

### <a name="return-value"></a>傳回值

### <a name="remarks"></a>備註

## <a name="cmenutearoffmanagerreset"></a><a name="reset"></a>CMenuTearoff 管理員:重置

```
void Reset(HMENU hmenu);
```

### <a name="parameters"></a>參數

[在]*赫梅努*<br/>

### <a name="remarks"></a>備註

## <a name="cmenutearoffmanagersetinuse"></a><a name="setinuse"></a>CMenutearoff 管理員::Setinuse

```
void SetInUse(
    UINT uiCmdId,
    BOOL bUse = TRUE);
```

### <a name="parameters"></a>參數

[在]*烏伊CmDId*<br/>

[在]*bUse*<br/>

### <a name="remarks"></a>備註

## <a name="cmenutearoffmanagersetuptearoffmenus"></a><a name="setuptearoffmenus"></a>CMenuTearoff 管理器::設置"關閉功能表"

```
void SetupTearOffMenus(HMENU hMenu);
```

### <a name="parameters"></a>參數

[在]*hMenu*<br/>

### <a name="remarks"></a>備註

## <a name="see-also"></a>另請參閱

[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[類別](../../mfc/reference/mfc-classes.md)<br/>
[CWinAppEx 類別](../../mfc/reference/cwinappex-class.md)
