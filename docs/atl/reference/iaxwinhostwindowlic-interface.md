---
title: "IAxWinHostWindowLic 介面 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- IAxWinHostWindowLic
- No header/ATL::IAxWinHostWindowLic
- No header/ATL::CreateControlLic
- No header/ATL::CreateControlLicEx
dev_langs:
- C++
helpviewer_keywords:
- IAxWinHostWindowLic interface
ms.assetid: 750f1520-6bce-428c-aca0-fccbe3f063c7
caps.latest.revision: 19
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
ms.sourcegitcommit: 050e7483670bd32f633660ba44491c8bb3fc462d
ms.openlocfilehash: 01ff8a7205418583606cbfdb1c028d7097501e00
ms.contentlocale: zh-tw
ms.lasthandoff: 02/24/2017

---
# <a name="iaxwinhostwindowlic-interface"></a>IAxWinHostWindowLic 介面
這個介面會提供管理已授權的控制項和其主應用程式物件的方法。  
  
## <a name="syntax"></a>語法  
  
```
interface IAxWinHostWindowLic : IAxWinHostWindow
```  
  
## <a name="members"></a>Members  
  
### <a name="methods"></a>方法  
  
|||  
|-|-|  
|[CreateControlLic](#createcontrollic)|建立授權的控制項，並將它附加至主應用程式物件。|  
|[CreateControlLicEx](#createcontrollicex)|建立授權的控制項、 將它連接至主機的物件，並選擇性地設定事件處理常式。|  
  
## <a name="remarks"></a>備註  
 `IAxWinHostWindowLic`繼承自[IAxWinHostWindow](../../atl/reference/iaxwinhostwindow-interface.md) ，並將支援的授權的控制項建立的方法。  
  
 請參閱[裝載 ActiveX 控制項使用 ATL 類別](../../atl/hosting-activex-controls-using-atl-axhost.md)範例中使用此介面的成員。  
  
## <a name="requirements"></a>需求  
 此介面的定義可做為 IDL 或 c + +，如下所示。  
  
|定義類型|檔案|  
|---------------------|----------|  
|IDL|ATLIFace.idl|  
|C++|ATLIFace.h （也包含在 ATLBase.h）|  
  
##  <a name="createcontrollic"></a>IAxWinHostWindowLic::CreateControlLic  
 建立授權的控制項、 將它初始化，以及裝載於所識別的視窗`hWnd`。  
  
```
STDMETHOD(CreateControlLic)(
    LPCOLESTR lpTricsData,
    HWND hWnd,
    IStream* pStream,
    BSTR bstrLic);
```  
  
### <a name="parameters"></a>參數  
 `bstrLic`  
 [in]包含控制項的授權金鑰 BSTR。  
  
### <a name="remarks"></a>備註  
 請參閱[IAxWinHostWindow::CreateControl](../../atl/reference/iaxwinhostwindow-interface.md#createcontrol)其餘參數和傳回值的說明。  
  
 呼叫這個方法就相當於呼叫[IAxWinHostWindowLic::CreateControlLicEx](#createcontrollicex)  
  
### <a name="example"></a>範例  
 請參閱[裝載 ActiveX 控制項使用 ATL 類別](../../atl/hosting-activex-controls-using-atl-axhost.md)如需使用範例`IAxWinHostWindowLic::CreateControlLic`。  
  
##  <a name="createcontrollicex"></a>IAxWinHostWindowLic::CreateControlLicEx  
 建立授權的 ActiveX 控制項、 將它初始化，以及裝載於指定的視窗，類似於[IAxWinHostWindow::CreateControl](../../atl/reference/iaxwinhostwindow-interface.md#createcontrol)。  
  
```
STDMETHOD(CreateControlLicEx)(
    LPCOLESTR lpszTricsData,
    HWND hWnd,
    IStream* pStream,
    IUnknown** ppUnk,
    REFIID riidAdvise,
    IUnknown* punkAdvise,
    BSTR bstrLic);
```  
  
### <a name="parameters"></a>參數  
 `bstrLic`  
 [in]包含控制項的授權金鑰 BSTR。  
  
### <a name="remarks"></a>備註  
 請參閱[IAxWinHostWindow::CreateControlEx](../../atl/reference/iaxwinhostwindow-interface.md#createcontrolex)其餘參數和傳回值的說明。  
  
### <a name="example"></a>範例  
 請參閱[裝載 ActiveX 控制項使用 ATL 類別](../../atl/hosting-activex-controls-using-atl-axhost.md)如需使用範例`IAxWinHostWindowLic::CreateControlLicEx`。










