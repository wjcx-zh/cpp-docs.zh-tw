---
title: CMenuTearOffManager 類別
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
ms.openlocfilehash: 8b92ddad9d3a6de41cf6914dee268f6e54b5d420
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62163704"
---
# <a name="cmenutearoffmanager-class"></a>CMenuTearOffManager 類別

管理 Tear-Off 功能表。 Tear-Off 功能表是在功能表列上的功能表。 使用者可以取下功能表列中的 Tear-Off 功能表，讓 Tear-Off 功能表浮動。

   如需詳細資訊，請參閱中的原始程式碼**VC\\atlmfc\\src\\mfc** Visual Studio 安裝資料夾。

## <a name="syntax"></a>語法

```
class CMenuTearOffManager : public CObject
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[CMenuTearOffManager::CMenuTearOffManager](#cmenutearoffmanager)|建構 `CMenuTearOffManager` 物件。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CMenuTearOffManager::Build](#build)||
|[CMenuTearOffManager::GetRegPath](#getregpath)||
|[CMenuTearOffManager::Initialize](#initialize)|初始化`CMenuTearOffManager`物件。|
|[CMenuTearOffManager::IsDynamicID](#isdynamicid)||
|[CMenuTearOffManager::Parse](#parse)||
|[CMenuTearOffManager::Reset](#reset)||
|[CMenuTearOffManager::SetInUse](#setinuse)||
|[CMenuTearOffManager::SetupTearOffMenus](#setuptearoffmenus)||

## <a name="remarks"></a>備註

若要使用您的應用程式中的 tear-off 功能表，您必須擁有`CMenuTearOffManager`物件。 在大部分情況下，您將不會建立或初始化`CMenuTearOffManager`直接物件。 這會為您處理當您呼叫[CWinAppEx::EnableTearOffMenus](../../mfc/reference/cwinappex-class.md#enabletearoffmenus)函式。

## <a name="example"></a>範例

下列範例示範如何建構和初始化`CMenuTearOffManager`藉由呼叫物件`CWinAppEX::EnableTearOffMenus`方法。 此程式碼片段是 [WordPad 範例](../../overview/visual-cpp-samples.md)的一部分。

[!code-cpp[NVC_MFC_WordPad#12](../../mfc/reference/codesnippet/cpp/cmenutearoffmanager-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>繼承階層

[CObject](../../mfc/reference/cobject-class.md)

`CMenuTearOffManager`

## <a name="requirements"></a>需求

**標頭：** afxmenutearoffmanager.h

##  <a name="build"></a>  CMenuTearOffManager::Build

```
void Build(
    UINT uiTearOffBarID,
    CString& strText);
```

### <a name="parameters"></a>參數

[in] *uiTearOffBarID*<br/>

[in] *strText*<br/>

### <a name="remarks"></a>備註

##  <a name="cmenutearoffmanager"></a>  CMenuTearOffManager::CMenuTearOffManager

建構[CMenuTearOffManager](../../mfc/reference/cmenutearoffmanager-class.md)物件。

```
CMenuTearOffManager();
```

### <a name="remarks"></a>備註

在大部分情況下，您不應建立`CMenuTearOffManager`以手動方式。 您的應用程式的架構會建立`CMenuTearOffManager`當您呼叫物件[CWinAppEx::EnableTearOffMenus](../../mfc/reference/cwinappex-class.md#enabletearoffmenus)。

##  <a name="getregpath"></a>  CMenuTearOffManager::GetRegPath

```
LPCTSTR GetRegPath() const;
```

### <a name="return-value"></a>傳回值

### <a name="remarks"></a>備註

##  <a name="initialize"></a>  CMenuTearOffManager::Initialize

初始化[CMenuTearOffManager](../../mfc/reference/cmenutearoffmanager-class.md)物件。

```
BOOL Initialize(
    LPCTSTR lpszRegEntry,
    UINT uiTearOffMenuFirst,
    UINT uiTearOffMenuLast);
```

### <a name="parameters"></a>參數

*lpszRegEntry*<br/>
[in]字串，包含路徑的登錄項目。 您的應用程式會將分割列的設定儲存在此登錄項目。

*uiTearOffMenuFirst*<br/>
[in]Tear-off 功能表第一個功能表識別碼。

*uiTearOffMenuLast*<br/>
[in]Tear-off 功能表最後功能表識別碼。

### <a name="return-value"></a>傳回值

如果成功則為非零；否則為 0。

### <a name="remarks"></a>備註

從功能表識別碼的範圍*uiTearOffMenuFirst*要*uiTearOffMenuLast*必須是連續的時間間隔。 此間隔定義 tear-off 功能表可在應用程式中同時出現的數目。

##  <a name="isdynamicid"></a>  CMenuTearOffManager::IsDynamicID

```
BOOL IsDynamicID(UINT uiID) const;
```

### <a name="parameters"></a>參數

[in] *uiID*<br/>

### <a name="return-value"></a>傳回值

### <a name="remarks"></a>備註

##  <a name="parse"></a>  CMenuTearOffManager::Parse

```
UINT Parse(CString& str);
```

### <a name="parameters"></a>參數

[in] *str*<br/>

### <a name="return-value"></a>傳回值

### <a name="remarks"></a>備註

##  <a name="reset"></a>  CMenuTearOffManager::Reset

```
void Reset(HMENU hmenu);
```

### <a name="parameters"></a>參數

[in]*hmenu*<br/>

### <a name="remarks"></a>備註

##  <a name="setinuse"></a>  CMenuTearOffManager::SetInUse

```
void SetInUse(
    UINT uiCmdId,
    BOOL bUse = TRUE);
```

### <a name="parameters"></a>參數

[in] *uiCmdId*<br/>

[in] *bUse*<br/>

### <a name="remarks"></a>備註

##  <a name="setuptearoffmenus"></a>  CMenuTearOffManager::SetupTearOffMenus

```
void SetupTearOffMenus(HMENU hMenu);
```

### <a name="parameters"></a>參數

[in] *hMenu*<br/>

### <a name="remarks"></a>備註

## <a name="see-also"></a>另請參閱

[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[類別](../../mfc/reference/mfc-classes.md)<br/>
[CWinAppEx 類別](../../mfc/reference/cwinappex-class.md)
