---
title: "CLinkCtrl Class | Microsoft Docs"
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
  - "CLinkCtrl"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CLinkCtrl class"
  - "控制項 [MFC], 連結"
  - "連結 [C++], link control"
  - "SysLink control"
  - "Web 網頁, link control"
ms.assetid: d1cd876a-ecca-42db-8ac4-9cd327df0cd4
caps.latest.revision: 23
caps.handback.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CLinkCtrl Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

提供 Windows 通用控制項 SysLink 的功能。  
  
## 語法  
  
```  
class CLinkCtrl : public CWnd  
```  
  
## Members  
  
### 公用建構函式  
  
|名稱|描述|  
|--------|--------|  
|[CLinkCtrl::CLinkCtrl](../Topic/CLinkCtrl::CLinkCtrl.md)|建構 `CLinkCtrl` 物件。|  
  
### 公用方法  
  
|名稱|描述|  
|--------|--------|  
|[CLinkCtrl::Create](../Topic/CLinkCtrl::Create.md)|建立連結控制項並將其附加至 `CLinkCtrl` 物件。|  
|[CLinkCtrl::CreateEx](../Topic/CLinkCtrl::CreateEx.md)|建立延伸樣式的連結控制項並將其附加至 `CLinkCtrl` 物件。|  
|[CLinkCtrl::GetIdealHeight](../Topic/CLinkCtrl::GetIdealHeight.md)|擷取連結控制的理想高度。|  
|[CLinkCtrl::GetIdealSize](../Topic/CLinkCtrl::GetIdealSize.md)|根據這個連結的指定寬度計算連結文字的慣用高度目前連結控制項的。|  
|[CLinkCtrl::GetItem](../Topic/CLinkCtrl::GetItem.md)|擷取連結控制項目的狀態和屬性。|  
|[CLinkCtrl::GetItemID](../Topic/CLinkCtrl::GetItemID.md)|擷取連結控制項目的 ID。|  
|[CLinkCtrl::GetItemState](../Topic/CLinkCtrl::GetItemState.md)|擷取連結控制項目的狀態。|  
|[CLinkCtrl::GetItemUrl](../Topic/CLinkCtrl::GetItemUrl.md)|擷取連結控制項目表示的 URL。|  
|[CLinkCtrl::HitTest](../Topic/CLinkCtrl::HitTest.md)|判斷使用者是否按指定的連結。|  
|[CLinkCtrl::SetItem](../Topic/CLinkCtrl::SetItem.md)|設定 Link 控制項項目的狀態和屬性。|  
|[CLinkCtrl::SetItemID](../Topic/CLinkCtrl::SetItemID.md)|設定 Link 控制項項目的 ID。|  
|[CLinkCtrl::SetItemState](../Topic/CLinkCtrl::SetItemState.md)|設定 Link 控制項中項目的狀態。|  
|[CLinkCtrl::SetItemUrl](../Topic/CLinkCtrl::SetItemUrl.md)|設定連結控制項目表示的 URL。|  
  
## 備註  
 「連結控制」在視窗則提供便利的方式嵌入電子文件連結。  實際的控制項是呈現標記的文字並啟動適當的應用程式中的視窗，當使用者按一下一個內嵌連結時。  多個連結在一個控制項之間的支援，並且可供以零起始的索引來存取。  
  
 這個控制項 \(也 `CLinkCtrl` 類別\) 至 Windows XP 下的程式才能使用 \(含\) 以後版本上執行。  
  
 如需詳細資訊，請參閱 [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]的 [SysLink 控制項](http://msdn.microsoft.com/library/windows/desktop/bb760706) 。  
  
## 繼承階層架構  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 `CLinkCtrl`  
  
## 需求  
 **Header:** afxcmn.h  
  
## 請參閱  
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [CWnd 類別](../../mfc/reference/cwnd-class.md)