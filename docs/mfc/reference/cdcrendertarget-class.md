---
title: "CDCRenderTarget 類別 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "afxrendertarget/CDCRenderTarget"
  - "CDCRenderTarget"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CDCRenderTarget 類別"
ms.assetid: aa8059c9-08e6-49e4-9b8c-00fa54077a61
caps.latest.revision: 16
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CDCRenderTarget 類別
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

ID2D1DCRenderTarget 的包裝函式。  
  
## 語法  
  
```  
class CDCRenderTarget : public CRenderTarget;  
```  
  
## Members  
  
### 公用建構函式  
  
|名稱|描述|  
|--------|--------|  
|[CDCRenderTarget::CDCRenderTarget](../Topic/CDCRenderTarget::CDCRenderTarget.md)|建構 CDCRenderTarget 物件。|  
  
### 公用方法  
  
|名稱|描述|  
|--------|--------|  
|[CDCRenderTarget::Attach](../Topic/CDCRenderTarget::Attach.md)|將現有的轉譯目標介面附加至物件|  
|[CDCRenderTarget::BindDC](../Topic/CDCRenderTarget::BindDC.md)|將轉譯目標繫結至接受所發出繪圖命令的裝置內容|  
|[CDCRenderTarget::Create](../Topic/CDCRenderTarget::Create.md)|建立 CDCRenderTarget。|  
|[CDCRenderTarget::Detach](../Topic/CDCRenderTarget::Detach.md)|將轉譯目標介面與其物件中斷連結|  
|[CDCRenderTarget::GetDCRenderTarget](../Topic/CDCRenderTarget::GetDCRenderTarget.md)|傳回 ID2D1DCRenderTarget 介面|  
  
### 公用運算子  
  
|名稱|描述|  
|--------|--------|  
|[CDCRenderTarget::operator ID2D1DCRenderTarget\*](../Topic/CDCRenderTarget::operator%20ID2D1DCRenderTarget*.md)|傳回 ID2D1DCRenderTarget 介面|  
  
### 受保護的資料成員  
  
|名稱|描述|  
|--------|--------|  
|[CDCRenderTarget::m\_pDCRenderTarget](../Topic/CDCRenderTarget::m_pDCRenderTarget.md)|ID2D1DCRenderTarget 物件的指標。|  
  
## 繼承階層架構  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CRenderTarget](../../mfc/reference/crendertarget-class.md)  
  
 [CDCRenderTarget](../../mfc/reference/cdcrendertarget-class.md)  
  
## 需求  
 **標頭檔：**afxrendertarget.h  
  
## 請參閱  
 [類別](../../mfc/reference/mfc-classes.md)