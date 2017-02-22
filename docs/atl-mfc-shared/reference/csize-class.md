---
title: "CSize Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CSize"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CSize class"
  - "維度"
  - "維度, MFC"
  - "SIZE"
ms.assetid: fb2cf85a-0bc1-46f8-892b-309c108b52ae
caps.latest.revision: 20
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 21
---
# CSize Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

類似於 Windows [大小](http://msdn.microsoft.com/library/windows/desktop/dd145106) 結構，實作一個相對座標或位置。  
  
## 語法  
  
```  
class CSize : public tagSIZE  
```  
  
## Members  
  
### 公用建構函式  
  
|名稱|描述|  
|--------|--------|  
|[CSize::CSize](../Topic/CSize::CSize.md)|建構 `CSize` 物件。|  
  
### 公用運算子  
  
|名稱|描述|  
|--------|--------|  
|[CSize::operator \-](../Topic/CSize::operator%20-.md)|減去兩個尺寸。|  
|[CSize::operator \!\=](../Topic/CSize::operator%20!=.md)|檢查是否不相等。 `CSize` 和大小之間。|  
|[CSize::operator \+](../Topic/CSize::operator%20+.md)|加入兩個尺寸。|  
|[CSize::operator \+\=](../Topic/CSize::operator%20+=.md)|加入至 `CSize`大小。|  
|[CSize::operator \-\=](../Topic/CSize::operator%20-=.md)|從 `CSize`減去大小。|  
|[CSize::operator \=\=](../Topic/CSize::operator%20==.md)|檢查是否相等。 `CSize` 和大小之間。|  
  
## 備註  
 這個類別會從 **大小** 結構取得。  這表示您可以在 **大小** 要求，並 **大小** 結構的資料成員是 `CSize`的可存取的資料成員中的參數。 `CSize` 。  
  
 **大小** \(和\) 的 `CSize`**cx** 和 **cy** 成員都是公用的。  此外， `CSize` 實作成員函式運算 **大小** 結構。  
  
> [!NOTE]
>  如需共用公用程式類別的詳細資訊 \(例如 `CSize`\)，請參閱 [共用類別](../../atl-mfc-shared/atl-mfc-shared-classes.md)。  
  
## 繼承階層架構  
 `tagSIZE`  
  
 `CSize`  
  
## 需求  
 **Header:** atltypes.h  
  
## 請參閱  
 [MFC MDI 範例](../../top/visual-cpp-samples.md)   
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [CRect Class](../../atl-mfc-shared/reference/crect-class.md)   
 [CPoint Class](../../atl-mfc-shared/reference/cpoint-class.md)