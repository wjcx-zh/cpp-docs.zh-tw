---
title: "CMFCDynamicLayout 類別 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
dev_langs: 
  - "C++"
ms.assetid: c2df2976-f049-47fc-9cf0-abe3e01948bc
caps.latest.revision: 16
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 18
---
# CMFCDynamicLayout 類別
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

指定使用者調整視窗大小時，控制項在視窗中如何移動和調整大小。  
  
## 語法  
  
```  
class CMFCDynamicLayout : public CObject  
```  
  
## 成員  
  
### 公用建構函式  
  
|名稱|描述|  
|--------|--------|  
|`CMFCDynamicLayout::CMFCDynamicLayout`|建構 `CMFCDynamicLayout` 物件。|  
|`CMFCDynamicLayout::~CMFCDynamicLayout`|解構函式。|  
  
### 公用方法  
  
|名稱|描述|  
|--------|--------|  
|[CMFCDynamicLayout::AddItem](../Topic/CMFCDynamicLayout::AddItem.md)|將子視窗 \(通常是控制項\) 加入至動態配置管理員所控制的視窗清單。|  
|[CMFCDynamicLayout::Adjust](../Topic/CMFCDynamicLayout::Adjust.md)|將子視窗 \(通常是控制項\) 加入至動態配置管理員所控制的視窗清單。|  
|[CMFCDynamicLayout::Create](../Topic/CMFCDynamicLayout::Create.md)|儲存並驗證主控視窗。|  
|[CMFCDynamicLayout::GetHostWnd](../Topic/CMFCDynamicLayout::GetHostWnd.md)|傳回主控視窗的指標。|  
|[CMFCDynamicLayout::GetMinSize](../Topic/CMFCDynamicLayout::GetMinSize.md)|傳回視窗大小下限，低於此值就不調整版面配置。|  
|[CMFCDynamicLayout::GetWindowRect](../Topic/CMFCDynamicLayout::GetWindowRect.md)|擷取視窗的目前用戶端區域的週框。|  
|[CMFCDynamicLayout::HasItem](../Topic/CMFCDynamicLayout::HasItem.md)|檢查如果子控制項是否已加入動態配置。|  
|[CMFCDynamicLayout::IsEmpty](../Topic/CMFCDynamicLayout::IsEmpty.md)|檢查動態配置是否未加入任何子視窗。|  
|[CMFCDynamicLayout::LoadResource](../Topic/CMFCDynamicLayout::LoadResource.md)|從 AFX\_DIALOG\_LAYOUT 資源讀取動態配置，然後將配置套用至主控視窗。|  
|靜態 [CMFCDynamicLayout::MoveHorizontal](../Topic/CMFCDynamicLayout::MoveHorizontal.md)|取得 [MoveSettings](../Topic/CMFCDynamicLayout::MoveSettings%20Structure.md) 值，用來定義當使用者調整其裝載視窗的大小時，水平移動子控制項的幅度。|  
|靜態 [CMFCDynamicLayout::MoveHorizontalAndVertical](../Topic/CMFCDynamicLayout::MoveHorizontalAndVertical.md)|取得 [MoveSettings](../Topic/CMFCDynamicLayout::MoveSettings%20Structure.md) 值，用來定義當使用者調整其裝載視窗的大小時，水平移動子控制項的幅度。|  
|靜態 [CMFCDynamicLayout::MoveNone](../Topic/CMFCDynamicLayout::MoveNone.md)|取得代表子控制項沒有移動 \(垂直或水平\) 的 [MoveSettings](../Topic/CMFCDynamicLayout::MoveSettings%20Structure.md) 值。|  
|靜態 [CMFCDynamicLayout::MoveVertical](../Topic/CMFCDynamicLayout::MoveVertical.md)|取得 [MoveSettings](../Topic/CMFCDynamicLayout::MoveSettings%20Structure.md) 值，用來定義當使用者調整其裝載視窗的大小時，垂直移動子控制項的幅度。|  
|[CMFCDynamicLayout::SetMinSize](../Topic/CMFCDynamicLayout::SetMinSize.md)|設定視窗大小下限，低於此值就不調整版面配置。|  
|靜態 [CMFCDynamicLayout::SizeHorizontal](../Topic/CMFCDynamicLayout::SizeHorizontal.md)|取得 [SizeSettings](../Topic/CMFCDynamicLayout::SizeSettings%20Structure.md) 值，用來定義當使用者調整其裝載視窗的大小時，水平調整子控制項大小的幅度。|  
|靜態 [CMFCDynamicLayout::SizeHorizontalAndVertical](../Topic/CMFCDynamicLayout::SizeHorizontalAndVertical.md)|取得 [SizeSettings](../Topic/CMFCDynamicLayout::SizeSettings%20Structure.md) 值，用來定義當使用者調整其裝載視窗的大小時，水平調整子控制項大小的幅度。|  
|靜態 [CMFCDynamicLayout::SizeNone](../Topic/CMFCDynamicLayout::SizeNone.md)|取得 [SizeSettings](../Topic/CMFCDynamicLayout::SizeSettings%20Structure.md) 值，表示子控制項的大小沒有變更。|  
|靜態 [CMFCDynamicLayout::SizeVertical](../Topic/CMFCDynamicLayout::SizeVertical.md)|取得 [SizeSettings](../Topic/CMFCDynamicLayout::SizeSettings%20Structure.md) 值，定義當使用者調整其裝載視窗的大小時，垂直調整子控制項大小的幅度。|  
  
## 巢狀類型  
  
|名稱|描述|  
|--------|--------|  
|[CMFCDynamicLayout::MoveSettings 結構](../Topic/CMFCDynamicLayout::MoveSettings%20Structure.md)|為動態配置中控制項封裝移動資料。|  
|[CMFCDynamicLayout::SizeSettings 結構](../Topic/CMFCDynamicLayout::SizeSettings%20Structure.md)|為動態配置中的控制項封裝大小變更資料。|  
  
## 備註  
  
## 繼承階層  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CMFCDynamicLayout](../../mfc/reference/cmfctoolbarbutton-class.md)  
  
## 需求  
 **標頭：**afxlayout.h  
  
## 請參閱  
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [類別](../../mfc/reference/mfc-classes.md)