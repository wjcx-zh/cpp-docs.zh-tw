---
title: "IDocHostUIHandlerDispatch Interface | Microsoft Docs"
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
  - "IDocHostUIHandlerDispatch"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "IDocHostUIHandlerDispatch interface"
ms.assetid: 6963a301-601a-4ac3-8bef-f7b252ea2fc6
caps.latest.revision: 22
caps.handback.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# IDocHostUIHandlerDispatch Interface
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

已解析和呈現引擎的 Microsoft HTML 的介面。  
  
> [!IMPORTANT]
>  這個類別和其成員不能用於 [!INCLUDE[wrt](../../atl/reference/includes/wrt_md.md)]執行的應用程式。  
  
## 語法  
  
```  
  
interface IDocHostUIHandlerDispatch : IDispatch  
  
```  
  
## Members  
  
### 公用方法  
  
> [!NOTE]
>  連結列於下表是 [IDocUIHostHandler](https://msdn.microsoft.com/en-us/library/aa753260.aspx) 介面成員的 INet SDK 參考主題。  `IDocHostUIHandlerDispatch` 具有與相同的功能 **IDocUIHostHandler**，具有該差異 `IDocHostUIHandlerDispatch` 分配介面 \(Dispinterface\)，而 **IDocUIHostHandler** 是自訂介面。  
  
|||  
|-|-|  
|[\<caps:sentence id\="tgt7" sentenceid\="bbafd0070a97938421603b1ef8409510" class\="tgtSentence"\>EnableModeless\<\/caps:sentence\>](https://msdn.microsoft.com/en-us/library/aa753253.aspx)|從呼叫 [IOleInPlaceActiveObject::EnableModeless](http://msdn.microsoft.com/library/windows/desktop/ms680115)的 MSHTML 實作。  也可稱為 MSHTML 何時顯示強制回應 \(Modal\) UI。|  
|[\<caps:sentence id\="tgt10" sentenceid\="2cfbfb70fe0af79263134b694d06311c" class\="tgtSentence"\>FilterDataObject\<\/caps:sentence\>](https://msdn.microsoft.com/en-us/library/aa753254.aspx)|由 MSHTML 呼叫主應用程式可讓主應用程式取代 MSHTML 的資料物件。|  
|[\<caps:sentence id\="tgt12" sentenceid\="715255e2d7f611c97308a373328e19a0" class\="tgtSentence"\>GetDropTarget\<\/caps:sentence\>](https://msdn.microsoft.com/en-us/library/aa753255.aspx)|呼叫 MSHTML，此時它是用來，置放目標可讓主應用程式提供替代的 [IDropTarget](http://msdn.microsoft.com/library/windows/desktop/ms679679)。|  
|[\<caps:sentence id\="tgt14" sentenceid\="5a51a8633a0d2036f843073d6f35a4af" class\="tgtSentence"\>GetExternal\<\/caps:sentence\>](https://msdn.microsoft.com/en-us/library/aa753256.aspx)|呼叫以取得 MSHTML 主機的 IDispatch 介面。|  
|[\<caps:sentence id\="tgt16" sentenceid\="ce27e0c2f7ebb0aaa2f9088818dc8347" class\="tgtSentence"\>GetHostInfo\<\/caps:sentence\>](https://msdn.microsoft.com/en-us/library/aa753257.aspx)|擷取 MSHTML 主應用程式的 UI 功能。|  
|[\<caps:sentence id\="tgt18" sentenceid\="693bd2149b17c4586cdc167e13e59f0a" class\="tgtSentence"\>GetOptionKeyPath\<\/caps:sentence\>](https://msdn.microsoft.com/en-us/library/aa753258.aspx)|傳回下一個 MSHTML 儲存使用者偏好設定的登錄機碼。|  
|[\<caps:sentence id\="tgt20" sentenceid\="7fce94585b477684cc21a38fe9ee288c" class\="tgtSentence"\>HideUI\<\/caps:sentence\>](https://msdn.microsoft.com/en-us/library/aa753259.aspx)|呼叫，以便將 MSHTML 移除它的功能表和工具列。|  
|[\<caps:sentence id\="tgt22" sentenceid\="359e4dcbd80b962decf88ef02d66fe14" class\="tgtSentence"\>OnDocWindowActivate\<\/caps:sentence\>](https://msdn.microsoft.com/en-us/library/aa753261.aspx)|從呼叫 [IOleInPlaceActiveObject::OnDocWindowActivate](http://msdn.microsoft.com/library/windows/desktop/ms687281)的 MSHTML 實作。|  
|[\<caps:sentence id\="tgt24" sentenceid\="8e472d7f3f3064d2ee6fdddd83002b86" class\="tgtSentence"\>OnFrameWindowActivate\<\/caps:sentence\>](https://msdn.microsoft.com/en-us/library/aa753262.aspx)|從呼叫 [IOleInPlaceActiveObject::OnFrameWindowActivate](http://msdn.microsoft.com/library/windows/desktop/ms683969)的 MSHTML 實作。|  
|[\<caps:sentence id\="tgt26" sentenceid\="3fd38deec5e9f4201074e886bfb178a5" class\="tgtSentence"\>ResizeBorder\<\/caps:sentence\>](https://msdn.microsoft.com/en-us/library/aa753263.aspx)|從呼叫 [IOleInPlaceActiveObject::ResizeBorder](http://msdn.microsoft.com/library/windows/desktop/ms680053)的 MSHTML 實作。|  
|[\<caps:sentence id\="tgt28" sentenceid\="2f382ba3de5494d18b20ccfa348f795e" class\="tgtSentence"\>ShowContextMenu\<\/caps:sentence\>](https://msdn.microsoft.com/en-us/library/aa753264.aspx)|從呼叫 MSHTML 顯示內容功能表。|  
|[\<caps:sentence id\="tgt30" sentenceid\="c6978c4c8ab30ae8380439da613bb63c" class\="tgtSentence"\>ShowUI\<\/caps:sentence\>](https://msdn.microsoft.com/en-us/library/aa753265.aspx)|可讓主應用程式取代 MSHTML 功能表和工具列。|  
|[\<caps:sentence id\="tgt32" sentenceid\="97bfd5aead25a2d9870b38da4b6745cd" class\="tgtSentence"\>TranslateAccelerator\<\/caps:sentence\>](https://msdn.microsoft.com/en-us/library/aa753266.aspx)|呼叫 MSHTML，當 [IOleInPlaceActiveObject::TranslateAccelerator](http://msdn.microsoft.com/library/windows/desktop/ms693360) 或 [IOleControlSite::TranslateAccelerator](http://msdn.microsoft.com/library/windows/desktop/ms693756) 呼叫。|  
|[\<caps:sentence id\="tgt34" sentenceid\="55c20a6fb6b05f6059d72b2854a7d7e2" class\="tgtSentence"\>TranslateUrl\<\/caps:sentence\>](https://msdn.microsoft.com/en-us/library/aa753267.aspx)|呼叫 MSHTML 為主應用程式提供機會修改要載入的 URL。|  
|[\<caps:sentence id\="tgt36" sentenceid\="8fdf7c2c3ebf5fa12ecc909279c951ff" class\="tgtSentence"\>UpdateUI\<\/caps:sentence\>](https://msdn.microsoft.com/en-us/library/aa753268.aspx)|告知主應用程式命令狀態已變更。|  
  
## 備註  
 可以取代功能表、工具列和內容功能表使用由 Microsoft HTML 剖析和呈現引擎 \(MSHTML\) 透過實作這個介面的主機。  
  
## 需求  
 這個介面的定義是以 IDL 或 C\+\+，如下所示。  
  
|定義型別|檔案|  
|----------|--------|  
|IDL|ATLIFace.idl|  
|C\+\+|ATLIFace.h \(也包含在 ATLBase.h\)|  
  
## 請參閱  
 [IDocUIHostHandler](https://msdn.microsoft.com/en-us/library/aa753260.aspx)