---
title: 註冊 OLE 控制項
ms.date: 11/04/2016
helpviewer_keywords:
- registering OLE controls
- OLE controls [MFC], registering
ms.assetid: 73c45b7f-7dbc-43f5-bd17-dd77c6acec72
ms.openlocfilehash: 0471bad0793779d0bc13a2bee41957381f56389f
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87214018"
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

## <a name="afxoleregistercontrolclass"></a><a name="afxoleregistercontrolclass"></a>AfxOleRegisterControlClass

向 Windows 註冊資料庫註冊控制項類別。

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
與控制項類別相關聯之模組的實例控制碼。

*clsid*<br/>
控制項的唯一類別 ID。

*pszProgID*<br/>
控制項的唯一程式 ID。

*idTypeName*<br/>
字串的資源識別碼，包含控制項的使用者可讀取型別名稱。

*idBitmap*<br/>
用來表示工具列或調色板中 OLE 控制項之點陣圖的資源識別碼。

*nRegFlags*<br/>
包含下列一個或多個旗標：

- `afxRegInsertable`允許控制項出現在 OLE 物件的 [插入物件] 對話方塊中。

- `afxRegApartmentThreading`將登錄中的執行緒模型設定為 ThreadingModel = 公寓。

- `afxRegFreeThreading`將登錄中的執行緒模型設定為 ThreadingModel = Free。

   您可以結合這兩個旗標 `afxRegApartmentThreading` ，並 `afxRegFreeThreading` 設定 ThreadingModel = 兩者。 如需執行緒模型註冊的詳細資訊，請參閱 Windows SDK 中的[InprocServer32](/windows/win32/com/inprocserver32) 。

> [!NOTE]
> 在 MFC 4.2 之前的 MFC 版本中， **`int`** *nRegFlags*參數是一種 BOOL 參數*bInsertable*，允許或禁止從 [插入物件] 對話方塊插入控制項。

*dwMiscStatus*<br/>
包含下列一個或多個狀態旗標（如需旗標的描述，請參閱 Windows SDK 中的 OLEMISC 列舉）：

- OLEMISC_RECOMPOSEONRESIZE

- OLEMISC_ONLYICONIC

- OLEMISC_INSERTNOTREPLACE

- OLEMISC_STATIC

- OLEMISC_CANTLINKINSIDE

- OLEMISC_CANLINKBYOLE1

- OLEMISC_ISLINKOBJECT

- OLEMISC_INSIDEOUT

- OLEMISC_ACTI加值稅EWHENVISIBLE

- OLEMISC_RENDERINGISDEVICEINDEPENDENT

- OLEMISC_INVISIBLEATRUNTIME

- OLEMISC_ALWAYSRUN

- OLEMISC_ACTSLIKEBUTTON

- OLEMISC_ACTSLIKELABEL

- OLEMISC_NOUIACTI加值稅E

- OLEMISC_ALIGNABLE

- OLEMISC_IMEMODE

- OLEMISC_SIMPLEFRAME

- OLEMISC_SETCLIENTSITEFIRST

*tlid*<br/>
控制項類別的唯一識別碼。

*wVerMajor*<br/>
控制項類別的主要版本號碼。

*wVerMinor*<br/>
控制項類別的次要版本號碼。

### <a name="return-value"></a>傳回值

如果已註冊控制項類別，則為非零。否則為0。

### <a name="remarks"></a>備註

這可讓具有 OLE 控制項感知功能的容器使用控制項。 `AfxOleRegisterControlClass`以控制項的名稱和系統上的位置更新登錄，同時設定控制項在登錄中支援的執行緒模型。 如需詳細資訊，請參閱[技術提示 64](../../mfc/tn064-apartment-model-threading-in-activex-controls.md)、OLE 控制項中的公寓模型執行緒，以及 Windows SDK 中的[進程和執行緒](/windows/win32/ProcThread/about-processes-and-threads)。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCAxCtl#11](../../mfc/reference/codesnippet/cpp/registering-ole-controls_1.cpp)]

上述範例示範如何 `AfxOleRegisterControlClass` 使用 [可插入] 旗標來呼叫，並將 [公寓模型 ORed] 的旗標用在一起以建立第六個參數：

[!code-cpp[NVC_MFCAxCtl#12](../../mfc/reference/codesnippet/cpp/registering-ole-controls_2.cpp)]

控制項將會顯示在已啟用容器的 [插入物件] 對話方塊中，而且它將會是 [單元模型感知]。 單元模型感知控制項必須確保靜態類別資料受到鎖定的保護，如此一來，當一個單元中的控制項正在存取靜態資料時，排程器就不會在完成前停用它，而且相同類別的另一個實例會使用相同的靜態資料開始。 對靜態資料的任何存取都會以重要區段程式碼括住。

### <a name="requirements"></a>需求

  **標頭**afxctl.h。h

## <a name="afxoleregisterpropertypageclass"></a><a name="afxoleregisterpropertypageclass"></a>AfxOleRegisterPropertyPageClass

向 Windows 註冊資料庫註冊屬性頁類別。

```
BOOL AFXAPI AfxOleRegisterPropertyPageClass(
   HINSTANCE hInstance,
   REFCLSID  clsid,
   UINT idTypeName,
   int nRegFlags);
```

### <a name="parameters"></a>參數

*hInstance*<br/>
與屬性頁類別相關聯之模組的實例控制碼。

*clsid*<br/>
屬性頁的唯一類別 ID。

*idTypeName*<br/>
字串的資源識別碼，包含屬性頁使用者可讀取的名稱。

*nRegFlags*<br/>
可能包含旗標：

- `afxRegApartmentThreading`將登錄中的執行緒模型設定為 ThreadingModel = 公寓。

> [!NOTE]
> 在 MFC 4.2 之前的 MFC 版本中， **`int`** 無法使用*nRegFlags*參數。 另請注意，此 `afxRegInsertable` 旗標不是屬性頁的有效選項，如果已設定，則會在 MFC 中產生判斷提示

### <a name="return-value"></a>傳回值

如果已註冊控制項類別，則為非零。否則為0。

### <a name="remarks"></a>備註

這可讓具有 OLE 控制項感知功能的容器使用屬性頁。 `AfxOleRegisterPropertyPageClass`使用屬性頁名稱和其在系統上的位置來更新登錄，同時設定控制項在登錄中支援的執行緒模型。 如需詳細資訊，請參閱[技術提示 64](../../mfc/tn064-apartment-model-threading-in-activex-controls.md)、OLE 控制項中的公寓模型執行緒，以及 Windows SDK 中的[進程和執行緒](/windows/win32/ProcThread/about-processes-and-threads)。

### <a name="requirements"></a>需求

  **標頭**afxctl.h。h

## <a name="afxoleregistertypelib"></a><a name="afxoleregistertypelib"></a>AfxOleRegisterTypeLib

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

  **標頭**afxdisp.h。h

## <a name="afxoleunregisterclass"></a><a name="afxoleunregisterclass"></a>AfxOleUnregisterClass

從 Windows 註冊資料庫移除控制項或屬性頁類別專案。

```
BOOL AFXAPI AfxOleUnregisterClass(REFCLSID clsID, LPCSTR pszProgID);
```

### <a name="parameters"></a>參數

*clsID*<br/>
控制項或屬性頁的唯一類別 ID。

*pszProgID*<br/>
控制項或屬性頁的唯一程式識別碼。

### <a name="return-value"></a>傳回值

如果成功取消註冊控制項或屬性頁類別，則為非零;否則為0。

### <a name="requirements"></a>需求

  **標頭**afxctl.h。h

## <a name="afxoleunregistertypelib"></a><a name="afxoleunregistertypelib"></a>AfxOleUnregisterTypeLib

呼叫此函式可從 Windows 註冊資料庫中移除類型程式庫專案。

```
BOOL AFXAPI AfxOleUnregisterTypeLib(REFGUID tlID);
```

### <a name="parameters"></a>參數

*tlID*<br/>
類型程式庫的唯一 ID。

### <a name="return-value"></a>傳回值

如果類型程式庫已成功取消註冊，則為非零。否則為0。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCAxCtl#13](../../mfc/reference/codesnippet/cpp/registering-ole-controls_5.cpp)]

### <a name="requirements"></a>需求

  **標頭**afxdisp.h。h

## <a name="see-also"></a>另請參閱

[巨集和全域](../../mfc/reference/mfc-macros-and-globals.md)
