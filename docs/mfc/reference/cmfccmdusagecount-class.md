---
title: "CMFCCmdUsageCount 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
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
- CMFCCmdUsageCount class
ms.assetid: 9c33b783-37c0-43ea-9f31-3c75e246c841
caps.latest.revision: 20
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Machine Translation
ms.sourcegitcommit: 0e0c08ddc57d437c51872b5186ae3fc983bb0199
ms.openlocfilehash: b264448af4041139018b181e2255988555267b89
ms.contentlocale: zh-tw
ms.lasthandoff: 02/24/2017

---
# <a name="cmfccmdusagecount-class"></a>CMFCCmdUsageCount 類別
追蹤 Windows 訊息，例如當使用者從功能表選取項目時的使用的計數。  
  
## <a name="syntax"></a>語法  
  
```  
class CMFCCmdUsageCount : public CObject  
```  
  
## <a name="members"></a>Members  
  
### <a name="public-constructors"></a>公用建構函式  
  
|||  
|-|-|  
|名稱|描述|  
|`CMFCCmdUsageCount::CMFCCmdUsageCount`|預設建構函式。|  
|`CMFCCmdUsageCount::~CMFCCmdUsageCount`|解構函式。|  
  
### <a name="public-methods"></a>公用方法  
  
|||  
|-|-|  
|名稱|說明|  
|[CMFCCmdUsageCount::AddCmd](#addcmd)|一個指定的命令相關聯的計數器遞增。|  
|[CMFCCmdUsageCount::GetCount](#getcount)|擷取與指定的命令識別碼相關聯的使用計數|  
|[CMFCCmdUsageCount::HasEnoughInformation](#hasenoughinformation)|判斷此物件是否已收集追蹤資料的最小數量。|  
|[CMFCCmdUsageCount::IsFreqeuntlyUsedCmd](#isfreqeuntlyusedcmd)|決定是否經常使用指定的命令。|  
|[CMFCCmdUsageCount::Reset](#reset)|清除所有命令的使用量。|  
|[CMFCCmdUsageCount::Serialize](#serialize)|從封存讀取此物件，或將它寫入至封存檔。 (覆寫[CObject::Serialize](../../mfc/reference/cobject-class.md#serialize)。)|  
|[CMFCCmdUsageCount::SetOptions](#setoptions)|設定的值共用`CMFCCmdUsageCount`類別資料成員。|  
  
### <a name="data-members"></a>資料成員  
  
|||  
|-|-|  
|名稱|描述|  
|`m_CmdUsage`|A`CMap`將命令對應至其使用方式計數的物件。|  
|`m_nMinUsagePercentage`|最小的使用量百分比經常使用的命令。|  
|`m_nStartCount`|用來判斷此物件是否已收集追蹤資料的最小數量開始計數器。|  
|`m_nTotalUsage`|所有追蹤的命令數目。|  
  
### <a name="remarks"></a>備註  
 `CMFCCmdUsageCount`類別會將每個數值的 Windows 訊息識別項對應至 32 位元不帶正負號的整數的計數器。 `CMFCToolBar`您可以使用這個類別來顯示常用的工具列項目。 如需詳細資訊`CMFCToolBar`，請參閱[CMFCToolBar 類別](../../mfc/reference/cmfctoolbar-class.md)。  
  
 您可以保存`CMFCCmdUsageCount`類別執行的程式之間的資料。 使用[CMFCCmdUsageCount::Serialize](#serialize)方法，將類別成員資料的序列化和[CMFCCmdUsageCount::SetOptions](#setoptions)方法來設定共用的成員資料。  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CMFCCmdUsageCount](../../mfc/reference/cmfccmdusagecount-class.md)  
  
## <a name="requirements"></a>需求  
 **標頭︰** afxcmdusagecount.h  
  
##  <a name="addcmd"></a>CMFCCmdUsageCount::AddCmd  
 一個指定的命令相關聯的計數器遞增。  
  
```  
void AddCmd(UINT uiCmd);
```  
  
### <a name="parameters"></a>參數  
  
|||  
|-|-|  
|參數|描述|  
|[in] `uiCmd`|指定命令計數器遞增。|  
  
### <a name="remarks"></a>備註  
 這個方法會加入新項目對應結構的命令計數`m_CmdUsage`，如果已經不存在。  
  
 這個方法會在下列情況中為 nothing:  
  
-   工具列架構為自訂模式 ( [CMFCToolBar::IsCustomizeMode](../../mfc/reference/cmfctoolbar-class.md#iscustomizemode)方法會傳回非零值)。  
  
-   此命令是指子功能表或功能表分隔符號 (`uiCmd`等於 0，則為-1)。  
  
- `uiCmd`指的是標準的命令 (全域`IsStandardCommand`函式會傳回非零值)。  
  
##  <a name="getcount"></a>CMFCCmdUsageCount::GetCount  
 擷取與指定的命令識別碼相關聯的使用計數  
  
```  
UINT GetCount(UINT uiCmd) const;  
```  
  
### <a name="parameters"></a>參數  
  
|||  
|-|-|  
|參數|描述|  
|[in] `uiCmd`|要擷取命令計數器的識別碼。|  
  
### <a name="return-value"></a>傳回值  
 與指定的命令識別碼相關聯的使用量  
  
##  <a name="hasenoughinformation"></a>CMFCCmdUsageCount::HasEnoughInformation  
 判斷此物件是否已接收追蹤資料的最小數量。  
  
```  
BOOL HasEnoughInformation() const;  
```  
  
### <a name="return-value"></a>傳回值  
 非零，如果此物件已接收的最小數量追蹤資料。否則為 0。  
  
### <a name="remarks"></a>備註  
 如果此方法會傳回非零值的總計數， `m_nTotalUsage`，所有追蹤的命令是等於或大於初始計數`m_nStartCount`。 根據預設，架構會設定初始計數 0。 您可以使用覆寫此值[CMFCCmdUsageCount::SetOptions](#setoptions)方法。  
  
 這個方法由[CMFCMenuBar::IsShowAllCommands](../../mfc/reference/cmfcmenubar-class.md#isshowallcommands)來判斷是否要顯示所有可用的功能表命令。  
  
##  <a name="isfreqeuntlyusedcmd"></a>CMFCCmdUsageCount::IsFreqeuntlyUsedCmd  
 決定是否經常使用指定的命令。  
  
```  
BOOL IsFreqeuntlyUsedCmd(UINT uiCmd) const;  
```  
  
### <a name="parameters"></a>參數  
  
|||  
|-|-|  
|參數|描述|  
|[in] `uiCmd`|指定要檢查的命令。|  
  
### <a name="return-value"></a>傳回值  
 非零，如果經常使用的命令。否則為 0。  
  
### <a name="remarks"></a>備註  
 這個方法會傳回 0，如果總命令的用法， `m_nTotalUsage`，為 0。 否則，這個方法會傳回非零，如果指定的命令使用其中的百分比大於最小的百分比， `m_nMinUsagePercentage`。 根據預設，架構會將最小百分比設定為 5。 您可以使用覆寫此值[CMFCCmdUsageCount::SetOptions](#setoptions)方法。 如果百分比下限為 0，則這個方法會傳回非零，如果指定的命令計數大於 0。  
  
 [CMFCToolBar::IsCommandRarelyUsed](../../mfc/reference/cmfctoolbar-class.md#iscommandrarelyused)使用這個方法來判斷命令是否很少使用。  
  
##  <a name="reset"></a>CMFCCmdUsageCount::Reset  
 清除所有命令的使用量。  
  
```  
void Reset();
```  
  
### <a name="remarks"></a>備註  
 呼叫這個方法來清除所有項目從對應結構的命令計數`m_CmdUsage`，以及重設總命令的用法， `m_nTotalUsage`、 計數器為 0。  
  
##  <a name="serialize"></a>CMFCCmdUsageCount::Serialize  
 此物件會讀取封存檔，或將它寫入至封存檔。  
  
```  
virtual void Serialize(CArchive& ar);
```  
  
### <a name="parameters"></a>參數  
  
|||  
|-|-|  
|參數|描述|  
|[in] `ar`|A`CArchive`来序列化或物件。|  
  
### <a name="remarks"></a>備註  
 這個方法會序列化指令計數的對應結構`m_CmdUsage`，和總計 命令使用方式`m_nTotalUsage`、 計數器或指定的封存。  
  
 序列化範例，請參閱[序列化︰ 序列化物件](../../mfc/serialization-serializing-an-object.md)。  
  
##  <a name="setoptions"></a>CMFCCmdUsageCount::SetOptions  
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
|[in] `nStartCount`|所有追蹤命令新初始的計數。|  
|[in] `nMinUsagePercentage`|新的最小的使用量百分比。|  
  
### <a name="return-value"></a>傳回值  
 `TRUE`如果方法成功，`FALSE`如果`nMinUsagePercentage`參數是大於或等於 100。  
  
### <a name="remarks"></a>備註  
 這個方法會設定為共用`CMFCCmdUsageCount`類別資料成員`m_nStartCount`和`m_nMinUsagePercentage`至`nStartCount`和`nMinUsagePercentage`分別。 `m_nStartCount`使用[CMFCCmdUsageCount::HasEnoughInformation](#hasenoughinformation)方法，以判斷此物件是否已收集追蹤資料的最小數量。 `m_nMinUsagePercentage`使用[CMFCCmdUsageCount::IsFreqeuntlyUsedCmd](#isfreqeuntlyusedcmd)方法，以判斷是否經常使用指定的命令。  
  
 偵錯組建中，這個方法產生判斷提示失敗如果`nMinUsagePercentage`參數是大於或等於 100。  
  
## <a name="see-also"></a>另請參閱  
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [類別](../../mfc/reference/mfc-classes.md)   
 [CMFCToolBar 類別](../../mfc/reference/cmfctoolbar-class.md)

