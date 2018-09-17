---
title: CMFCCmdUsageCount 類別 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
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
dev_langs:
- C++
helpviewer_keywords:
- CMFCCmdUsageCount [MFC], AddCmd
- CMFCCmdUsageCount [MFC], GetCount
- CMFCCmdUsageCount [MFC], HasEnoughInformation
- CMFCCmdUsageCount [MFC], IsFreqeuntlyUsedCmd
- CMFCCmdUsageCount [MFC], Reset
- CMFCCmdUsageCount [MFC], Serialize
- CMFCCmdUsageCount [MFC], SetOptions
ms.assetid: 9c33b783-37c0-43ea-9f31-3c75e246c841
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: a1e28b9c28823e77244bc6e686db163e5110a8fa
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/17/2018
ms.locfileid: "45719962"
---
# <a name="cmfccmdusagecount-class"></a>CMFCCmdUsageCount 類別
追蹤 Windows 訊息，例如當使用者從功能表選取項目時的使用的計數。  
  
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
|[CMFCCmdUsageCount::AddCmd](#addcmd)|一個指定的命令相關聯的計數器遞增。|  
|[CMFCCmdUsageCount::GetCount](#getcount)|擷取與指定的命令識別碼相關聯的使用計數|  
|[CMFCCmdUsageCount::HasEnoughInformation](#hasenoughinformation)|判斷這個物件是否已收集追蹤資料的最小數量。|  
|[Isfreqeuntlyusedcmd](#isfreqeuntlyusedcmd)|判斷是否經常使用指定的命令。|  
|[CMFCCmdUsageCount::Reset](#reset)|清除所有命令的使用計數。|  
|[CMFCCmdUsageCount::Serialize](#serialize)|從封存讀取這個物件，或將其寫入至封存。 (覆寫 [CObject::Serialize](../../mfc/reference/cobject-class.md#serialize)。)|  
|[CMFCCmdUsageCount::SetOptions](#setoptions)|設定的值共用`CMFCCmdUsageCount`類別資料成員。|  
  
### <a name="data-members"></a>資料成員  
  
|||  
|-|-|  
|名稱|描述|  
|`m_CmdUsage`|A`CMap`將命令對應至其使用方式計數的物件。|  
|`m_nMinUsagePercentage`|命令常用的最小使用量百分比。|  
|`m_nStartCount`|用來判斷這個物件是否已收集追蹤資料的最小數量開始計數器。|  
|`m_nTotalUsage`|所有追蹤的命令數目。|  
  
### <a name="remarks"></a>備註  
 `CMFCCmdUsageCount`類別會將每個數值的 Windows 訊息識別項對應至 32 位元不帶正負號的整數的計數器。 `CMFCToolBar` 您可以使用這個類別來顯示常用的工具列項目。 如需詳細資訊`CMFCToolBar`，請參閱 < [CMFCToolBar 類別](../../mfc/reference/cmfctoolbar-class.md)。  
  
 您可以保存`CMFCCmdUsageCount`類別執行您的程式之間的資料。 使用[CMFCCmdUsageCount::Serialize](#serialize)方法，將類別成員資料的序列化並[CMFCCmdUsageCount::SetOptions](#setoptions)方法來設定共用的成員資料。  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CMFCCmdUsageCount](../../mfc/reference/cmfccmdusagecount-class.md)  
  
## <a name="requirements"></a>需求  
 **標頭：** afxcmdusagecount.h  
  
##  <a name="addcmd"></a>  CMFCCmdUsageCount::AddCmd  
 一個指定的命令相關聯的計數器遞增。  
  
```  
void AddCmd(UINT uiCmd);
```  
  
### <a name="parameters"></a>參數  
  
|||  
|-|-|  
|參數|描述|  
|*uiCmd*|[in]指定命令要計數器遞增。|  
  
### <a name="remarks"></a>備註  
 這個方法會加入新項目指令計數的對應結構`m_CmdUsage`，如果項目不存在。  
  
 這個方法會在下列案例中為 nothing:  
  
-   工具列架構已自訂模式 ( [CMFCToolBar::IsCustomizeMode](../../mfc/reference/cmfctoolbar-class.md#iscustomizemode)方法會傳回非零值)。  
  
-   此命令是指子功能表或功能表分隔符號 ( *uiCmd*等於 0，則為-1)。  
  
- *uiCmd*指的是標準的命令 (全域`IsStandardCommand`函式會傳回非零值)。  
  
##  <a name="getcount"></a>  CMFCCmdUsageCount::GetCount  
 擷取與指定的命令識別碼相關聯的使用計數  
  
```  
UINT GetCount(UINT uiCmd) const;  
```  
  
### <a name="parameters"></a>參數  
  
|||  
|-|-|  
|參數|描述|  
|*uiCmd*|[in]要擷取 [命令] 計數器的識別碼。|  
  
### <a name="return-value"></a>傳回值  
 與指定的命令識別碼相關聯的使用計數  
  
##  <a name="hasenoughinformation"></a>  CMFCCmdUsageCount::HasEnoughInformation  
 決定是否此物件已接收追蹤資料的最小數量。  
  
```  
BOOL HasEnoughInformation() const;  
```  
  
### <a name="return-value"></a>傳回值  
 如果此物件已接收追蹤資料的最小數量，非零值。否則為 0。  
  
### <a name="remarks"></a>備註  
 如果此方法會傳回非零值的總計數， `m_nTotalUsage`，所有追蹤的命令是等於或大於初始的計數， `m_nStartCount`。 根據預設，架構會將初始計數 0。 您可以使用覆寫此值[CMFCCmdUsageCount::SetOptions](#setoptions)方法。  
  
 這個方法由[CMFCMenuBar::IsShowAllCommands](../../mfc/reference/cmfcmenubar-class.md#isshowallcommands)來判斷是否要顯示所有可用的功能表命令。  
  
##  <a name="isfreqeuntlyusedcmd"></a>  Isfreqeuntlyusedcmd  
 判斷是否經常使用指定的命令。  
  
```  
BOOL IsFreqeuntlyUsedCmd(UINT uiCmd) const;  
```  
  
### <a name="parameters"></a>參數  
  
|||  
|-|-|  
|參數|描述|  
|*uiCmd*|[in]指定要檢查的命令。|  
  
### <a name="return-value"></a>傳回值  
 非零值，如果經常使用的命令;否則為 0。  
  
### <a name="remarks"></a>備註  
 這個方法會傳回 0，如果總命令的用法， `m_nTotalUsage`，為 0。 否則，這個方法會傳回非零值，如果指定的命令使用其中的百分比大於最小的百分比， `m_nMinUsagePercentage`。 根據預設，架構會設定為 5 的最小百分比。 您可以使用覆寫此值[CMFCCmdUsageCount::SetOptions](#setoptions)方法。 如果百分比下限為 0，則這個方法會傳回非零值，如果指定的命令計數大於 0。  
  
 [CMFCToolBar::IsCommandRarelyUsed](../../mfc/reference/cmfctoolbar-class.md#iscommandrarelyused)使用這個方法來判斷是否有很少使用的命令。  
  
##  <a name="reset"></a>  CMFCCmdUsageCount::Reset  
 清除所有命令的使用計數。  
  
```  
void Reset();
```  
  
### <a name="remarks"></a>備註  
 呼叫這個方法來清除所有的項目，從對應結構的指令計數`m_CmdUsage`，以及重設總計命令的用法， `m_nTotalUsage`、 計數器為 0。  
  
##  <a name="serialize"></a>  CMFCCmdUsageCount::Serialize  
 讀取此物件從封存，或將它寫入封存。  
  
```  
virtual void Serialize(CArchive& ar);
```  
  
### <a name="parameters"></a>參數  
  
|||  
|-|-|  
|參數|描述|  
|*ar*|[in]A`CArchive`来序列化或物件。|  
  
### <a name="remarks"></a>備註  
 這個方法會序列化的指令計數的對應結構`m_CmdUsage`，和 總命令的用法， `m_nTotalUsage`、 計數器或指定的封存。  
  
 如需序列化的範例，請參閱[序列化： 序列化物件](../../mfc/serialization-serializing-an-object.md)。  
  
##  <a name="setoptions"></a>  CMFCCmdUsageCount::SetOptions  
 設定的值共用`CMFCCmdUsageCount`類別資料成員。  
  
```  
static BOOL __stdcall SetOptions(
    UINT nStartCount,  
    UINT nMinUsagePercentage);
```  
  
### <a name="parameters"></a>參數  
  
|||  
|-|-|  
|參數|描述|  
|*nStartCount*|[in]所有追蹤的命令新增初始的計數。|  
|*nMinUsagePercentage*|[in]新的最小的使用量百分比。|  
  
### <a name="return-value"></a>傳回值  
 如果方法成功，FALSE 則為 TRUE *nMinUsagePercentage*參數是大於或等於 100。  
  
### <a name="remarks"></a>備註  
 這個方法會設定共用`CMFCCmdUsageCount`類別資料成員`m_nStartCount`並`m_nMinUsagePercentage`來*nStartCount*並*nMinUsagePercentage*分別。 `m_nStartCount` 由[CMFCCmdUsageCount::HasEnoughInformation](#hasenoughinformation)方法，以判斷這個物件是否已收集追蹤資料的最小數量。 `m_nMinUsagePercentage` 由[Isfreqeuntlyusedcmd](#isfreqeuntlyusedcmd)方法，以判斷是否經常使用指定的命令。  
  
 在 偵錯組建中這個方法如果會產生判斷提示失敗*nMinUsagePercentage*參數是大於或等於 100。  
  
## <a name="see-also"></a>另請參閱  
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [類別](../../mfc/reference/mfc-classes.md)   
 [CMFCToolBar 類別](../../mfc/reference/cmfctoolbar-class.md)
