---
title: "CNetAddressCtrl 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CNetAddressCtrl
- AFXCMN/CNetAddressCtrl
- AFXCMN/CNetAddressCtrl::CNetAddressCtrl
- AFXCMN/CNetAddressCtrl::Create
- AFXCMN/CNetAddressCtrl::CreateEx
- AFXCMN/CNetAddressCtrl::DisplayErrorTip
- AFXCMN/CNetAddressCtrl::GetAddress
- AFXCMN/CNetAddressCtrl::GetAllowType
- AFXCMN/CNetAddressCtrl::SetAllowType
dev_langs:
- C++
helpviewer_keywords:
- CNetAddressCtrl class
ms.assetid: cb4c6aca-3f49-4b52-b76c-65f57096155b
caps.latest.revision: 32
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
ms.sourcegitcommit: 0e0c08ddc57d437c51872b5186ae3fc983bb0199
ms.openlocfilehash: 03b08d13a9e456c5533b4dddce7f389a63a69c6d
ms.lasthandoff: 02/24/2017

---
# <a name="cnetaddressctrl-class"></a>CNetAddressCtrl 類別
`CNetAddressCtrl` 類別表示網路位址控制項，您可以用來輸入和驗證 IPv4、IPv6 和具名 DNS 位址的格式。  
  
## <a name="syntax"></a>語法  
  
```  
class CNetAddressCtrl : public CEdit  
```  
  
## <a name="members"></a>Members  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|描述|  
|----------|-----------------|  
|[CNetAddressCtrl::CNetAddressCtrl](#cnetaddressctrl)|建構 `CNetAddressCtrl` 物件。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|描述|  
|----------|-----------------|  
|[CNetAddressCtrl::Create](#create)|使用指定的樣式建立網路位址控制項，並將其附加至目前`CNetAddressCtrl`物件。|  
|[CNetAddressCtrl::CreateEx](#createex)|使用指定的延伸樣式建立網路位址控制項，並將其附加至目前`CNetAddressCtrl`物件。|  
|[CNetAddressCtrl::DisplayErrorTip](#displayerrortip)|當使用者在目前的網路位址控制項進入不支援的網路位址，會顯示錯誤汽球提示。|  
|[CNetAddressCtrl::GetAddress](#getaddress)|擷取目前的網路位址控制項相關聯的網路位址的驗證和剖析呈現。|  
|[CNetAddressCtrl::GetAllowType](#getallowtype)|擷取目前的網路位址控制項可支援的網路位址的型別。|  
|[CNetAddressCtrl::SetAllowType](#setallowtype)|設定目前的網路位址控制項可支援的網路位址的類型。|  
  
## <a name="remarks"></a>備註  
 網路位址控制項驗證使用者輸入的地址的格式正確。 控制項不會實際連線至網路位址。 [CNetAddressCtrl::SetAllowType](#setallowtype)方法會指定一或多個類型的地址， [CNetAddressCtrl::GetAddress](#getaddress)方法可以剖析和驗證。 位址可以是 IPv4、 IPv6、 或具名的伺服器、 網路、 主機或廣播的訊息目的地的地址的格式。 如果位址的格式不正確，您可以使用[CNetAddressCtrl::DisplayErrorTip](#displayerrortip)方法，以顯示資訊提示訊息方塊，以圖形方式指向網路位址控制項的文字方塊中，並顯示預先定義的錯誤訊息。  
  
 `CNetAddressCtrl`類別衍生自[CEdit](../../mfc/reference/cedit-class.md)類別。 因此，網路位址控制項提供存取所有 Windows 編輯控制項的訊息。  
  
 下圖說明包含網路位址控制項的對話方塊。 文字 方塊中 （1） 的網路位址控制項包含無效的網路位址。 如果網路位址不正確，就會顯示資訊提示訊息 (2)。  
  
 ![具有網路位址控制項和資訊提示的對話方塊。] (../../mfc/reference/media/cnetaddctrl.png "cnetaddctrl")  
  
## <a name="example"></a>範例  
 下列程式碼範例是驗證的網路位址 對話方塊的一部分。 三個選項按鈕的事件處理常式指定的網路位址可以是其中一種位址類型。 使用者在網路控制中，文字方塊中輸入的地址，然後按下按鈕，以驗證地址。 如果位址是有效的則會顯示成功訊息;否則，就會顯示預先定義的資訊提示錯誤訊息。  
  
 [!code-cpp[NVC_MFC_CNetAddressCtrl_s&#1;&1;](../../mfc/reference/codesnippet/cpp/cnetaddressctrl-class_1.cpp)]  
  
## <a name="example"></a>範例  
 下列程式碼範例從對話方塊標頭檔會定義[NC_ADDRESS](http://msdn.microsoft.com/library/windows/desktop/bb773345)和[NET_ADDRESS_INFO](http://msdn.microsoft.com/library/windows/desktop/bb773346)變數所需的[CNetAddressCtrl::GetAddress](#getaddress)方法。  
  
 [!code-cpp[NVC_MFC_CNetAddressCtrl_s&#1;&2;](../../mfc/reference/codesnippet/cpp/cnetaddressctrl-class_2.h)]  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CEdit](../../mfc/reference/cedit-class.md)  
  
 `CNetAddressCtrl`  
  
## <a name="requirements"></a>需求  
 **標頭：** afxcmn.h  
  
 這個類別支援[!INCLUDE[windowsver](../../build/reference/includes/windowsver_md.md)]和更新版本。  
  
 這個類別的其他需求所述[建置需求的 Windows Vista 通用控制項](../../mfc/build-requirements-for-windows-vista-common-controls.md)。  
  
##  <a name="cnetaddressctrl"></a>CNetAddressCtrl::CNetAddressCtrl  
 建構 `CNetAddressCtrl` 物件。  
  
```  
CNetAddressCtrl();
```  
  
### <a name="remarks"></a>備註  
 使用[CNetAddressCtrl::Create](#create)或[CNetAddressCtrl::CreateEx](#createex)方法來建立網路控制，並將其附加至`CNetAddressCtrl`物件。  
  
##  <a name="create"></a>CNetAddressCtrl::Create  
 使用指定的樣式建立網路位址控制項，並將其附加至目前`CNetAddressCtrl`物件。  
  
```  
virtual BOOL Create(
    DWORD dwStyle,   
    const RECT& rect,   
    CWnd* pParentWnd,   
    UINT nID);
```  
  
### <a name="parameters"></a>參數  
  
|參數|描述|  
|---------------|-----------------|  
|[in] `dwStyle`|若要套用至控制項的樣式的位元組合。 如需詳細資訊，請參閱[編輯樣式](../../mfc/reference/edit-styles.md)。|  
|[in] `rect`|參考[RECT](http://msdn.microsoft.com/library/windows/desktop/dd162897)結構，包含控制項的大小與位置。|  
|[in] `pParentWnd`|非 null 指標[CWnd](../../mfc/reference/cwnd-class.md)是控制項的父視窗的物件。|  
|[in] `nID`|控制項的 ID。|  
  
### <a name="return-value"></a>傳回值  
 如果此方法成功為 `true`；否則為 `false`。  
  
##  <a name="createex"></a>CNetAddressCtrl::CreateEx  
 使用指定的延伸樣式建立網路位址控制項，並將其附加至目前`CNetAddressCtrl`物件。  
  
```  
virtual BOOL CreateEx(
    DWORD dwExStyle,   
    DWORD dwStyle,   
    const RECT& rect,   
    CWnd* pParentWnd,   
    UINT nID);
```  
  
### <a name="parameters"></a>參數  
  
|參數|描述|  
|---------------|-----------------|  
|[in] `dwExStyle`|位元組合 (OR) 的延伸樣式套用至控制項。 如需詳細資訊，請參閱`dwExStyle`參數[CreateWindowEx](http://msdn.microsoft.com/library/windows/desktop/ms632680)函式。|  
|[in] `dwStyle`|位元組合 (OR) 的樣式套用至控制項。 如需詳細資訊，請參閱[編輯樣式](../../mfc/reference/edit-styles.md)。|  
|[in] `rect`|參考[RECT](http://msdn.microsoft.com/library/windows/desktop/dd162897)結構，包含控制項的大小與位置。|  
|[in] `pParentWnd`|非 null 指標[CWnd](../../mfc/reference/cwnd-class.md)是控制項的父視窗的物件。|  
|[in] `nID`|控制項的 ID。|  
  
### <a name="return-value"></a>傳回值  
 如果此方法成功為 `true`；否則為 `false`。  
  
##  <a name="displayerrortip"></a>CNetAddressCtrl::DisplayErrorTip  
 在目前的網路位址控制項相關聯的汽球提示中顯示錯誤訊息。  
  
```  
HRESULT DisplayErrorTip();
```  
  
### <a name="return-value"></a>傳回值  
 值`S_OK`如果此方法成功則為錯誤碼。  
  
### <a name="remarks"></a>備註  
 使用[CNetAddressCtrl::SetAllowType](#setallowtype)方法，以指定的位址可支援目前的網路位址控制項的類型。 使用[CNetAddressCtrl::GetAddress](#getaddress)方法來驗證和剖析使用者輸入的網路位址。 使用[CNetAddressCtrl::DisplayErrorTip](#displayerrortip)方法，以顯示錯誤訊息資訊提示，如果[CNetAddressCtrl::GetAddress](#getaddress)方法不成功。  
  
 此訊息會叫用[NetAddr_DisplayErrorTip](http://msdn.microsoft.com/library/windows/desktop/bb774314)巨集，這會在說明[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。 該巨集傳送`NCM_DISPLAYERRORTIP`訊息。  
  
##  <a name="getaddress"></a>CNetAddressCtrl::GetAddress  
 擷取目前的網路位址控制項相關聯的網路位址的驗證和剖析呈現。  
  
```  
HRESULT GetAddress(PNC_ADDRESS pAddress) const;  
```  
  
### <a name="parameters"></a>參數  
  
|參數|描述|  
|---------------|-----------------|  
|[in、out] `pAddress`|指標[NC_ADDRESS](http://msdn.microsoft.com/library/windows/desktop/bb773345)結構。  設定`pAddrInfo`這個位址的結構的成員[NET_ADDRESS_INFO](http://msdn.microsoft.com/library/windows/desktop/bb773346)結構才能呼叫 GetAddress 方法。|  
  
### <a name="return-value"></a>傳回值  
 值`S_OK`如果此方法成功，否則 COM 錯誤程式碼。 如需可能的錯誤代碼的詳細資訊，請參閱 > 一節會傳回值[NetAddr_GetAddress](http://msdn.microsoft.com/library/windows/desktop/bb774316)巨集。  
  
### <a name="remarks"></a>備註  
 如果此方法成功， [NET_ADDRESS_INFO](http://msdn.microsoft.com/library/windows/desktop/bb773346)結構包含的網路位址的其他資訊。  
  
 使用[CNetAddressCtrl::SetAllowType](#setallowtype)方法，以指定的位址可支援目前的網路位址控制項的類型。 使用[CNetAddressCtrl::GetAddress](#getaddress)方法來驗證和剖析使用者輸入的網路位址。 使用[CNetAddressCtrl::DisplayErrorTip](#displayerrortip)方法，以顯示錯誤訊息資訊提示，如果[CNetAddressCtrl::GetAddress](#getaddress)方法不成功。  
  
 這個方法會叫用[NetAddr_GetAddress](http://msdn.microsoft.com/library/windows/desktop/bb774316)巨集，這會在說明[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。 該巨集傳送`NCM_GETADDRESS`訊息。  
  
##  <a name="getallowtype"></a>CNetAddressCtrl::GetAllowType  
 擷取目前的網路位址控制項可支援的網路位址的型別。  
  
```  
DWORD GetAllowType() const;  
```  
  
### <a name="return-value"></a>傳回值  
 網路位址控制項可以支援的位元組合 (OR) 旗標，以指定的位址類型。 如需詳細資訊，請參閱[NET_STRING](http://msdn.microsoft.com/library/windows/desktop/bb762586)。  
  
### <a name="remarks"></a>備註  
 此訊息會叫用[NetAddr_GetAllowType](http://msdn.microsoft.com/library/windows/desktop/bb774318)巨集，這會在說明[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。 該巨集傳送`NCM_GETALLOWTYPE`訊息。  
  
##  <a name="setallowtype"></a>CNetAddressCtrl::SetAllowType  
 設定目前的網路位址控制項可支援的網路位址的類型。  
  
```  
HRESULT SetAllowType(DWORD dwAddrMask);
```  
  
### <a name="parameters"></a>參數  
  
|參數|描述|  
|---------------|-----------------|  
|[in] `dwAddrMask`|網路位址控制項可以支援的位元組合 (OR) 旗標，以指定的位址類型。 如需詳細資訊，請參閱[NET_STRING](http://msdn.microsoft.com/library/windows/desktop/bb762586)。|  
  
### <a name="return-value"></a>傳回值  
 `S_OK`如果此方法成功。否則，COM 錯誤程式碼。  
  
### <a name="remarks"></a>備註  
 使用[CNetAddressCtrl::SetAllowType](#setallowtype)方法，以指定的位址可支援目前的網路位址控制項的類型。 使用[CNetAddressCtrl::GetAddress](#getaddress)方法來驗證和剖析使用者輸入的網路位址。 使用[CNetAddressCtrl::DisplayErrorTip](#displayerrortip)方法，以顯示錯誤訊息資訊提示，如果[CNetAddressCtrl::GetAddress](#getaddress)方法不成功。  
  
 此訊息會叫用[NetAddr_SetAllowType](http://msdn.microsoft.com/library/windows/desktop/bb774320)巨集，這會在說明[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。 該巨集傳送`NCM_SETALLOWTYPE`訊息。  
  
## <a name="see-also"></a>另請參閱  
 [CNetAddressCtrl 類別](../../mfc/reference/cnetaddressctrl-class.md)   
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [CEdit 類別](../../mfc/reference/cedit-class.md)

