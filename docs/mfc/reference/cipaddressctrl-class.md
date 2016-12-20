---
title: "CIPAddressCtrl Class | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CIPAddressCtrl"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CIPAddressCtrl class"
  - "通用控制項, Internet Explorer 4.0"
  - "Internet address edit box"
  - "Internet Explorer 4.0 common controls"
  - "Internet protocol address box"
  - "IP address control"
ms.assetid: 9764d2f4-cb14-4ba8-b799-7f57a55a47c6
caps.latest.revision: 22
caps.handback.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CIPAddressCtrl Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

提供 Windows 通用 IP 位址控制項的功能。  
  
## 語法  
  
```  
class CIPAddressCtrl : public CWnd  
```  
  
## Members  
  
### 公用建構函式  
  
|名稱|描述|  
|--------|--------|  
|[CIPAddressCtrl::CIPAddressCtrl](../Topic/CIPAddressCtrl::CIPAddressCtrl.md)|建構 `CIPAddressCtrl` 物件。|  
  
### 公用方法  
  
|名稱|描述|  
|--------|--------|  
|[CIPAddressCtrl::ClearAddress](../Topic/CIPAddressCtrl::ClearAddress.md)|清除的內容 IP 位址控制項。|  
|[CIPAddressCtrl::Create](../Topic/CIPAddressCtrl::Create.md)|建立 IP 位址控制項並將其附加至 `CIPAddressCtrl` 物件。|  
|[CIPAddressCtrl::CreateEx](../Topic/CIPAddressCtrl::CreateEx.md)|建立具有指定之視窗的延伸樣式的 IP 位址控制項並將其附加至 `CIPAddressCtrl` 物件。|  
|[CIPAddressCtrl::GetAddress](../Topic/CIPAddressCtrl::GetAddress.md)|擷取所有四個欄位位址值 IP 位址控制項的。|  
|[CIPAddressCtrl::IsBlank](../Topic/CIPAddressCtrl::IsBlank.md)|判斷 IP 位址控制項中的所有欄位是否為空的。|  
|[CIPAddressCtrl::SetAddress](../Topic/CIPAddressCtrl::SetAddress.md)|將所有四個欄位位址值 IP 位址控制項的。|  
|[CIPAddressCtrl::SetFieldFocus](../Topic/CIPAddressCtrl::SetFieldFocus.md)|設定鍵盤焦點至 IP 位址控制項中指定的欄位。|  
|[CIPAddressCtrl::SetFieldRange](../Topic/CIPAddressCtrl::SetFieldRange.md)|在 IP 位址控制項中指定的欄位設定範圍。|  
  
## 備註  
 IP 位址控制項類似控制項，以編輯控制項，可讓您輸入及管理 Internet Protocol \(IP\) 格式的數字位址。  
  
 這個控制項 \(也 `CIPAddressCtrl` 類別\) 給在 Microsoft Internet Explorer 4.0 的管理員程式才能使用 \(含\) 以後版本。  它們也可以在  視窗和 Windows NT 下未來版本。  
  
 如需 IP 位址控制項的詳細資訊，請參閱 [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)][IP 位址控制項](http://msdn.microsoft.com/library/windows/desktop/bb761372) 。  
  
## 繼承階層架構  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 `CIPAddressCtrl`  
  
## 需求  
 **Header:** afxcmn.h  
  
## 請參閱  
 [CWnd 類別](../../mfc/reference/cwnd-class.md)   
 [階層架構圖表](../../mfc/hierarchy-chart.md)