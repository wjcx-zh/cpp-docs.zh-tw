---
title: "CAxWindow2T Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "ATL::CAxWindow2T<TBase>"
  - "ATL::CAxWindow2T"
  - "CAxWindow2T"
  - "ATL.CAxWindow2T<TBase>"
  - "ATL.CAxWindow2T"
  - "CAxWindow2"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CAxWindow2 class"
ms.assetid: b87bc943-7991-4537-b902-2138d7f4d837
caps.latest.revision: 22
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 25
---
# CAxWindow2T Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

這個類別會提供管理裝載 ActiveX 控制項的視窗提供方法，因此不支援裝載已授權的 ActiveX 控制項。  
  
> [!IMPORTANT]
>  這個類別和其成員不能用於 Windows 執行階段執行的應用程式。  
  
## 語法  
  
```  
  
      template <   
class TBase= CWindow   
>  
class CAxWindow2T :   
public CAxWindowT< TBase >  
```  
  
#### 參數  
 *TBase*  
 `CAxWindowT` 衍生自類別的類別。  
  
## Members  
  
### 公用建構函式  
  
|名稱|描述|  
|--------|--------|  
|[CAxWindow2T::CAxWindow2T](../Topic/CAxWindow2T::CAxWindow2T.md)|建構 `CAxWindow2T` 物件。|  
  
### 公用方法  
  
|名稱|描述|  
|--------|--------|  
|[CAxWindow2T::Create](../Topic/CAxWindow2T::Create.md)|建立裝載視窗。|  
|[CAxWindow2T::CreateControlLic](../Topic/CAxWindow2T::CreateControlLic.md)|建立已授權的 ActiveX 控制項，將它初始化，並將它裝載在指定的視窗。|  
|[CAxWindow2T::CreateControlLicEx](../Topic/CAxWindow2T::CreateControlLicEx.md)|建立已授權的 ActiveX 控制項，將它初始化，將它裝載在指定的視窗，並從控制項擷取介面指標 \(或指標\)。|  
|[CAxWindow2T::GetWndClassName](../Topic/CAxWindow2T::GetWndClassName.md)|擷取的視窗類別名稱的靜態方法。|  
  
### 公用運算子  
  
|名稱|描述|  
|--------|--------|  
|[CAxWindow2T::operator \=](../Topic/CAxWindow2T::operator%20=.md)|`HWND` 指派至現有的 `CAxWindow2T` 物件。|  
  
## 備註  
 `CAxWindow2T` 提供管理裝載 ActiveX 控制項的視窗的方法。  `CAxWindow2T` 同時也支援裝載已授權的 ActiveX 控制項。  「**AtlAxWinLic80**」提供載入，以 `CAxWindow2T`包裝。  
  
 類別 `CAxWindow2` 實作為 `CAxWindow2T` 類別的特製化。  此特製化宣告如下所示:  
  
 `typedef CAxWindow2T <CWindow> CAxWindow2;`  
  
> [!NOTE]
>  `CAxWindowT` 成員記載 [CAxWindow](../../atl/reference/caxwindow-class.md)之下。  
  
 對於此類別之成員的範例參閱 [載入使用 ATL AXHost 的 ActiveX 控制項](../../atl/hosting-activex-controls-using-atl-axhost.md) 。  
  
## 繼承階層架構  
 `TBase`  
  
 `CAxWindowT`  
  
 `CAxWindow2T`  
  
## 需求  
 **Header:** atlwin.h  
  
## 請參閱  
 [Class Overview](../../atl/atl-class-overview.md)   
 [控制項內含項目常見問題集](../../atl/atl-control-containment-faq.md)