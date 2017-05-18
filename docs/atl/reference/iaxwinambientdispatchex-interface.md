---
title: "IAxWinAmbientDispatchEx 介面 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- IAxWinAmbientDispatchEx
- No header/ATL::IAxWinAmbientDispatchEx
- No header/ATL::SetAmbientDispatch
dev_langs:
- C++
helpviewer_keywords:
- IAxWinAmbientDispatchEx interface
ms.assetid: 2c25e079-6128-4278-bc72-b2c6195ba7ef
caps.latest.revision: 25
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
ms.openlocfilehash: 915514a021aa89b751a49a34cb53b693b9fd0c45
ms.contentlocale: zh-tw
ms.lasthandoff: 02/24/2017

---
# <a name="iaxwinambientdispatchex-interface"></a>IAxWinAmbientDispatchEx 介面
這個介面會實作補充環境裝載的控制項屬性。  
  
> [!IMPORTANT]
>  這個類別及其成員無法在 [!INCLUDE[wrt](../../atl/reference/includes/wrt_md.md)]中執行的應用程式內使用。  
  
## <a name="syntax"></a>語法  
  
```
MIDL_INTERFACE("B2D0778B - AC99 - 4c58 - A5C8 - E7724E5316B5") IAxWinAmbientDispatchEx : public IAxWinAmbientDispatch
```  
  
## <a name="members"></a>Members  
  
### <a name="methods"></a>方法  
  
|||  
|-|-|  
|[SetAmbientDispatch](#setambientdispatch)|呼叫這個方法是以補充預設環境屬性的介面與使用者定義的介面。|  
  
## <a name="remarks"></a>備註  
 靜態連結 ATL 及主控 ActiveX 控制項，尤其是具有環境屬性的 ActiveX 控制項的 ATL 應用程式中包含這個介面。 不包括此介面將會產生這個判斷提示: 「 您是否忘記將 LIBID CComModule::Init 」  
  
 這個介面是由 ATL 的 ActiveX 控制項裝載物件公開。 衍生自[IAxWinAmbientDispatch](../../atl/reference/iaxwinambientdispatch-interface.md)，`IAxWinAmbientDispatchEx`將可讓您增補 ATL 提供與您自己的環境屬性介面的方法。  
  
 [AXHost](https://msdn.microsoft.com/library/system.windows.forms.axhost.aspx)將會嘗試載入型別資訊有關`IAxWinAmbientDispatch`和`IAxWinAmbientDispatchEx`從類型程式庫包含程式碼。  
  
 如果您要連結至 ATL90.dll， **AXHost**會從類型程式庫 DLL 中載入的型別資訊。  
  
 請參閱[裝載 ActiveX 控制項使用 ATL 類別](../../atl/hosting-activex-controls-using-atl-axhost.md)如需詳細資訊。  
  
## <a name="requirements"></a>需求  
 此介面的定義有數種格式，如下表所示。  
  
|定義類型|檔案|  
|---------------------|----------|  
|IDL|atliface.idl|  
|類型程式庫|ATL.dll|  
|C++|atliface.h （也包含在 ATLBase.h）|  
  
##  <a name="setambientdispatch"></a>IAxWinAmbientDispatchEx::SetAmbientDispatch  
 呼叫這個方法是以補充預設環境屬性的介面與使用者定義的介面。  
  
```
virtual HRESULT STDMETHODCALLTYPE SetAmbientDispatch(IDispatch* pDispatch) = 0;
```  
  
### <a name="parameters"></a>參數  
 *pDispatch*  
 新的介面指標。  
  
### <a name="return-value"></a>傳回值  
 傳回 S_OK，如果成功或失敗的錯誤 HRESULT。  
  
### <a name="remarks"></a>備註  
 當`SetAmbientDispatch`稱為的新介面的指標，這個新介面將用來叫用任何屬性或方法，如果系統要求您針對裝載的控制項，這些屬性所未提供的[IAxWinAmbientDispatch](../../atl/reference/iaxwinambientdispatch-interface.md)。  
  
## <a name="see-also"></a>另請參閱  
 [IAxWinAmbientDispatch 介面](../../atl/reference/iaxwinambientdispatch-interface.md)

