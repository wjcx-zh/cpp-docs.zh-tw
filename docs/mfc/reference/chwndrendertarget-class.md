---
title: "CHwndRenderTarget 類別 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CHwndRenderTarget"
  - "afxrendertarget/CHwndRenderTarget"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CHwndRenderTarget 類別"
ms.assetid: aa65b69f-7202-46ea-af81-ef325da0b840
caps.latest.revision: 17
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 19
---
# CHwndRenderTarget 類別
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

ID2D1HwndRenderTarget 的包裝函式。  
  
## 語法  
  
```  
class CHwndRenderTarget : public CRenderTarget;  
```  
  
## Members  
  
### 公用建構函式  
  
|名稱|描述|  
|--------|--------|  
|[CHwndRenderTarget::CHwndRenderTarget](../Topic/CHwndRenderTarget::CHwndRenderTarget.md)|從 HWND 建構 CHwndRenderTarget 物件。|  
  
### 公用方法  
  
|名稱|描述|  
|--------|--------|  
|[CHwndRenderTarget::Attach](../Topic/CHwndRenderTarget::Attach.md)|將現有的轉譯目標介面附加至物件|  
|[CHwndRenderTarget::CheckWindowState](../Topic/CHwndRenderTarget::CheckWindowState.md)|表示與此轉譯目標關聯的 HWND 是否為封閉的。|  
|[CHwndRenderTarget::Create](../Topic/CHwndRenderTarget::Create.md)|建立與視窗相關聯的轉譯目標|  
|[CHwndRenderTarget::Detach](../Topic/CHwndRenderTarget::Detach.md)|將轉譯目標介面與其物件中斷連結|  
|[CHwndRenderTarget::GetHwnd](../Topic/CHwndRenderTarget::GetHwnd.md)|傳回與這個轉譯目標相關聯的 HWND。|  
|[CHwndRenderTarget::GetHwndRenderTarget](../Topic/CHwndRenderTarget::GetHwndRenderTarget.md)|傳回 ID2D1HwndRenderTarget 介面。|  
|[CHwndRenderTarget::ReCreate](../Topic/CHwndRenderTarget::ReCreate.md)|重新建立與視窗相關聯的轉譯目標|  
|[CHwndRenderTarget::Resize](../Topic/CHwndRenderTarget::Resize.md)|將轉譯目標大小變更為指定的像素大小|  
  
### 公用運算子  
  
|名稱|描述|  
|--------|--------|  
|[CHwndRenderTarget::operator ID2D1HwndRenderTarget\*](../Topic/CHwndRenderTarget::operator%20ID2D1HwndRenderTarget*.md)|傳回 ID2D1HwndRenderTarget 介面。|  
  
### 受保護的資料成員  
  
|名稱|描述|  
|--------|--------|  
|[CHwndRenderTarget::m\_pHwndRenderTarget](../Topic/CHwndRenderTarget::m_pHwndRenderTarget.md)|ID2D1HwndRenderTarget 物件的指標。|  
  
## 繼承階層架構  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CRenderTarget](../../mfc/reference/crendertarget-class.md)  
  
 [CHwndRenderTarget](../../mfc/reference/chwndrendertarget-class.md)  
  
## 需求  
 **標頭檔：**afxrendertarget.h  
  
## 請參閱  
 [類別](../../mfc/reference/mfc-classes.md)