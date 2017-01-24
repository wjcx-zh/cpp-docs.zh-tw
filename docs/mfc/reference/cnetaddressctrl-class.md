---
title: "CNetAddressCtrl 類別 | Microsoft Docs"
ms.custom: ""
ms.date: "12/09/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CNetAddressCtrl 類別"
ms.assetid: cb4c6aca-3f49-4b52-b76c-65f57096155b
caps.latest.revision: 32
caps.handback.revision: 20
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CNetAddressCtrl 類別
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

`CNetAddressCtrl` 類別表示網路位址控制項，您可以使用輸入和驗證 IPv4 和 IPv6、名為 DNS 位址格式。  
  
## 語法  
  
```  
class CNetAddressCtrl : public CEdit  
```  
  
## 成員  
  
### 公用建構函式  
  
|名稱|描述|  
|--------|--------|  
|[CNetAddressCtrl::CNetAddressCtrl](../Topic/CNetAddressCtrl::CNetAddressCtrl.md)|建構 `CNetAddressCtrl` 物件。|  
  
### 公用方法  
  
|名稱|描述|  
|--------|--------|  
|[CNetAddressCtrl::Create](../Topic/CNetAddressCtrl::Create.md)|建立具有指定樣式的網路位址控制項並將其附加至目前 `CNetAddressCtrl` 物件。|  
|[CNetAddressCtrl::CreateEx](../Topic/CNetAddressCtrl::CreateEx.md)|會使用指定的延伸樣式的網路位址控制項並將其附加至目前 `CNetAddressCtrl` 物件。|  
|[CNetAddressCtrl::DisplayErrorTip](../Topic/CNetAddressCtrl::DisplayErrorTip.md)|當使用者輸入在目前網路位址控制項時，中不支援的網路位址顯示錯誤汽球提示。|  
|[CNetAddressCtrl::GetAddress](../Topic/CNetAddressCtrl::GetAddress.md)|擷取網路位址的已驗證和剖析表示與目前網路位址控制項。|  
|[CNetAddressCtrl::GetAllowType](../Topic/CNetAddressCtrl::GetAllowType.md)|擷取目前網路位址控制項可以支援網路位址的類型。|  
|[CNetAddressCtrl::SetAllowType](../Topic/CNetAddressCtrl::SetAllowType.md)|設定目前網路位址控制項可以支援網路位址的類型。|  
  
## 備註  
 網路位址控制項來驗證使用者輸入位址的格式不正確。  控制項實際上沒有連接至網路位址。  [CNetAddressCtrl::SetAllowType](../Topic/CNetAddressCtrl::SetAllowType.md) 方法指定 [CNetAddressCtrl::GetAddress](../Topic/CNetAddressCtrl::GetAddress.md) 方法可以剖析及驗證位址的一個或多個型別。  以 IPv4 或 IPv6、名為位址的形式伺服器、網路、主機或廣播訊息的目的端位址，可以是。  如果位址的格式不正確，您可以使用 [CNetAddressCtrl::DisplayErrorTip](../Topic/CNetAddressCtrl::DisplayErrorTip.md) 方法顯示圖形、網路位址控制項文字方塊並顯示一個預先定義之錯誤訊息的資訊訊息方塊提示。  
  
 `CNetAddressCtrl` 類別 [CEdit](../../mfc/reference/cedit-class.md) 從類別衍生。  因此，網路位址控制項可用來存取所有視窗編輯控制項訊息。  
  
 下圖說明包含網路位址控制項的對話方塊。  網路位址控制項的文字方塊 \(1\) 包含無效的位址。  如果網址無效，資訊提示訊息 \(2\) 隨即顯示。  
  
 ![具有網路位址控制項和資訊提示的對話方塊](../../mfc/reference/media/cnetaddctrl.png "CNetAddCtrl")  
  
## 範例  
 下列程式碼範例會驗證網路位址對話方塊的區段。  三個選項按鈕的事件處理常式指定位址可以是三個位址型別之一。  使用者可以在 Web 控制項的文字方塊的位址，然後按  按鈕會驗證這個位址。  如果位址有效，成功訊息的顯示，否則，預先定義的資訊提示會顯示錯誤訊息。  
  
 [!code-cpp[NVC_MFC_CNetAddressCtrl_s1#1](../../mfc/reference/codesnippet/CPP/cnetaddressctrl-class_1.cpp)]  
  
## 範例  
 下列程式碼範例會從對話方塊標頭檔會定義 [CNetAddressCtrl::GetAddress](../Topic/CNetAddressCtrl::GetAddress.md) 方法所需的 [NC\_ADDRESS](http://msdn.microsoft.com/library/windows/desktop/bb773345) 和 [NET\_ADDRESS\_INFO](http://msdn.microsoft.com/library/windows/desktop/bb773346) 變數。  
  
 [!code-cpp[NVC_MFC_CNetAddressCtrl_s1#2](../../mfc/reference/codesnippet/CPP/cnetaddressctrl-class_2.h)]  
  
## 繼承階層架構  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CEdit](../../mfc/reference/cedit-class.md)  
  
 `CNetAddressCtrl`  
  
## 需求  
 **標題:** afxcmn.h  
  
 這個類別會在 [!INCLUDE[windowsver](../../build/reference/includes/windowsver_md.md)] \(含\) 以後版本支援。  
  
 這個類別還需要在 [Windows Vista 通用控制項的組建需求](../../mfc/build-requirements-for-windows-vista-common-controls.md)說明。  
  
## 請參閱  
 [CNetAddressCtrl Class](../../mfc/reference/cnetaddressctrl-class.md)   
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [CEdit Class](../../mfc/reference/cedit-class.md)