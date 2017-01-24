---
title: "IAxWinAmbientDispatchEx Interface | Microsoft Docs"
ms.custom: ""
ms.date: "12/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "ATL.IAxWinAmbientDispatchEx"
  - "IAxWinAmbientDispatchEx"
  - "ATL::IAxWinAmbientDispatchEx"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "IAxWinAmbientDispatchEx interface"
ms.assetid: 2c25e079-6128-4278-bc72-b2c6195ba7ef
caps.latest.revision: 25
caps.handback.revision: 12
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# IAxWinAmbientDispatchEx Interface
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

這個介面會實作裝載控制項之補充環境屬性。  
  
> [!IMPORTANT]
>  這個類別和其成員不能用於 [!INCLUDE[wrt](../../atl/reference/includes/wrt_md.md)]執行的應用程式。  
  
## 語法  
  
```  
  
      MIDL_INTERFACE( "B2D0778B - AC99 - 4c58 - A5C8 - E7724E5316B5" )  
IAxWinAmbientDispatchEx : public IAxWinAmbientDispatch  
```  
  
## Members  
  
### 方法  
  
|||  
|-|-|  
|[SetAmbientDispatch](../Topic/IAxWinAmbientDispatchEx::SetAmbientDispatch.md)|呼叫這個方法搭配具有使用者定義之介面的預設環境屬性的介面。|  
  
## 備註  
 包含這個介面會使用 ATL 靜態連結並裝載 ActiveX 控制項的 ATL 應用程式，有環境屬性特別的 ActiveX 控制項。  不包含這個介面會產生這個判斷提示:「忘記傳遞至 LIBID CComModule::Init?」  
  
 這個介面是由裝載物件的 ATL 的 ActiveX 控制項公開 \(Expose\)。  從 [IAxWinAmbientDispatch](../../atl/reference/iaxwinambientdispatch-interface.md)衍生， `IAxWinAmbientDispatchEx` 加入允許您新增至 ATL 提供的環境屬性介面與個人的方法。  
  
 [AXHost](https://msdn.microsoft.com/en-us/library/system.windows.forms.axhost.aspx) 會嘗試從包含程式碼的型別程式庫載入有關 `IAxWinAmbientDispatch` 和 `IAxWinAmbientDispatchEx` 的型別資訊。  
  
 如果您有 ATL90.dll 連接， **AXHost** 從型別程式庫會載入型別資訊在 DLL。  
  
 如需的詳細資訊請參閱 [載入使用 ATL AXHost 的 ActiveX 控制項](../../atl/hosting-activex-controls-using-atl-axhost.md) 。  
  
## 需求  
 這個介面的定義可用的一些表單中，如下表所示。  
  
|定義型別|檔案|  
|----------|--------|  
|IDL|atliface.idl|  
|型別程式庫|ATL.dll|  
|C\+\+|atliface.h \(也包含在 ATLBase.h\)|  
  
## 請參閱  
 [IAxWinAmbientDispatch Interface](../../atl/reference/iaxwinambientdispatch-interface.md)