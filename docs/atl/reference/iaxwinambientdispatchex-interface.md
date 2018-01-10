---
title: "IAxWinAmbientDispatchEx 介面 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- IAxWinAmbientDispatchEx
- ATLIFACE/ATL::IAxWinAmbientDispatchEx
- ATLIFACE/ATL::SetAmbientDispatch
dev_langs: C++
helpviewer_keywords: IAxWinAmbientDispatchEx interface
ms.assetid: 2c25e079-6128-4278-bc72-b2c6195ba7ef
caps.latest.revision: "25"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 3fd212417a00335bfc02699cf5e38eeacc6451ad
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="iaxwinambientdispatchex-interface"></a>IAxWinAmbientDispatchEx 介面
這個介面會實作裝載控制項的補充環境屬性。  
  
> [!IMPORTANT]
>  這個類別及其成員不能在 Windows 執行階段中執行的應用程式。  
  
## <a name="syntax"></a>語法  
  
```
MIDL_INTERFACE("B2D0778B - AC99 - 4c58 - A5C8 - E7724E5316B5") IAxWinAmbientDispatchEx : public IAxWinAmbientDispatch
```  
  
## <a name="members"></a>成員  
  
### <a name="methods"></a>方法  
  
|||  
|-|-|  
|[SetAmbientDispatch](#setambientdispatch)|這個方法被呼叫來補充預設環境屬性的介面與使用者定義的介面。|  
  
## <a name="remarks"></a>備註  
 靜態連結至 ATL 和主機 ActiveX 控制項，特別是 ActiveX 控制項有環境屬性的 ATL 應用程式中包含這個介面。 不包括此介面將會產生這個判斷提示: 「 您是否忘記要傳遞到 Init LIBID"  
  
 這個介面是 ATL 的 ActiveX 控制項裝載物件所公開的。 衍生自[IAxWinAmbientDispatch](../../atl/reference/iaxwinambientdispatch-interface.md)，`IAxWinAmbientDispatchEx`將可讓您增補 ATL 提供與您自己的環境屬性介面的方法。  
  
 [AXHost](https://msdn.microsoft.com/library/system.windows.forms.axhost.aspx)會嘗試載入型別資訊有關`IAxWinAmbientDispatch`和`IAxWinAmbientDispatchEx`從類型程式庫所包含的程式碼。  
  
 如果您要連結至 ATL90.dll， **AXHost**會從類型程式庫 DLL 中載入的型別資訊。  
  
 請參閱[裝載 ActiveX 控制項使用 ATL AXHost](../../atl/hosting-activex-controls-using-atl-axhost.md)如需詳細資訊。  
  
## <a name="requirements"></a>需求  
 下表所示使用數種格式，此介面的定義。  
  
|定義類型|檔案|  
|---------------------|----------|  
|IDL|atliface.idl|  
|類型程式庫|ATL.dll|  
|C++|atliface.h （也包含在 ATLBase.h）|  
  
##  <a name="setambientdispatch"></a>IAxWinAmbientDispatchEx::SetAmbientDispatch  
 這個方法被呼叫來補充預設環境屬性的介面與使用者定義的介面。  
  
```
virtual HRESULT STDMETHODCALLTYPE SetAmbientDispatch(IDispatch* pDispatch) = 0;
```  
  
### <a name="parameters"></a>參數  
 *pDispatch*  
 新的介面指標。  
  
### <a name="return-value"></a>傳回值  
 傳回 S_OK，如果成功或失敗的錯誤 HRESULT。  
  
### <a name="remarks"></a>備註  
 當`SetAmbientDispatch`呼叫與新介面的指標，這個新介面將用來叫用任何屬性或方法，如果系統要求您針對裝載的控制項，這些屬性所未提供的[IAxWinAmbientDispatch](../../atl/reference/iaxwinambientdispatch-interface.md).  
  
## <a name="see-also"></a>請參閱  
 [IAxWinAmbientDispatch 介面](../../atl/reference/iaxwinambientdispatch-interface.md)
