---
title: 應用程式控制 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- vc.mfc.macros
dev_langs:
- C++
helpviewer_keywords:
- application control [MFC]
ms.assetid: c1f69f15-e0fe-4515-9f36-d63d31869deb
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 3b06302d330ec8677a3de9b3ccaebf0b7b237b0e
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/25/2018
ms.locfileid: "50053887"
---
# <a name="application-control"></a>應用程式控制

OLE 會需要應用程式和其物件的實際控制。 OLE 系統 Dll 必須能夠啟動和自動發行的應用程式、 協調其生產環境和修改的物件，等等。 本主題中的函式符合這些需求。 除了由 OLE 系統 Dll 呼叫，這些函式有時必須呼叫以及應用程式。

### <a name="application-control"></a>應用程式控制

|||
|-|-|
|[AfxOleCanExitApp](#afxolecanexitapp)|指示應用程式是否可以結束。|
|[AfxOleGetMessageFilter](#afxolegetmessagefilter)|擷取應用程式的目前訊息篩選器。|
|[AfxOleGetUserCtrl](#afxolegetuserctrl)|擷取目前使用者控制旗標。|
|[AfxOleSetUserCtrl](#afxolesetuserctrl)|設定或清除使用者控制旗標。|
|[AfxOleLockApp](#afxolelockapp)|架構的應用程式中的作用中物件的數字的全域計數會遞增。|
|[AfxOleLockControl](#afxolelockcontrol)| 鎖定指定之控制項的 class factory。 |
|[AfxOleUnlockApp](#afxoleunlockapp)|遞減架構的應用程式中的作用中物件數目的計數。|
|[AfxOleUnlockControl](#afxoleunlockcontrol)| 取消鎖定指定之控制項的 class factory。 |
|[AfxOleRegisterServerClass](#afxoleregisterserverclass)|OLE 系統登錄中註冊伺服器。|
|[AfxOleSetEditMenu](#afxoleseteditmenu)|實作的使用者介面*typename*物件命令。|

##  <a name="afxolecanexitapp"></a>  AfxOleCanExitApp

指示應用程式是否可以結束。

```
BOOL AFXAPI AfxOleCanExitApp();
```

### <a name="return-value"></a>傳回值

如果應用程式可結束則非零，否則為 0。

### <a name="remarks"></a>備註

如果對應用程式物件有未完成的參考，則不應該結束。 全域函式 `AfxOleLockApp` 和 `AfxOleUnlockApp` 分別會遞增和遞減應用程式物件的參考計數。 這個計數器為非零值時，應用程式不應該結束。 如果計數器是非零值，當使用者從 [系統] 功能表選擇 [關閉]，或從 [檔案] 功能表選擇 [結束] 時，應用程式的主視窗將會隱藏 (不會終結)。 架構會呼叫此函式`CFrameWnd::OnClose`。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCAutomation#2](../../mfc/codesnippet/cpp/application-control_1.cpp)]

## <a name="requirements"></a>需求

**標頭**: afxdisp.h

##  <a name="afxolegetmessagefilter"></a>  AfxOleGetMessageFilter

擷取應用程式的目前訊息篩選器。

```
COleMessageFilter* AFXAPI AfxOleGetMessageFilter();
```

### <a name="return-value"></a>傳回值

指向目前訊息篩選器的指標。

### <a name="remarks"></a>備註

就像您會呼叫 `COleMessageFilter` 來存取目前應用程式物件一般，請呼叫這個函式來存取目前的 `AfxGetApp` 衍生物件。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCAutomation#3](../../mfc/codesnippet/cpp/application-control_2.cpp)]

[!code-cpp[NVC_MFCAutomation#4](../../mfc/codesnippet/cpp/application-control_3.cpp)]

### <a name="requirements"></a>需求

**標頭**: afxwin.h

##  <a name="afxolegetuserctrl"></a>  AfxOleGetUserCtrl

擷取目前使用者控制旗標。

```
BOOL AFXAPI AfxOleGetUserCtrl();
```

### <a name="return-value"></a>傳回值

如果使用者在控制應用程式則為非零；否則為 0。

### <a name="remarks"></a>備註

當使用者具有已明確開啟或建立的新文件時，應用程式是在使用者的控制之下。 如果應用程式不是由 OLE 系統 DLL 啟動，也就是說如果使用者是使用系統殼層啟動應用程式，表示仍然在使用者的控制之下。

### <a name="requirements"></a>需求

**標頭**: afxdisp.h

##  <a name="afxolesetuserctrl"></a>  AfxOleSetUserCtrl

設定或清除使用者控制旗標，所述的參考`AfxOleGetUserCtrl`。

```
void AFXAPI AfxOleSetUserCtrl(BOOL bUserCtrl);
```

### <a name="parameters"></a>參數

*bUserCtrl*<br/>
指定是否要設定或清除使用者控制旗標。

### <a name="remarks"></a>備註

架構會呼叫此函式時的使用者建立或載入文件，但文件載入，或透過間接的動作，例如從容器應用程式載入的內嵌的物件建立時，不。

如果您的應用程式中的其他動作應該將使用者放在應用程式的控制，請呼叫此函式。

### <a name="requirements"></a>需求

**標頭**: afxdisp.h

##  <a name="afxolelockapp"></a>  AfxOleLockApp

架構的應用程式中的作用中物件的數字的全域計數會遞增。

```
void AFXAPI AfxOleLockApp();
```

### <a name="remarks"></a>備註

架構會保留您作用中的應用程式中的物件數目的計數。 `AfxOleLockApp`和`AfxOleUnlockApp`函式分別遞增和遞減此計數。

當使用者嘗試關閉具有作用中物件的應用程式-應用程式的使用中的物件計數為非零值，framework 會隱藏使用者的檢視，而不是完全關閉應用程式。 `AfxOleCanExitApp`函式會指出是否可以終止應用程式。

呼叫`AfxOleLockApp`從任何如果不想要終結時由用戶端應用程式仍在使用該物件會公開 OLE 介面的物件。 同時也呼叫`AfxOleUnlockApp`呼叫的任何物件的解構函式中`AfxOleLockApp`建構函式。 根據預設， `COleDocument` （和衍生類別） 會自動鎖定和解除鎖定應用程式。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCAutomation#5](../../mfc/codesnippet/cpp/application-control_4.cpp)]

### <a name="requirements"></a>需求

**標頭**: afxdisp.h

##  <a name="afxoleunlockapp"></a>  AfxOleUnlockApp

遞減架構的應用程式中的作用中物件計數。

```
void AFXAPI AfxOleUnlockApp();
```

### <a name="remarks"></a>備註

請參閱`AfxOleLockApp`如需詳細資訊。

當作用中物件的數目到達零時，`AfxOleOnReleaseAllObjects`呼叫。

### <a name="example"></a>範例

範例，請參閱[AfxOleLockApp](#afxolelockapp)。

### <a name="requirements"></a>需求

**標頭**: afxdisp.h

## <a name="afxolelockcontrol"></a>AfxOleLockControl

鎖定指定控制項的 Class Factory，以便動態建立與記憶體中保留之控制項相關聯的資料。

### <a name="syntax"></a>語法

```
BOOL AFXAPI AfxOleLockControl(  REFCLSID clsid  );
BOOL AFXAPI AfxOleLockControl( LPCTSTR lpszProgID );
```

### <a name="parameters"></a>參數

*clsid*<br/>
控制項的唯一類別 ID。

*lpszProgID*<br/>
控制項的唯一程式 ID。

### <a name="return-value"></a>傳回值

如果已順利鎖定控制項的 Class Factory 則為非零值；否則為 0。

### <a name="remarks"></a>備註

這可大幅提升控制項的顯示速度。 例如，當您在對話方塊中建立控制項並使用 `AfxOleLockControl` 鎖定控制項時，就不需要每次在對話方塊顯示或終結時建立和刪除該控制項。 如果使用者重複開啟和關閉對話方塊，鎖定您的控制項可以大幅提升效能。 當您準備終結控制項時，請呼叫 `AfxOleUnlockControl`。

### <a name="example"></a>範例

```cpp
// Starts and locks control's (Microsoft Calendar) class factory.
// Control will remain in memory for lifetime of
// application or until AfxOleUnlockControl() is called.

AfxOleLockControl(_T("MSCAL.Calendar"));
```

### <a name="requirements"></a>需求

**標題:** afxwin.h

### <a name="see-also"></a>另請參閱

[巨集和全域](mfc-macros-and-globals.md)<br/>
[AfxOleUnlockControl](#afxoleunlockcontrol)

##  <a name="afxoleregisterserverclass"></a>  AfxOleRegisterServerClass

此函式可讓您在 OLE 系統登錄中註冊您的伺服器。

```
BOOL AFXAPI AfxOleRegisterServerClass(
    REFCLSID clsid,
    LPCTSTR lpszClassName,
    LPCTSTR lpszShortTypeName,
    LPCTSTR lpszLongTypeName,
    OLE_APPTYPE nAppType = OAT_SERVER,
    LPCTSTR* rglpszRegister = NULL,
    LPCTSTR* rglpszOverwrite = NULL);
```

### <a name="parameters"></a>參數

*clsid*<br/>
參考到伺服器的 OLE 類別識別碼。

*lpszClassName*<br/>
包含伺服器的物件的類別名稱的字串指標。

*lpszShortTypeName*<br/>
字串，包含伺服器的物件類型，例如"Chart"。 的簡短名稱的指標

*lpszLongTypeName*<br/>
指向字串，包含完整的名稱伺服器的物件類型，例如"Microsoft Excel 5.0 圖表 」。

*nAppType*<br/>
這種值取自 OLE_APPTYPE 列舉，指定 OLE 應用程式的類型。 可能的值如下所示：

- OAT_INPLACE_SERVER 伺服器具有完整伺服器的使用者介面。

- OAT_SERVER 伺服器支援僅內嵌。

- OAT_CONTAINER 容器支援內嵌連結。

- OAT_DISPATCH_OBJECT `IDispatch`-支援的物件。

*rglpszRegister*<br/>
代表索引鍵和值加入至 OLE 系統登錄，如果找不到索引鍵的任何現有值的字串指標的陣列。

*rglpszOverwrite*<br/>
代表索引鍵和值加入至 OLE 系統登錄，如果登錄包含指定的索引鍵的現有值的字串指標的陣列。

### <a name="return-value"></a>傳回值

如果成功註冊的伺服器類別，為非零否則為 0。

### <a name="remarks"></a>備註

大部分的應用程式可以使用`COleTemplateServer::Register`註冊應用程式的文件類型。 如果您的應用程式系統登錄格式不適用於一般的模式，您可以使用`AfxOleRegisterServerClass`更多的控制。

登錄是由一組索引鍵和值所組成。 *RglpszRegister*並*rglpszOverwrite*引數是字串指標的陣列，其中包含索引鍵和值，並以**NULL**字元 ( `'\0'`). 每個字串可以有可置換的參數，其位置標記的字元序列 *%1*透過 *%5*。

符號的資料會填入，如下所示：

|符號|值|
|------------|-----------|
|%1|類別識別碼，格式為字串|
|%2|類別名稱|
|%3|可執行檔路徑|
|%4|簡短的型別名稱|
|%5|Long 型別名稱|

### <a name="requirements"></a>需求

**標頭**: afxdisp.h

##  <a name="afxoleseteditmenu"></a>  AfxOleSetEditMenu

實作的使用者介面*typename*物件命令。

```
void AFXAPI AfxOleSetEditMenu(
    COleClientItem* pClient,
    CMenu* pMenu,
    UINT iMenuItem,
    UINT nIDVerbMin,
    UINT nIDVerbMax = 0,
    UINT nIDConvert = 0);
```

### <a name="parameters"></a>參數

*pClient*<br/>
用戶端 OLE 項目的指標。

*pMenu*<br/>
若要更新功能表物件的指標。

*iMenuItem*<br/>
若要更新的功能表項目的索引。

*nIDVerbMin*<br/>
對應至主要的動詞命令識別碼。

*nIDVerbMax*<br/>
對應到最後一個動詞命令識別碼。

*nIDConvert*<br/>
轉換功能表項目的 ID。

### <a name="remarks"></a>備註

伺服器會辨識主要動詞命令，如果功能表項目就會變成 「 動詞*typename*物件 」 和*nIDVerbMin*使用者選擇命令時，會傳送命令。 如果伺服器會辨識的數個動詞命令，則功能表項目會變成 「 *typename*物件 」 使用者選擇命令時，就會看到列出所有動詞命令的子功能表。 當使用者從子功能表中，選擇動詞*nIDVerbMin*如果選擇第一個指令動詞，傳送*nIDVerbMin* + 1 會傳送第二個動詞會選擇，依此類推。 預設值`COleDocument`實作會自動處理這項功能。

您必須在您的用戶端應用程式資源指令碼中的下列陳述式 (。RC) 檔案：

**#include \<afxolecl.rc >**

### <a name="requirements"></a>需求

**標頭**: afxole.h

## <a name="see-also"></a>另請參閱

[巨集和全域](../../mfc/reference/mfc-macros-and-globals.md)

## <a name="afxoleunlockcontrol"></a> AfxOleUnlockControl

取消鎖定指定之控制項的 class factory。

### <a name="syntax"></a>語法

```
BOOL AFXAPI AfxOleUnlockControl( REFCLSID clsid );
BOOL AFXAPI AfxOleUnlockControl( LPCTSTR lpszProgID );
```

### <a name="parameters"></a>參數

*clsid*<br/>
控制項的唯一類別 ID。

*lpszProgID*<br/>
控制項的唯一程式 ID。

### <a name="return-value"></a>傳回值

如果控制項的 class factory 已成功解除鎖定;，非零值。否則為 0。

### <a name="remarks"></a>備註

控制項已鎖定與`AfxOleLockControl`，如此一來，動態建立與控制項相關聯的資料保留在記憶體中。 這明顯可以加速控制項的顯示，因為控制項需要未建立並終結每一次，它會顯示。 當您準備終結控制項時，請呼叫 `AfxOleUnlockControl`。

### <a name="example"></a>範例

```cpp
// Unlock control's (Microsoft Calendar Control) class factory.

AfxOleUnlockControl(_T("MSCAL.Calendar"));

```

### <a name="requirements"></a>需求

**標題:** afxwin.h

### <a name="see-also"></a>另請參閱

[巨集和全域](mfc-macros-and-globals.md)<br/>
[AfxOleLockControl](#afxolelockcontrol)

