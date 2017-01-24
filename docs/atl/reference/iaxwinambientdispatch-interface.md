---
title: "IAxWinAmbientDispatch Interface | Microsoft Docs"
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
  - "IAxWinAmbientDispatch"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "IAxWinAmbientDispatch interface"
ms.assetid: 55ba6f7b-7a3c-4792-ae47-c8a84b683ca9
caps.latest.revision: 24
caps.handback.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# IAxWinAmbientDispatch Interface
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

這個介面會提供所裝載的控制項或容器的特性的方法。  
  
> [!IMPORTANT]
>  這個類別和其成員不能用於 [!INCLUDE[wrt](../../atl/reference/includes/wrt_md.md)]執行的應用程式。  
  
## 語法  
  
```  
  
interface IAxWinAmbientDispatch : IDispatch  
  
```  
  
## Members  
  
### 方法  
  
|||  
|-|-|  
|[get\_AllowContextMenu](../Topic/IAxWinAmbientDispatch::get_AllowContextMenu.md)|**AllowContextMenu** 屬性所裝載的控制項是否允許顯示其內容功能表。|  
|[get\_AllowShowUI](../Topic/IAxWinAmbientDispatch::get_AllowShowUI.md)|**AllowShowUI** 屬性所裝載的控制項是否允許顯示其使用者介面。|  
|[get\_AllowWindowlessActivation](../Topic/IAxWinAmbientDispatch::get_AllowWindowlessActivation.md)|**AllowWindowlessActivation** 屬性指定容器是否允許無視窗啟動。|  
|[get\_BackColor](../Topic/IAxWinAmbientDispatch::get_BackColor.md)|`BackColor` 屬性指定容器的環境背景色彩。|  
|[get\_DisplayAsDefault](../Topic/IAxWinAmbientDispatch::get_DisplayAsDefault.md)|**DisplayAsDefault** 是允許控制項尋找的環境屬性 \(Ambient Property\)，如果它是預設控制項。|  
|[get\_DocHostDoubleClickFlags](../Topic/IAxWinAmbientDispatch::get_DocHostDoubleClickFlags.md)|**DocHostDoubleClickFlags** 屬性指定應該是為了回應按兩下作業。|  
|[get\_DocHostFlags](../Topic/IAxWinAmbientDispatch::get_DocHostFlags.md)|**DocHostFlags** 屬性指定主物件的使用者介面功能。|  
|[get\_Font](../Topic/IAxWinAmbientDispatch::get_Font.md)|**字型** 屬性指定容器的環境字型。|  
|[get\_ForeColor](../Topic/IAxWinAmbientDispatch::get_ForeColor.md)|`ForeColor` 屬性指定容器的前景色彩。|  
|[get\_LocaleID](../Topic/IAxWinAmbientDispatch::get_LocaleID.md)|**LocaleID** 屬性指定容器的地區設定 ID。|  
|[get\_MessageReflect](../Topic/IAxWinAmbientDispatch::get_MessageReflect.md)|**MessageReflect** 環境屬性指定容器是否會反映訊息傳送至裝載的控制項。|  
|[get\_OptionKeyPath](../Topic/IAxWinAmbientDispatch::get_OptionKeyPath.md)|**OptionKeyPath** 屬性指定登錄機碼路徑做為使用者設定。|  
|[get\_ShowGrabHandles](../Topic/IAxWinAmbientDispatch::get_ShowGrabHandles.md)|如果應該繪製其本身具有抓取控點， **ShowGrabHandles** 環境屬性允許控制項時出現。|  
|[get\_ShowHatching](../Topic/IAxWinAmbientDispatch::get_ShowHatching.md)|如果應該繪製其本身孵化後， **ShowHatching** 環境屬性允許控制項時出現。|  
|[get\_UserMode](../Topic/IAxWinAmbientDispatch::get_UserMode.md)|**UserMode** 屬性指定容器的使用者模式。|  
|[put\_AllowContextMenu](../Topic/IAxWinAmbientDispatch::put_AllowContextMenu.md)|**AllowContextMenu** 屬性所裝載的控制項是否允許顯示其內容功能表。|  
|[put\_AllowShowUI](../Topic/IAxWinAmbientDispatch::put_AllowShowUI.md)|**AllowShowUI** 屬性所裝載的控制項是否允許顯示其使用者介面。|  
|[put\_AllowWindowlessActivation](../Topic/IAxWinAmbientDispatch::put_AllowWindowlessActivation.md)|**AllowWindowlessActivation** 屬性指定容器是否允許無視窗啟動。|  
|[put\_BackColor](../Topic/IAxWinAmbientDispatch::put_BackColor.md)|`BackColor` 屬性指定容器的環境背景色彩。|  
|[put\_DisplayAsDefault](../Topic/IAxWinAmbientDispatch::put_DisplayAsDefault.md)|**DisplayAsDefault** 是允許控制項尋找的環境屬性 \(Ambient Property\)，如果它是預設控制項。|  
|[put\_DocHostDoubleClickFlags](../Topic/IAxWinAmbientDispatch::put_DocHostDoubleClickFlags.md)|**DocHostDoubleClickFlags** 屬性指定應該是為了回應按兩下作業。|  
|[put\_DocHostFlags](../Topic/IAxWinAmbientDispatch::put_DocHostFlags.md)|**DocHostFlags** 屬性指定主物件的使用者介面功能。|  
|[put\_Font](../Topic/IAxWinAmbientDispatch::put_Font.md)|**字型** 屬性指定容器的環境字型。|  
|[put\_ForeColor](../Topic/IAxWinAmbientDispatch::put_ForeColor.md)|`ForeColor` 屬性指定容器的前景色彩。|  
|[put\_LocaleID](../Topic/IAxWinAmbientDispatch::put_LocaleID.md)|**LocaleID** 屬性指定容器的地區設定 ID。|  
|[put\_MessageReflect](../Topic/IAxWinAmbientDispatch::put_MessageReflect.md)|**MessageReflect** 環境屬性指定容器是否會反映訊息傳送至裝載的控制項。|  
|[put\_OptionKeyPath](../Topic/IAxWinAmbientDispatch::put_OptionKeyPath.md)|**OptionKeyPath** 屬性指定登錄機碼路徑做為使用者設定。|  
|[put\_UserMode](../Topic/IAxWinAmbientDispatch::put_UserMode.md)|**UserMode** 屬性指定容器的使用者模式。|  
  
## 備註  
 這個介面是由裝載物件的 ATL 的 ActiveX 控制項公開 \(Expose\)。  呼叫的方法以設定環境屬性適用於裝載的控制項或指定容器的行為的其他方面。  若要補充屬性。 `IAxWinAmbientDispatch`提供，使用 [IAxWinAmbientDispatchEx](../../atl/reference/iaxwinambientdispatchex-interface.md)。  
  
 [AXHost](https://msdn.microsoft.com/en-us/library/system.windows.forms.axhost.aspx) 會嘗試從包含程式碼的 typelib 載入有關 `IAxWinAmbientDispatch` 和 `IAxWinAmbientDispatchEx` 的型別資訊。  
  
 如果您有 ATL90.dll 連接，從 **AXHost** typelib 會載入型別資訊在 DLL。  
  
 如需的詳細資訊請參閱 [載入使用 ATL AXHost 的 ActiveX 控制項](../../atl/hosting-activex-controls-using-atl-axhost.md) 。  
  
## 需求  
 這個介面的定義可用的一些表單中，如下表所示。  
  
|定義型別|檔案|  
|----------|--------|  
|IDL|atliface.idl|  
|型別程式庫|ATL.dll|  
|C\+\+|atliface.h \(也包含在 ATLBase.h\)|  
  
## 請參閱  
 [IAxWinAmbientDispatchEx Interface](../../atl/reference/iaxwinambientdispatchex-interface.md)   
 [IAxWinHostWindow Interface](../../atl/reference/iaxwinhostwindow-interface.md)   
 [CAxWindow::QueryHost](../Topic/CAxWindow::QueryHost.md)   
 [AtlAxGetHost](../Topic/AtlAxGetHost.md)