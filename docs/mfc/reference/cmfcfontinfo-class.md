---
title: "CMFCFontInfo Class | Microsoft Docs"
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
  - "CMFCFontInfo"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CMFCFontInfo class"
  - "CMFCFontInfo::CMFCFontInfo constructor"
ms.assetid: f88329b2-d74e-4921-9441-a3bb6536a049
caps.latest.revision: 26
caps.handback.revision: 14
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CMFCFontInfo Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

`CMFCFontInfo` 類別名稱和描述字型的其他屬性。  
  
## 語法  
  
```  
class CMFCFontInfo : public CObject  
```  
  
## Members  
  
### 公用建構函式  
  
|名稱|描述|  
|--------|--------|  
|`CMFCFontInfo`|建構 `CMFCFontInfo` 物件。|  
  
### 公用方法  
  
|名稱|描述|  
|--------|--------|  
|[CMFCFontInfo::GetFullName](../Topic/CMFCFontInfo::GetFullName.md)|擷取字型及其字元集 \(指令碼\) 的連接字串的名稱。|  
  
### 資料成員  
  
|名稱|描述|  
|--------|--------|  
|[CMFCFontInfo::m\_nCharSet](../Topic/CMFCFontInfo::m_nCharSet.md)|指定字元集的值 \(指令碼\) 與字型。|  
|[CMFCFontInfo::m\_nPitchAndFamily](../Topic/CMFCFontInfo::m_nPitchAndFamily.md)|指定字型的字幅與系列的值。|  
|[CMFCFontInfo::m\_nType](../Topic/CMFCFontInfo::m_nType.md)|指定字型類型的值。|  
|[CMFCFontInfo::m\_strName](../Topic/CMFCFontInfo::m_strName.md)|字型的名稱;例如， \[**Arial**\]。|  
|[CMFCFontInfo::m\_strScript](../Topic/CMFCFontInfo::m_strScript.md)|字元集 \(指令碼\) 的名稱與字型。|  
  
## 備註  
 您可以附加至 [CMFCToolBarFontComboBox Class](../../mfc/reference/cmfctoolbarfontcombobox-class.md) 類別的項目 `CMFCFontInfo` 物件。  呼叫方法 [CMFCToolBarFontComboBox::GetFontDesc](../Topic/CMFCToolBarFontComboBox::GetFontDesc.md) 擷取指標 `CMFCFontInfo` 物件。  
  
## 範例  
 下列範例示範如何使用 `CMFCFontInfo` 類別的各種成員。  範例會示範如何從 `CMFCRibbonFontComboBox`取得 `CMFCFontInfo` 物件以及如何存取它的區域變數。  這個範例是 [MSOffice 2007 年示範範例](../../top/visual-cpp-samples.md)的一部分。  
  
 [!CODE [NVC_MFC_MSOffice2007Demo#6](../CodeSnippet/VS_Snippets_Misc/NVC_MFC_MSOffice2007Demo#6)]  
  
## 需求  
 **標題:** afxtoolbarfontcombobox.h  
  
## 請參閱  
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [類別](../../mfc/reference/mfc-classes.md)   
 [CMFCToolBarFontComboBox Class](../../mfc/reference/cmfctoolbarfontcombobox-class.md)   
 [CMFCToolBarFontSizeComboBox Class](../../mfc/reference/cmfctoolbarfontsizecombobox-class.md)