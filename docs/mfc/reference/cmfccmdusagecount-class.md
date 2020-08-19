---
title: CMFCCmdUsageCount 類別
ms.date: 11/04/2016
f1_keywords:
- CMFCCmdUsageCount
- AFXCMDUSAGECOUNT/CMFCCmdUsageCount
- AFXCMDUSAGECOUNT/CMFCCmdUsageCount::AddCmd
- AFXCMDUSAGECOUNT/CMFCCmdUsageCount::GetCount
- AFXCMDUSAGECOUNT/CMFCCmdUsageCount::HasEnoughInformation
- AFXCMDUSAGECOUNT/CMFCCmdUsageCount::IsFreqeuntlyUsedCmd
- AFXCMDUSAGECOUNT/CMFCCmdUsageCount::Reset
- AFXCMDUSAGECOUNT/CMFCCmdUsageCount::Serialize
- AFXCMDUSAGECOUNT/CMFCCmdUsageCount::SetOptions
helpviewer_keywords:
- CMFCCmdUsageCount [MFC], AddCmd
- CMFCCmdUsageCount [MFC], GetCount
- CMFCCmdUsageCount [MFC], HasEnoughInformation
- CMFCCmdUsageCount [MFC], IsFreqeuntlyUsedCmd
- CMFCCmdUsageCount [MFC], Reset
- CMFCCmdUsageCount [MFC], Serialize
- CMFCCmdUsageCount [MFC], SetOptions
ms.assetid: 9c33b783-37c0-43ea-9f31-3c75e246c841
ms.openlocfilehash: 15026746f2af55b9cc153cce19cf00475e5c5d77
ms.sourcegitcommit: 1839405b97036891b6e4d37c99def044d6f37eff
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/18/2020
ms.locfileid: "88561098"
---
# <a name="cmfccmdusagecount-class"></a>CMFCCmdUsageCount 類別

追蹤 Windows 訊息的使用計數，例如當使用者從功能表中選取專案時。

## <a name="syntax"></a>語法

```
class CMFCCmdUsageCount : public CObject
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|||
|-|-|
|名稱|描述|
|`CMFCCmdUsageCount::CMFCCmdUsageCount`|預設建構函式。|
|`CMFCCmdUsageCount::~CMFCCmdUsageCount`|解構函式。|

### <a name="public-methods"></a>公用方法

|||
|-|-|
|名稱|描述|
|[CMFCCmdUsageCount：： AddCmd](#addcmd)|遞增與指定命令相關聯的計數器。|
|[CMFCCmdUsageCount：： GetCount](#getcount)|抓取與指定的命令識別碼相關聯的使用計數。|
|[CMFCCmdUsageCount：： HasEnoughInformation](#hasenoughinformation)|判斷此物件是否已收集最少量的追蹤資料。|
|[CMFCCmdUsageCount：： IsFreqeuntlyUsedCmd](#isfreqeuntlyusedcmd)|判斷指定的命令是否經常使用。|
|[CMFCCmdUsageCount：： Reset](#reset)|清除所有命令的使用計數。|
|[CMFCCmdUsageCount：：序列化](#serialize)|從封存讀取此物件，或將它寫入封存。 (覆寫 [CObject::Serialize](../../mfc/reference/cobject-class.md#serialize)。)|
|[CMFCCmdUsageCount：： >setoptions](#setoptions)|設定共用 `CMFCCmdUsageCount` 類別資料成員的值。|

### <a name="data-members"></a>資料成員

|||
|-|-|
|名稱|描述|
|`m_CmdUsage`|將 `CMap` 命令對應至其使用計數的物件。|
|`m_nMinUsagePercentage`|經常使用之命令的最小使用量百分比。|
|`m_nStartCount`|啟動計數器，用來判斷此物件是否已收集最少的追蹤資料量。|
|`m_nTotalUsage`|所有追蹤命令的計數。|

### <a name="remarks"></a>備註

類別會將 `CMFCCmdUsageCount` 每個數值 Windows 訊息識別碼對應至32位不帶正負號的整數計數器。 `CMFCToolBar` 使用這個類別來顯示經常使用的工具列專案。 如需的詳細資訊 `CMFCToolBar` ，請參閱 [CMFCToolBar 類別](../../mfc/reference/cmfctoolbar-class.md)。

您可以在 `CMFCCmdUsageCount` 程式執行之間保存類別資料。 您可以使用 [CMFCCmdUsageCount：：序列化](#serialize) 方法來序列化類別成員資料，並使用 [CMFCCmdUsageCount：： >setoptions](#setoptions) 方法來設定共用成員資料。

## <a name="inheritance-hierarchy"></a>繼承階層架構

[CObject](../../mfc/reference/cobject-class.md)

[CMFCCmdUsageCount](../../mfc/reference/cmfccmdusagecount-class.md)

## <a name="requirements"></a>規格需求

**標頭：** afxcmdusagecount。h

## <a name="cmfccmdusagecountaddcmd"></a><a name="addcmd"></a> CMFCCmdUsageCount：： AddCmd

遞增與指定命令相關聯的計數器。

```cpp
void AddCmd(UINT uiCmd);
```

### <a name="parameters"></a>參數

*uiCmd*\
在指定要遞增的命令計數器。

### <a name="remarks"></a>備註

如果專案不存在，這個方法會將新專案加入至命令計數的對應結構 `m_CmdUsage` 。

在下列情況下，此方法不會執行任何動作：

- Toolbar framework 在自訂模式中 ([CMFCToolBar：： IsCustomizeMode](../../mfc/reference/cmfctoolbar-class.md#iscustomizemode) 方法會傳回非零值) 。

- 此命令會參考子功能表或功能表分隔符號 ( *uiCmd* 等於0或-1) 。

- *uiCmd* 是指標准命令 (全域函式會傳回 `IsStandardCommand` 非零值) 。

## <a name="cmfccmdusagecountgetcount"></a><a name="getcount"></a> CMFCCmdUsageCount：： GetCount

抓取與指定的命令識別碼相關聯的使用計數。

```
UINT GetCount(UINT uiCmd) const;
```

### <a name="parameters"></a>參數

*uiCmd*\
在要取出之命令計數器的識別碼。

### <a name="return-value"></a>傳回值

與指定的命令識別碼相關聯的使用計數。

## <a name="cmfccmdusagecounthasenoughinformation"></a><a name="hasenoughinformation"></a> CMFCCmdUsageCount：： HasEnoughInformation

判斷此物件是否已收到最少的追蹤資料量。

```
BOOL HasEnoughInformation() const;
```

### <a name="return-value"></a>傳回值

如果這個物件已收到最少量的追蹤資料，則為非零。否則為0。

### <a name="remarks"></a>備註

如果 `m_nTotalUsage` 所有追蹤命令的總計數等於或大於初始計數，則這個方法會傳回非零值 `m_nStartCount` 。 根據預設，架構會設定初始計數0。 您可以使用 [CMFCCmdUsageCount：： >setoptions](#setoptions) 方法來覆寫此值。

[CMFCMenuBar：： IsShowAllCommands](../../mfc/reference/cmfcmenubar-class.md#isshowallcommands)會使用這個方法來判斷是否要顯示所有可用的功能表命令。

## <a name="cmfccmdusagecountisfreqeuntlyusedcmd"></a><a name="isfreqeuntlyusedcmd"></a> CMFCCmdUsageCount：： IsFreqeuntlyUsedCmd

判斷指定的命令是否經常使用。

```
BOOL IsFreqeuntlyUsedCmd(UINT uiCmd) const;
```

### <a name="parameters"></a>參數

*uiCmd*\
在指定要檢查的命令。

### <a name="return-value"></a>傳回值

如果經常使用命令，則為非零;否則為0。

### <a name="remarks"></a>備註

如果命令使用總計為0，則這個方法 `m_nTotalUsage` 會傳回0。 否則，如果所指定命令的使用百分比大於最小百分比，則這個方法會傳回非零值 `m_nMinUsagePercentage` 。 根據預設，架構會將最小百分比設定為5。 您可以使用 [CMFCCmdUsageCount：： >setoptions](#setoptions) 方法來覆寫此值。 如果最小百分比為0，則如果指定的命令計數大於0，則這個方法會傳回非零值。

[CMFCToolBar：： IsCommandRarelyUsed](../../mfc/reference/cmfctoolbar-class.md#iscommandrarelyused) 會使用這個方法來判斷是否很少使用命令。

## <a name="cmfccmdusagecountreset"></a><a name="reset"></a> CMFCCmdUsageCount：： Reset

清除所有命令的使用計數。

```cpp
void Reset();
```

### <a name="remarks"></a>備註

呼叫這個方法可清除命令計數、和之對應結構中的所有專案， `m_CmdUsage` 以及重設總命令使用方式、 `m_nTotalUsage` 、計數器至0。

## <a name="cmfccmdusagecountserialize"></a><a name="serialize"></a> CMFCCmdUsageCount：：序列化

從封存讀取此物件，或將它寫入封存。

```
virtual void Serialize(CArchive& ar);
```

### <a name="parameters"></a>參數

*Ar*\
在 `CArchive` 要從或序列化為的物件。

### <a name="remarks"></a>備註

這個方法會將命令計數的對應結構、 `m_CmdUsage` 和命令的總使用方式、 `m_nTotalUsage` 計數器從或寫入至指定的封存。

如需序列化範例，請參閱 [序列化：序列化物件](../../mfc/serialization-serializing-an-object.md)。

## <a name="cmfccmdusagecountsetoptions"></a><a name="setoptions"></a> CMFCCmdUsageCount：： >setoptions

設定共用 `CMFCCmdUsageCount` 類別資料成員的值。

```
static BOOL __stdcall SetOptions(
    UINT nStartCount,
    UINT nMinUsagePercentage);
```

### <a name="parameters"></a>參數

*nStartCount*\
在所有追蹤命令的新初始計數。

*nMinUsagePercentage*\
在新的最小使用量百分比。

### <a name="return-value"></a>傳回值

如果方法成功，則為 TRUE，如果 *nMinUsagePercentage* 參數大於或等於100，則為 FALSE。

### <a name="remarks"></a>備註

這個方法會將共用的 `CMFCCmdUsageCount` 類別資料成員 `m_nStartCount` 和分別設定 `m_nMinUsagePercentage` 為 *nStartCount* 和 *nMinUsagePercentage*。 `m_nStartCount`[CMFCCmdUsageCount：： HasEnoughInformation](#hasenoughinformation)方法用來判斷此物件是否已收集最少量的追蹤資料。 `m_nMinUsagePercentage`[CMFCCmdUsageCount：： IsFreqeuntlyUsedCmd](#isfreqeuntlyusedcmd)方法會使用，以判斷是否經常使用指定的命令。

在 Debug 組建中，如果 *nMinUsagePercentage* 參數大於或等於100，這個方法會產生判斷提示失敗。

## <a name="see-also"></a>另請參閱

[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[類別](../../mfc/reference/mfc-classes.md)<br/>
[CMFCToolBar 類別](../../mfc/reference/cmfctoolbar-class.md)
