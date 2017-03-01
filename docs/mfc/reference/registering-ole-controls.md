---
title: "註冊 OLE 控制項 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vc.mfc.macros.ole
dev_langs:
- C++
helpviewer_keywords:
- registering OLE controls
- OLE controls, registering
ms.assetid: 73c45b7f-7dbc-43f5-bd17-dd77c6acec72
caps.latest.revision: 15
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
translationtype: Machine Translation
ms.sourcegitcommit: 17a158366f94d27b7a46917282425d652e6b9042
ms.openlocfilehash: 9c54fb7dc3802e78c8dc68df02ff55ef4732a36b
ms.lasthandoff: 02/24/2017

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
  
##  <a name="a-nameafxoleregistercontrolclassa--afxoleregistercontrolclass"></a><a name="afxoleregistercontrolclass"></a>AfxOleRegisterControlClass  
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
 `hInstance`  
 模組相關聯的控制項類別的執行個體控制代碼。  
  
 `clsid`  
 控制項的唯一類別 ID。  
  
 `pszProgID`  
 控制項的唯一程式 ID。  
  
 `idTypeName`  
 包含控制項的使用者可讀取的型別名稱的字串資源識別碼。  
  
 *idBitmap*  
 用來代表工具列或調色盤中的 OLE 控制項的點陣圖資源識別碼。  
  
 `nRegFlags`  
 包含一或多個下列旗標︰  
  
- `afxRegInsertable`可讓控制項出現在 OLE 物件的 [插入物件] 對話方塊中。  
  
- `afxRegApartmentThreading`在 ThreadingModel 登錄中設定執行緒模型 = Apartment。  
  
- `afxRegFreeThreading`在 ThreadingModel 登錄中設定執行緒模型 = 免費。  
  
     您可以結合兩個旗標`afxRegApartmentThreading`和`afxRegFreeThreading`設定 ThreadingModel = Both。 請參閱[InprocServer32](http://msdn.microsoft.com/library/windows/desktop/ms682390)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]的執行緒模型註冊的詳細資訊。  
  
> [!NOTE]
>  在 MFC 4.2 之前的 MFC 版本`int``nRegFlags`參數是**BOOL**參數， *bInsertable*，可允許或不允許從 [插入物件] 對話方塊中插入控制項。  
  
 *dwMiscStatus*  
 包含一或多個下列狀態旗標 (旗標的說明，請參閱**OLEMISC**中的列舉[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]):  
  
-   OLEMISC_RECOMPOSEONRESIZE  
  
-   OLEMISC_ONLYICONIC  
  
-   OLEMISC_INSERTNOTREPLACE  
  
-   OLEMISC_STATIC  
  
-   OLEMISC_CANTLINKINSIDE  
  
-   OLEMISC_CANLINKBYOLE1  
  
-   OLEMISC_ISLINKOBJECT  
  
-   OLEMISC_INSIDEOUT  
  
-   OLEMISC_ACTIVATEWHENVISIBLE  
  
-   OLEMISC_RENDERINGISDEVICEINDEPENDENT  
  
-   OLEMISC_INVISIBLEATRUNTIME  
  
-   OLEMISC_ALWAYSRUN  
  
-   OLEMISC_ACTSLIKEBUTTON  
  
-   OLEMISC_ACTSLIKELABEL  
  
-   OLEMISC_NOUIACTIVATE  
  
-   OLEMISC_ALIGNABLE  
  
-   OLEMISC_IMEMODE  
  
-   OLEMISC_SIMPLEFRAME  
  
-   OLEMISC_SETCLIENTSITEFIRST  
  
 *tlid*  
 控制項類別的唯一識別碼。  
  
 `wVerMajor`  
 控制項類別的主要版本號碼。  
  
 `wVerMinor`  
 控制項類別的次要版本號碼。  
  
### <a name="return-value"></a>傳回值  
 非零，如果已註冊控制項類別。否則為 0。  
  
### <a name="remarks"></a>備註  
 這可讓控制項的 OLE 控制項感知的容器使用。 `AfxOleRegisterControlClass`以控制項的名稱和位置，在系統上的更新登錄，也會設定控制項支援在登錄中的執行緒模型。 如需詳細資訊，請參閱[技術附註 64](../../mfc/tn064-apartment-model-threading-in-activex-controls.md)，「 Apartment Model 執行緒在 OLE 控制項，」 和[相關處理序和執行緒](http://msdn.microsoft.com/library/windows/desktop/ms681917)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFCAxCtl #&11;](../../mfc/reference/codesnippet/cpp/registering-ole-controls_1.cpp)]  
  
 上述範例將示範如何`AfxOleRegisterControlClass`呼叫的旗標可插入和 apartment 的旗標型號 or 運算，以建立第六個參數︰  
  
 [!code-cpp[NVC_MFCAxCtl #&12;](../../mfc/reference/codesnippet/cpp/registering-ole-controls_2.cpp)]  
  
 控制項將會出現在 [插入物件] 對話方塊啟用狀態的容器，並將予以公寓模型感知。 公寓模型感知控制項，讓一個 apartment 中的控制項存取靜態資料，雖然它不停用排程器完成時，並使用相同的靜態資料的相同類別的另一個執行個體啟動之前，必須確定資料會受到鎖定時，該靜態類別。 重要區段的程式碼會包含任何靜態資料的存取。  
  
### <a name="requirements"></a>需求  
  **標頭**afxctl.h  
  
##  <a name="a-nameafxoleregisterpropertypageclassa--afxoleregisterpropertypageclass"></a><a name="afxoleregisterpropertypageclass"></a>AfxOleRegisterPropertyPageClass  
 向 Windows 註冊資料庫中的屬性頁類別。  
  
```  
BOOL AFXAPI AfxOleRegisterPropertyPageClass(
   HINSTANCE hInstance,  
   REFCLSID  clsid,  
   UINT idTypeName,  
   int nRegFlags); 
```  
  
### <a name="parameters"></a>參數  
 `hInstance`  
 模組屬性頁類別相關聯的執行個體控制代碼。  
  
 `clsid`  
 屬性頁的唯一類別 ID。  
  
 `idTypeName`  
 包含屬性頁面的使用者可讀名稱的字串資源識別碼。  
  
 `nRegFlags`  
 可能包含旗標︰  
  
- `afxRegApartmentThreading`在 ThreadingModel 登錄中設定執行緒模型 = Apartment。  
  
> [!NOTE]
>  在 MFC 4.2 之前的 MFC 版本`int``nRegFlags`參數無法使用。 也請注意，`afxRegInsertable`旗標不是有效的選項屬性頁面，而且會判斷提示在 MFC 中如果設定  
  
### <a name="return-value"></a>傳回值  
 非零，如果已註冊控制項類別。否則為 0。  
  
### <a name="remarks"></a>備註  
 這可讓 OLE 控制項感知的容器所使用的屬性頁。 `AfxOleRegisterPropertyPageClass`更新登錄以屬性頁名稱及其在系統上的位置，也會設定控制項支援在登錄中的執行緒模型。 如需詳細資訊，請參閱[技術附註 64](../../mfc/tn064-apartment-model-threading-in-activex-controls.md)，「 Apartment Model 執行緒在 OLE 控制項，」 和[相關處理序和執行緒](http://msdn.microsoft.com/library/windows/desktop/ms681917)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
### <a name="requirements"></a>需求  
  **標頭**afxctl.h  
  
##  <a name="a-nameafxoleregistertypeliba--afxoleregistertypelib"></a><a name="afxoleregistertypelib"></a>AfxOleRegisterTypeLib  
 向 Windows 註冊資料庫註冊類型程式庫，並且允許其他 OLE 控制項感知的容器使用類型程式庫。  
  
```   
BOOL AfxOleRegisterTypeLib(
    HINSTANCE hInstance,  
    REFGUID tlid,  
    LPCTSTR pszFileName = NULL,  
    LPCTSTR pszHelpDir  = NULL); 
```  
  
### <a name="parameters"></a>參數  
 `hInstance`  
 類型程式庫相關的應用程式的執行個體控制代碼。  
  
 *tlid*  
 類型程式庫的唯一 ID。  
  
 *pszFileName*  
 指向控制項的當地語系化類型程式庫 (.TLB) 檔案的選擇性檔名的指標。  
  
 *pszHelpDir*  
 可以找到此類型程式庫的說明檔的目錄名稱。 如果**NULL**，假設為型別程式庫本身的相同目錄中的說明檔。  
  
### <a name="return-value"></a>傳回值  
 如果類型程式庫已註冊則為非零，否則為 0。  
  
### <a name="remarks"></a>備註  
 此函式會以類型程式庫名稱及其在系統上的位置更新登錄。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFCAutomation #&7;](../../mfc/codesnippet/cpp/registering-ole-controls_3.cpp)]  
  
 [!code-cpp[NVC_MFCAutomation #&8;](../../mfc/codesnippet/cpp/registering-ole-controls_4.cpp)]  
  
### <a name="requirements"></a>需求  
  **標頭**afxdisp.h  
  
##  <a name="a-nameafxoleunregisterclassa--afxoleunregisterclass"></a><a name="afxoleunregisterclass"></a>AfxOleUnregisterClass  
 從 Windows 註冊資料庫移除控制項或屬性頁面類別項目。  
  
```   
BOOL AFXAPI AfxOleUnregisterClass(REFCLSID clsID, LPCSTR pszProgID); 
```  
  
### <a name="parameters"></a>參數  
 *clsID*  
 控制項或屬性頁的唯一類別 ID。  
  
 `pszProgID`  
 控制項或屬性頁的唯一程式 ID。  
  
### <a name="return-value"></a>傳回值  
 非零，如果控制項或屬性頁面類別已成功移除註冊。否則為 0。  
  
### <a name="requirements"></a>需求  
  **標頭**afxctl.h  
  
##  <a name="a-nameafxoleunregistertypeliba--afxoleunregistertypelib"></a><a name="afxoleunregistertypelib"></a>AfxOleUnregisterTypeLib  
 呼叫此函式可從 Windows 註冊資料庫移除類型程式庫項目。  
  
```   
BOOL AFXAPI AfxOleUnregisterTypeLib(REFGUID tlID); 
```  
  
### <a name="parameters"></a>參數  
 `tlID`  
 類型程式庫的唯一 ID。  
  
### <a name="return-value"></a>傳回值  
 非零，如果型別程式庫已成功移除註冊。否則為 0。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFCAxCtl #&13;](../../mfc/reference/codesnippet/cpp/registering-ole-controls_5.cpp)]  

### <a name="requirements"></a>需求  
  **標頭**afxdisp.h  

## <a name="see-also"></a>另請參閱  
 [巨集和全域變數](../../mfc/reference/mfc-macros-and-globals.md)

