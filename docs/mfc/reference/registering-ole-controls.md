---
title: 註冊 OLE 控制項 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- vc.mfc.macros.ole
dev_langs:
- C++
helpviewer_keywords:
- registering OLE controls
- OLE controls [MFC], registering
ms.assetid: 73c45b7f-7dbc-43f5-bd17-dd77c6acec72
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: d9008ba16d52987e4d7f14b5692cdf349951f83a
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/19/2018
ms.locfileid: "46407708"
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

##  <a name="afxoleregistercontrolclass"></a>  AfxOleRegisterControlClass

向 Windows 註冊資料庫中的控制項類別。

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
控制項類別相關聯的模組執行個體控制代碼。

*clsid*<br/>
控制項的唯一類別 ID。

*pszProgID*<br/>
控制項的唯一程式 ID。

*idTypeName*<br/>
包含控制項的使用者可讀取的型別名稱的字串資源識別碼。

*idBitmap*<br/>
用來代表中 OLE 控制項的工具列或調色盤點陣圖的資源 ID。

*nRegFlags*<br/>
包含一或多個下列旗標：

- `afxRegInsertable` 可讓控制項出現在 OLE 物件的 [插入物件] 對話方塊中。

- `afxRegApartmentThreading` ThreadingModel 登錄中設定執行緒模型 = Apartment。

- `afxRegFreeThreading` ThreadingModel 登錄中設定執行緒模型 = 免費。

     您可以結合兩個旗標`afxRegApartmentThreading`和`afxRegFreeThreading`設 ThreadingModel = Both。 請參閱[InprocServer32](/windows/desktop/com/inprocserver32)的執行緒模型註冊的更多有關 Windows SDK 中。

> [!NOTE]
>  在 MFC 4.2 之前的 MFC 版本**int** *nRegFlags*參數，則 BOOL 參數*bInsertable*，可允許或不允許從 Insert 插入控制項[物件] 對話方塊。

*dwMiscStatus*<br/>
包含一或多個下列的狀態旗標 （適用於旗標的描述，請參閱 Windows SDK 中的 OLEMISC 列舉型別）：

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
控制項類別的唯一識別碼。

*wVerMajor*<br/>
控制項類別的主要版本號碼。

*wVerMinor*<br/>
控制項類別的次要版本號碼。

### <a name="return-value"></a>傳回值

非零值，如果已註冊的控制項類別;否則為 0。

### <a name="remarks"></a>備註

這可讓 OLE 控制項感知的容器所使用的控制項。 `AfxOleRegisterControlClass` 控制項的名稱和系統上的位置更新登錄，也會設定此控制項支援在登錄中的執行緒模型。 如需詳細資訊，請參閱[技術的附註 64](../../mfc/tn064-apartment-model-threading-in-activex-controls.md)，「 Apartment Model 執行緒中 OLE 控制項，」 並[相關處理序和執行緒](/windows/desktop/ProcThread/about-processes-and-threads)Windows SDK 中。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCAxCtl#11](../../mfc/reference/codesnippet/cpp/registering-ole-controls_1.cpp)]

上述範例示範如何`AfxOleRegisterControlClass`呼叫的旗標可插入和 apartment 的旗標模型 Or 在一起以建立第六個參數：

[!code-cpp[NVC_MFCAxCtl#12](../../mfc/reference/codesnippet/cpp/registering-ole-controls_2.cpp)]

控制項將會顯示在插入物件 對話方塊中，對於已啟用容器，並將予以 apartment 模型感知。 公寓模型感知控制項必須確保資料會受到鎖定，該靜態類別，以便 apartment 中的控制項存取靜態資料，而它不之前停用排程器完成，和另一個執行個體相同的類別可讓您開始使用在相同的靜態資料。 任何對靜態資料的存取會住重要區段的程式碼。

### <a name="requirements"></a>需求

  **標頭**afxctl.h

##  <a name="afxoleregisterpropertypageclass"></a>  AfxOleRegisterPropertyPageClass

向 Windows 註冊資料庫中的屬性頁類別。

```
BOOL AFXAPI AfxOleRegisterPropertyPageClass(
   HINSTANCE hInstance,
   REFCLSID  clsid,
   UINT idTypeName,
   int nRegFlags);
```

### <a name="parameters"></a>參數

*hInstance*<br/>
屬性頁類別相關聯的模組執行個體控制代碼。

*clsid*<br/>
屬性頁的唯一類別 ID。

*idTypeName*<br/>
包含屬性頁面的使用者可讀名稱的字串資源識別碼。

*nRegFlags*<br/>
可能包含旗標：

- `afxRegApartmentThreading` ThreadingModel 登錄中設定執行緒模型 = Apartment。

> [!NOTE]
>  在 MFC 4.2 之前的 MFC 版本**int** *nRegFlags*參數無法使用。 也請注意，`afxRegInsertable`旗標不是有效的選項屬性頁面，如果設定，將會造成判斷提示在 MFC 中

### <a name="return-value"></a>傳回值

非零值，如果已註冊的控制項類別;否則為 0。

### <a name="remarks"></a>備註

這可讓 OLE 控制項感知的容器所使用的 [屬性] 頁面。 `AfxOleRegisterPropertyPageClass` 屬性頁名稱與它在系統上的位置更新登錄，也會設定此控制項支援在登錄中的執行緒模型。 如需詳細資訊，請參閱[技術的附註 64](../../mfc/tn064-apartment-model-threading-in-activex-controls.md)，「 Apartment Model 執行緒中 OLE 控制項，」 並[相關處理序和執行緒](/windows/desktop/ProcThread/about-processes-and-threads)Windows SDK 中。

### <a name="requirements"></a>需求

  **標頭**afxctl.h

##  <a name="afxoleregistertypelib"></a>  AfxOleRegisterTypeLib

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
可以找到此類型程式庫的說明檔的目錄名稱。 如果是 NULL，說明檔會假設為本身之類型程式庫相同的目錄中。

### <a name="return-value"></a>傳回值

如果類型程式庫已註冊則為非零，否則為 0。

### <a name="remarks"></a>備註

此函式會以類型程式庫名稱及其在系統上的位置更新登錄。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCAutomation#7](../../mfc/codesnippet/cpp/registering-ole-controls_3.cpp)]

[!code-cpp[NVC_MFCAutomation#8](../../mfc/codesnippet/cpp/registering-ole-controls_4.cpp)]

### <a name="requirements"></a>需求

  **標頭**afxdisp.h

##  <a name="afxoleunregisterclass"></a>  AfxOleUnregisterClass

從 Windows 登錄資料庫移除的控制項或屬性頁面類別項目。

```
BOOL AFXAPI AfxOleUnregisterClass(REFCLSID clsID, LPCSTR pszProgID);
```

### <a name="parameters"></a>參數

*clsID*<br/>
控制項或屬性頁面的唯一類別 ID。

*pszProgID*<br/>
控制項或屬性頁面的唯一程式識別碼。

### <a name="return-value"></a>傳回值

已成功移除註冊; 控制項或屬性頁面類別時，非零值。否則為 0。

### <a name="requirements"></a>需求

  **標頭**afxctl.h

##  <a name="afxoleunregistertypelib"></a>  AfxOleUnregisterTypeLib

呼叫此函式可從 Windows 登錄資料庫移除類型程式庫項目。

```
BOOL AFXAPI AfxOleUnregisterTypeLib(REFGUID tlID);
```

### <a name="parameters"></a>參數

*tlID*<br/>
類型程式庫的唯一 ID。

### <a name="return-value"></a>傳回值

非零值，如果型別程式庫已成功取消登錄;否則為 0。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCAxCtl#13](../../mfc/reference/codesnippet/cpp/registering-ole-controls_5.cpp)]

### <a name="requirements"></a>需求

  **標頭**afxdisp.h

## <a name="see-also"></a>另請參閱

[巨集和全域](../../mfc/reference/mfc-macros-and-globals.md)
