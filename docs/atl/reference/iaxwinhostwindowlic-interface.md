---
title: IAxWinHostWindowLic 介面 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- IAxWinHostWindowLic
- ATLIFACE/ATL::IAxWinHostWindowLic
- ATLIFACE/ATL::CreateControlLic
- ATLIFACE/ATL::CreateControlLicEx
dev_langs:
- C++
helpviewer_keywords:
- IAxWinHostWindowLic interface
ms.assetid: 750f1520-6bce-428c-aca0-fccbe3f063c7
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 41b4d7891d1bb00f4ee689477d1056dbf2bf28cf
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
ms.locfileid: "32362836"
---
# <a name="iaxwinhostwindowlic-interface"></a>IAxWinHostWindowLic 介面
這個介面會提供管理授權的控制項和其主機物件的方法。  
  
## <a name="syntax"></a>語法  
  
```
interface IAxWinHostWindowLic : IAxWinHostWindow
```  
  
## <a name="members"></a>成員  
  
### <a name="methods"></a>方法  
  
|||  
|-|-|  
|[CreateControlLic](#createcontrollic)|建立授權的控制項，並將其附加到主機的物件。|  
|[CreateControlLicEx](#createcontrollicex)|建立授權的控制項，將其附加至主機物件，並且選擇性地設定事件處理常式。|  
  
## <a name="remarks"></a>備註  
 `IAxWinHostWindowLic` 繼承自[IAxWinHostWindow](../../atl/reference/iaxwinhostwindow-interface.md) ，並將支援的授權控制項建立的方法。  
  
 請參閱[裝載 ActiveX 控制項使用 ATL AXHost](../../atl/hosting-activex-controls-using-atl-axhost.md)的範例會使用此介面的成員。  
  
## <a name="requirements"></a>需求  
 此介面的定義可做為 IDL 或 c + +，如下所示。  
  
|定義類型|檔案|  
|---------------------|----------|  
|IDL|ATLIFace.idl|  
|C++|ATLIFace.h （也包含在 ATLBase.h）|  
  
##  <a name="createcontrollic"></a>  IAxWinHostWindowLic::CreateControlLic  
 建立授權的控制項、 初始化，然後將它裝載於視窗所識別`hWnd`。  
  
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
 請參閱[IAxWinHostWindow::CreateControl](../../atl/reference/iaxwinhostwindow-interface.md#createcontrol)其餘的參數和傳回值的說明。  
  
 呼叫這個方法相當於呼叫[IAxWinHostWindowLic::CreateControlLicEx](#createcontrollicex)  
  
### <a name="example"></a>範例  
 請參閱[裝載 ActiveX 控制項使用 ATL AXHost](../../atl/hosting-activex-controls-using-atl-axhost.md)如使用的範例`IAxWinHostWindowLic::CreateControlLic`。  
  
##  <a name="createcontrollicex"></a>  IAxWinHostWindowLic::CreateControlLicEx  
 建立授權的 ActiveX 控制項、 初始化，然後將它裝載於指定的視窗，類似於[IAxWinHostWindow::CreateControl](../../atl/reference/iaxwinhostwindow-interface.md#createcontrol)。  
  
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
 請參閱[IAxWinHostWindow::CreateControlEx](../../atl/reference/iaxwinhostwindow-interface.md#createcontrolex)其餘的參數和傳回值的說明。  
  
### <a name="example"></a>範例  
 請參閱[裝載 ActiveX 控制項使用 ATL AXHost](../../atl/hosting-activex-controls-using-atl-axhost.md)如使用的範例`IAxWinHostWindowLic::CreateControlLicEx`。









