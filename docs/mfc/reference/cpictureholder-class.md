---
title: "CPictureHolder Class | Microsoft Docs"
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
  - "Picture"
  - "CPictureHolder"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "控制項 [MFC], OLE"
  - "CPictureHolder class"
  - "OLE 控制項, 影像"
  - "Picture property"
ms.assetid: a4f59775-704a-41dd-b5bd-2e531c95127a
caps.latest.revision: 20
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CPictureHolder Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

實作圖片屬性，可讓使用者顯示在控制項中的圖片。  
  
## 語法  
  
```  
class CPictureHolder  
```  
  
## 成員  
  
### 公用建構函式  
  
|名稱|描述|  
|--------|--------|  
|[CPictureHolder::CPictureHolder](../Topic/CPictureHolder::CPictureHolder.md)|建構 `CPictureHolder` 物件。|  
  
### 公用方法  
  
|名稱|描述|  
|--------|--------|  
|[CPictureHolder::CreateEmpty](../Topic/CPictureHolder::CreateEmpty.md)|建立空的 `CPictureHolder` 物件。|  
|[CPictureHolder::CreateFromBitmap](../Topic/CPictureHolder::CreateFromBitmap.md)|從建立點陣圖。 `CPictureHolder` 物件。|  
|[CPictureHolder::CreateFromIcon](../Topic/CPictureHolder::CreateFromIcon.md)|若要從圖示的 `CPictureHolder` 物件。|  
|[CPictureHolder::CreateFromMetafile](../Topic/CPictureHolder::CreateFromMetafile.md)|若要從中繼檔的 `CPictureHolder` 物件。|  
|[CPictureHolder::GetDisplayString](../Topic/CPictureHolder::GetDisplayString.md)|擷取控制項容器的屬性瀏覽器中顯示的字串。|  
|[CPictureHolder::GetPictureDispatch](../Topic/CPictureHolder::GetPictureDispatch.md)|傳回物件的 `CPictureHolder``IDispatch` 介面。|  
|[CPictureHolder::GetType](../Topic/CPictureHolder::GetType.md)|告知 `CPictureHolder` 物件是否為點陣圖、中繼檔 \(Metafile\) 或圖示。|  
|[CPictureHolder::Render](../Topic/CPictureHolder::Render.md)|呈現圖片。|  
|[CPictureHolder::SetPictureDispatch](../Topic/CPictureHolder::SetPictureDispatch.md)|設定 `CPictureHolder` 物件的 `IDispatch` 介面。|  
  
### 公用資料成員  
  
|名稱|描述|  
|--------|--------|  
|[CPictureHolder::m\_pPict](../Topic/CPictureHolder::m_pPict.md)|將圖片物件的指標。|  
  
## 備註  
 `CPictureHolder` 不具有基底類別。  
  
 內建圖片屬性，開發人員可以顯示指定點陣圖、圖示或中繼檔。  
  
 如需建立自訂圖片屬性的詳細資訊，請參閱本文 [MFC ActiveX 控制項:使用在 ActiveX 控制項的圖片](../../mfc/mfc-activex-controls-using-pictures-in-an-activex-control.md)。  
  
## 繼承階層架構  
 `CPictureHolder`  
  
## 需求  
 **Header:** afxctl.h  
  
## 請參閱  
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [CFontHolder Class](../../mfc/reference/cfontholder-class.md)