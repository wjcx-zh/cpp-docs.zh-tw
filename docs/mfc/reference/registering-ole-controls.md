---
title: 註冊 OLE 控制項
ms.date: 11/04/2016
helpviewer_keywords:
- registering OLE controls
- OLE controls [MFC], registering
ms.assetid: 73c45b7f-7dbc-43f5-bd17-dd77c6acec72
ms.openlocfilehash: 2f2d7872e8b9369b5eef283e5b52a54c29afd563
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81372963"
---
# <a name="registering-ole-controls"></a>註冊 OLE 控制項

OLE 控制項就像其他 OLE 伺服器物件，可以由其他 OLE 感知應用程式存取。 只要註冊控制項的類型程式庫和類別即可。

下列函式可讓您在 Windows 註冊資料庫中加入和移除控制項的類別、屬性頁和類型程式庫：

### <a name="registering-ole-controls"></a>註冊 OLE 控制項

|||
|-|-|
|[AfxOleRegisterControlClass](#afxoleregistercontrolclass)|將控制項的類別加入至註冊資料庫。|
|[AfxOleRegisterPropertyPageClass](#afxoleregisterpropertypageclass)|將控制項屬性頁加入至註冊資料庫。|
|[AfxOleRegisterTypeLib](#afxoleregistertypelib)|將控制項的類型程式庫加入至註冊資料庫。|
|[AfxOleUnregisterClass](#afxoleunregisterclass)|從註冊資料庫移除控制項類別或屬性頁類別。|
|[AfxOleUnregisterTypeLib](#afxoleunregistertypelib)|從註冊資料庫移除控制項的類型程式庫。|

通常在控制項 DLL 實作 `AfxOleRegisterTypeLib` 時呼叫 `DllRegisterServer`。 同樣地，`AfxOleUnregisterTypeLib` 是由 `DllUnregisterServer` 呼叫。 通常 `AfxOleRegisterControlClass`、`AfxOleRegisterPropertyPageClass` 和 `AfxOleUnregisterClass` 是由控制項的 Class Factory 或屬性頁的 `UpdateRegistry` 成員函式呼叫。

## <a name="afxoleregistercontrolclass"></a><a name="afxoleregistercontrolclass"></a>AfxOle 註冊控制類

將控制類註冊到 Windows 註冊資料庫。

```
BOOL AFXAPI AfxOleRegisterControlClass(
    HINSTANCE hInstance,
    REFCLSID clsid,
    LPCTSTR pszProgID,
    UINT idTypeName,
    UINT idBitmap,
    int nRegFlags,
    DWORD dwMiscStatus,
    REFGUID tlid,
    WORD wVerMajor,
    WORD wVerMinor);
```

### <a name="parameters"></a>參數

*hInstance*<br/>
與控制類關聯的模組的實例句柄。

*Clsid*<br/>
控制項的唯一類別 ID。

*pszProgID*<br/>
控制項的唯一程式 ID。

*idType 名稱*<br/>
包含控制項的使用者可讀類型名稱的字串的資源 ID。

*idBitmap*<br/>
用於表示工具列或調色板中的 OLE 控制項的位圖的資源 ID。

*nRegFlags*<br/>
包含以下一個或多個標誌:

- `afxRegInsertable`允許控制項顯示在 OLE 物件的「插入物件」對話框中。

- `afxRegApartmentThreading`將註冊表中的線程模型設置為線程模型_公寓。

- `afxRegFreeThreading`將註冊表中的線程模型設置為線程模型_自由。

   可以組合兩個標誌`afxRegApartmentThreading``afxRegFreeThreading`並設置線程模型_兩者。 有關線程模型註冊的詳細資訊,請參閱 Windows SDK 中的[InprocServer32。](/windows/win32/com/inprocserver32)

> [!NOTE]
> 在 MFC 4.2 之前的 MFC 版本中 **,int** *nRegFlags*參數是 BOOL 參數*bInsert,* 允許或不允許從「插入物件」對話框中插入控制項。

*dwMiscStatus*<br/>
包含以下一個或多個狀態標誌(有關標誌的說明,請參閱 Windows SDK 中的 OLEMISC 枚舉):

- OLEMISC_RECOMPOSEONRESIZE

- OLEMISC_ONLYICONIC

- OLEMISC_INSERTNOTREPLACE

- OLEMISC_STATIC

- OLEMISC_CANTLINKINSIDE

- OLEMISC_CANLINKBYOLE1

- OLEMISC_ISLINKOBJECT

- OLEMISC_INSIDEOUT

- OLEMISC_ACTIVATEWHENVISIBLE

- OLEMISC_RENDERINGISDEVICEINDEPENDENT

- OLEMISC_INVISIBLEATRUNTIME

- OLEMISC_ALWAYSRUN

- OLEMISC_ACTSLIKEBUTTON

- OLEMISC_ACTSLIKELABEL

- OLEMISC_NOUIACTIVATE

- OLEMISC_ALIGNABLE

- OLEMISC_IMEMODE

- OLEMISC_SIMPLEFRAME

- OLEMISC_SETCLIENTSITEFIRST

*tlid*<br/>
控件類的唯一 ID。

*wVerMajor*<br/>
控件類的主要版本號。

*wVerMinor*<br/>
控件類的次要版本號。

### <a name="return-value"></a>傳回值

如果已註冊控制類,則非零;否則 0。

### <a name="remarks"></a>備註

這允許 OLE 控制感知的容器使用控制項。 `AfxOleRegisterControlClass`使用控制項名稱和位置在系統上更新註冊表,並設置控制件在註冊表中支援的線程模型。 有關詳細資訊,請參閱[技術說明 64](../../mfc/tn064-apartment-model-threading-in-activex-controls.md),"OLE 控制件中的公寓-模型線程",以及有關 Windows SDK 中[的進程和線程](/windows/win32/ProcThread/about-processes-and-threads)。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCAxCtl#11](../../mfc/reference/codesnippet/cpp/registering-ole-controls_1.cpp)]

上面的範例展示如何`AfxOleRegisterControlClass`使用可插入標誌和儲存模式 ORed 的標誌一起呼叫以建立第六個參數:

[!code-cpp[NVC_MFCAxCtl#12](../../mfc/reference/codesnippet/cpp/registering-ole-controls_2.cpp)]

該控件將顯示在已啟用容器的「插入物件」對話框中,並且它將具有單元模型感知功能。 單元模型感知控件必須確保靜態類數據受鎖保護,因此,當一個單元中的控件訪問靜態數據時,計劃程式不會將其禁用,並且同一類的另一個實例開始使用相同的靜態數據。 對靜態數據的任何訪問都將被關鍵節代碼包圍。

### <a name="requirements"></a>需求

  **頭**afxctl.h

## <a name="afxoleregisterpropertypageclass"></a><a name="afxoleregisterpropertypageclass"></a>AfxOle 註冊屬性頁類

將屬性頁類註冊到 Windows 註冊資料庫。

```
BOOL AFXAPI AfxOleRegisterPropertyPageClass(
   HINSTANCE hInstance,
   REFCLSID  clsid,
   UINT idTypeName,
   int nRegFlags);
```

### <a name="parameters"></a>參數

*hInstance*<br/>
與屬性頁類關聯的模組的實例句柄。

*Clsid*<br/>
屬性頁的唯一類 ID。

*idType 名稱*<br/>
包含屬性頁使用者可讀名稱的字串的資源 ID。

*nRegFlags*<br/>
可能包含標誌:

- `afxRegApartmentThreading`將註冊表中的線程模型設置為線程模型 = 公寓。

> [!NOTE]
> 在 MFC 4.2 之前的 MFC 版本中 **,int** *nRegFlags*參數不可用。 另請注意,`afxRegInsertable`該旗標不是屬性頁的有效選項,如果設定了「已設定」,則會導致 MFC 中的 ASSERT

### <a name="return-value"></a>傳回值

如果已註冊控制類,則非零;否則 0。

### <a name="remarks"></a>備註

這允許具有 OLE 控制感知的容器使用屬性頁。 `AfxOleRegisterPropertyPageClass`使用屬性頁名稱及其在系統上的位置更新註冊表,並設置控制項在註冊表中支援的線程模型。 有關詳細資訊,請參閱[技術說明 64](../../mfc/tn064-apartment-model-threading-in-activex-controls.md),"OLE 控制件中的公寓-模型線程",以及有關 Windows SDK 中[的進程和線程](/windows/win32/ProcThread/about-processes-and-threads)。

### <a name="requirements"></a>需求

  **頭**afxctl.h

## <a name="afxoleregistertypelib"></a><a name="afxoleregistertypelib"></a>AfxOle 註冊類型 Lib

向 Windows 註冊資料庫註冊類型程式庫，並且允許其他 OLE 控制項感知的容器使用類型程式庫。

```
BOOL AfxOleRegisterTypeLib(
    HINSTANCE hInstance,
    REFGUID tlid,
    LPCTSTR pszFileName = NULL,
    LPCTSTR pszHelpDir  = NULL);
```

### <a name="parameters"></a>參數

*hInstance*<br/>
類型程式庫相關的應用程式的執行個體控制代碼。

*tlid*<br/>
類型程式庫的唯一 ID。

*pszFileName*<br/>
指向控制項的當地語系化類型程式庫 (.TLB) 檔案的選擇性檔名的指標。

*pszHelpDir*<br/>
可以找到此類型程式庫的說明檔的目錄名稱。 如果為 NULL，則假設說明檔在和類型程式庫相同的目錄中。

### <a name="return-value"></a>傳回值

如果類型程式庫已註冊則為非零，否則為 0。

### <a name="remarks"></a>備註

此函式會以類型程式庫名稱及其在系統上的位置更新登錄。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCAutomation#7](../../mfc/codesnippet/cpp/registering-ole-controls_3.cpp)]

[!code-cpp[NVC_MFCAutomation#8](../../mfc/codesnippet/cpp/registering-ole-controls_4.cpp)]

### <a name="requirements"></a>需求

  **標題**afxdisp.h

## <a name="afxoleunregisterclass"></a><a name="afxoleunregisterclass"></a>AfxOleUn 寄存器類

從 Windows 註冊資料庫中刪除控制項或屬性頁類項目。

```
BOOL AFXAPI AfxOleUnregisterClass(REFCLSID clsID, LPCSTR pszProgID);
```

### <a name="parameters"></a>參數

*Clsid*<br/>
控件或屬性頁的唯一類 ID。

*pszProgID*<br/>
控制項或屬性頁的唯一程式 ID。

### <a name="return-value"></a>傳回值

如果控件或屬性頁類已成功取消註冊,則非零;否則 0。

### <a name="requirements"></a>需求

  **頭**afxctl.h

## <a name="afxoleunregistertypelib"></a><a name="afxoleunregistertypelib"></a>AfxOleUn寄存器類型Lib

呼叫此函數從 Windows 註冊資料庫中刪除類型庫條目。

```
BOOL AFXAPI AfxOleUnregisterTypeLib(REFGUID tlID);
```

### <a name="parameters"></a>參數

*tlID*<br/>
類型程式庫的唯一 ID。

### <a name="return-value"></a>傳回值

如果類型庫已成功取消註冊,則非零;否則 0。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCAxCtl#13](../../mfc/reference/codesnippet/cpp/registering-ole-controls_5.cpp)]

### <a name="requirements"></a>需求

  **標題**afxdisp.h

## <a name="see-also"></a>另請參閱

[巨集和全域](../../mfc/reference/mfc-macros-and-globals.md)
