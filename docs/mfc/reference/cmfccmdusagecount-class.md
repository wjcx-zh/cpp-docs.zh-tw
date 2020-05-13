---
title: CMFCCmd 使用計數類
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
ms.openlocfilehash: 02b302ec38922128190a6f20ce2f156b52383b55
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/22/2020
ms.locfileid: "81752588"
---
# <a name="cmfccmdusagecount-class"></a>CMFCCmd 使用計數類

跟蹤 Windows 消息的使用計數,例如當使用者從功能表中選擇專案時。

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
|[CMFCCmd 使用計數:添加Cmd](#addcmd)|增加與給定命令關聯的計數器的一個。|
|[CMFCCmd 使用計數:取得計數](#getcount)|檢索與給定命令 ID 關聯的使用計數。|
|[CMFCCmd 使用計數::有足夠資訊](#hasenoughinformation)|確定此物件是否已收集最小數量的跟蹤數據。|
|[CMFCCmd 使用計數: IsFreqeuntly使用Cmd](#isfreqeuntlyusedcmd)|確定是否經常使用給定命令。|
|[CMFCCmd 使用計數:重置](#reset)|清除所有命令的使用方式計數。|
|[CMFCCmd 使用計數:序列化](#serialize)|從存檔中讀取此物件或將其寫入存檔。 (覆寫 [CObject::Serialize](../../mfc/reference/cobject-class.md#serialize)。)|
|[CMFCCmd使用計數::設定選項](#setoptions)|設置共用`CMFCCmdUsageCount`類數據成員的值。|

### <a name="data-members"></a>資料成員

|||
|-|-|
|名稱|描述|
|`m_CmdUsage`|將`CMap`命令映射到其用法計數的物件。|
|`m_nMinUsagePercentage`|經常使用命令的最低使用百分比。|
|`m_nStartCount`|用於確定此物件是否已收集最小數量的跟蹤數據的起始計數器。|
|`m_nTotalUsage`|所有跟蹤命令的計數。|

### <a name="remarks"></a>備註

該`CMFCCmdUsageCount`類將每個數位 Windows 消息識別符映射到 32 位未簽名的整數計數器。 `CMFCToolBar`使用此類顯示常用工具列項。 有關 的詳細`CMFCToolBar`資訊 ,請參閱[CMFCToolBar 類別](../../mfc/reference/cmfctoolbar-class.md)。

您可以在程式執行`CMFCCmdUsageCount`之間保留類數據。 使用[CMFCCmdUseCount::序列化](#serialize)方法序列化類成員數據,使用[CMFCCmdUseCount::SetOptions](#setoptions)方法設置共享成員數據。

## <a name="inheritance-hierarchy"></a>繼承階層架構

[CObject](../../mfc/reference/cobject-class.md)

[CMFCCmd 使用計數](../../mfc/reference/cmfccmdusagecount-class.md)

## <a name="requirements"></a>需求

**標題:** afxcmd 用法計數.h

## <a name="cmfccmdusagecountaddcmd"></a><a name="addcmd"></a>CMFCCmd 使用計數:添加Cmd

增加與給定命令關聯的計數器的一個。

```cpp
void AddCmd(UINT uiCmd);
```

### <a name="parameters"></a>參數

|||
|-|-|
|參數|描述|
|*烏伊Cmd*|[在]指定命令計數器以遞增。|

### <a name="remarks"></a>備註

此方法向命令計數的地圖結構添加新條目,`m_CmdUsage`如果該條目不存在。

在以下情況下,此方法不執行任何操作:

- 工具列框架處於自定義模式[(CMFCToolBar:is自定義模式](../../mfc/reference/cmfctoolbar-class.md#iscustomizemode)方法返回非零值)。

- 該命令引用子功能表或功能表分隔符 *(uiCmd*等於 0 或 -1)。

- *uiCmd*引用標準命令(全域`IsStandardCommand`函數返回非零值)。

## <a name="cmfccmdusagecountgetcount"></a><a name="getcount"></a>CMFCCmd 使用計數:取得計數

檢索與給定命令 ID 關聯的使用計數。

```
UINT GetCount(UINT uiCmd) const;
```

### <a name="parameters"></a>參數

|||
|-|-|
|參數|描述|
|*烏伊Cmd*|[在]要檢索的命令計數器的 ID。|

### <a name="return-value"></a>傳回值

與給定命令 ID 關聯的用法計數。

## <a name="cmfccmdusagecounthasenoughinformation"></a><a name="hasenoughinformation"></a>CMFCCmd 使用計數::有足夠資訊

確定此物件是否已收到最小數量的跟蹤數據。

```
BOOL HasEnoughInformation() const;
```

### <a name="return-value"></a>傳回值

如果此物件已收到最小數量的跟蹤數據,則非零;否則 0。

### <a name="remarks"></a>備註

如果所有追蹤命令的總計計數`m_nTotalUsage`等於或大於初始計數`m_nStartCount`, 則此方法返回非零值。 默認情況下,框架設置初始計數 0。 您可以使用[CMFCCmd 使用計數::設定選項](#setoptions)方法覆蓋此值。

此方法由[CMFCMenuBar::IsShowAllCommands](../../mfc/reference/cmfcmenubar-class.md#isshowallcommands)用於確定是否顯示所有可用的功能表命令。

## <a name="cmfccmdusagecountisfreqeuntlyusedcmd"></a><a name="isfreqeuntlyusedcmd"></a>CMFCCmd 使用計數: IsFreqeuntly使用Cmd

確定是否經常使用給定命令。

```
BOOL IsFreqeuntlyUsedCmd(UINT uiCmd) const;
```

### <a name="parameters"></a>參數

|||
|-|-|
|參數|描述|
|*烏伊Cmd*|[在]指定要檢查的命令。|

### <a name="return-value"></a>傳回值

如果經常使用該命令,則非零;否則 0。

### <a name="remarks"></a>備註

如果總命令用法為 0,`m_nTotalUsage`則此方法返回 0。 否則,如果使用指定命令的百分比大於最小百分比,`m_nMinUsagePercentage`則此方法返回非零。 默認情況下,框架將最小百分比設置為 5。 您可以使用[CMFCCmd 使用計數::設定選項](#setoptions)方法覆蓋此值。 如果最小百分比為 0,則如果指定的命令計數大於 0,此方法將返回非零。

[CMFCToolBar:IsCommand很少使用](../../mfc/reference/cmfctoolbar-class.md#iscommandrarelyused)此方法來確定是否很少使用命令。

## <a name="cmfccmdusagecountreset"></a><a name="reset"></a>CMFCCmd 使用計數:重置

清除所有命令的使用方式計數。

```cpp
void Reset();
```

### <a name="remarks"></a>備註

呼叫此方法以清除命令計數的映射結構中的所有項目,`m_CmdUsage`並將總命令用法重置為`m_nTotalUsage`0。

## <a name="cmfccmdusagecountserialize"></a><a name="serialize"></a>CMFCCmd 使用計數:序列化

從存檔中讀取此物件,或將其寫入存檔。

```
virtual void Serialize(CArchive& ar);
```

### <a name="parameters"></a>參數

|||
|-|-|
|參數|描述|
|*ar*|[在]`CArchive`要序列化的物件。|

### <a name="remarks"></a>備註

此方法序列化指令計數的映射結構、`m_CmdUsage`和總命令用法`m_nTotalUsage`, 從指定存檔或到指定的存檔。

有關序列化範例,請參閱[序列化:序列化物件](../../mfc/serialization-serializing-an-object.md)。

## <a name="cmfccmdusagecountsetoptions"></a><a name="setoptions"></a>CMFCCmd使用計數::設定選項

設置共用`CMFCCmdUsageCount`類數據成員的值。

```
static BOOL __stdcall SetOptions(
    UINT nStartCount,
    UINT nMinUsagePercentage);
```

### <a name="parameters"></a>參數

|||
|-|-|
|參數|描述|
|*N 開始計數*|[在]所有跟蹤命令的新初始計數。|
|*nMinUsage百分比*|[在]新的最小使用百分比。|

### <a name="return-value"></a>傳回值

如果方法成功,則為 TRUE,如果*nMinUsage 百分比*參數大於或等於 100,則 FALSE。

### <a name="remarks"></a>備註

此方法分別設定`CMFCCmdUsageCount`共享類別資料`m_nStartCount`成員`m_nMinUsagePercentage`與*nStartCount*和*nMinUsage 百分比*。 `m_nStartCount`[由 CMFCCmdUsageCount::HasOfof 資訊](#hasenoughinformation)方法用於確定此物件是否已收集最小數量的跟蹤數據。 `m_nMinUsagePercentage`[由 CMFCCmdUsageCount 使用:IsFreqeuntly使用Cmd](#isfreqeuntlyusedcmd)方法來確定是否經常使用給定命令。

在除錯產生中,如果*nMinUsage 百分比*參數大於或等於 100,此方法將生成斷言失敗。

## <a name="see-also"></a>另請參閱

[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[類別](../../mfc/reference/mfc-classes.md)<br/>
[CMFCToolBar 類別](../../mfc/reference/cmfctoolbar-class.md)
