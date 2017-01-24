---
title: "CFixedStringT Class | Microsoft Docs"
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
  - "CFixedStringT"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CFixedStringT class"
  - "shared classes, CFixedStringT"
ms.assetid: 6d4171ba-3104-493a-a6cc-d515f4ba9a4b
caps.latest.revision: 17
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CFixedStringT Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

這個類別是內建的字元緩衝區表示字串物件。  
  
## 語法  
  
```  
  
      template< class   
      StringType  
      , int   
      t_nChars  
       >    
class CFixedStringT : private CFixedStringMgr, public StringType  
```  
  
#### 參數  
 `StringType`  
 使用，基底類別會提供內建的字串物件，而且所有 `CStringT`架構類型。  範例包括、和 `CString``CStringA``CStringW`。  
  
 *t\_nChars*  
 在緩衝區中的字元數。  
  
## Members  
  
### 公用建構函式  
  
|名稱|描述|  
|--------|--------|  
|[CFixedStringT::CFixedStringT](../Topic/CFixedStringT::CFixedStringT.md)|字串物件的建構函式。|  
  
### 公用運算子  
  
|名稱|描述|  
|--------|--------|  
|[CFixedStringT::operator \=](../Topic/CFixedStringT::operator%20=.md)|指派新值給 `CFixedStringT` 物件。|  
  
## 備註  
 這個類別是根據 `CStringT`的自訂字串類別的範例。  雖然很類似，這兩個類別中實作不同。  `CFixedStringT` 和 `CStringT` 的主要差異如下:  
  
-   初始字元緩衝區配置做為物件的一部分且具有 *t\_nChars*大小。  這可讓 **CFixedString** 物件佔據基於效能目的連續記憶體區塊。  不過，如果 `CFixedStringT` ，物件的內容。 *t\_nChars*態度，動態配置緩衝區。  
  
-   `CFixedStringT` 物件的字元緩衝區永遠都是相同的長度 \(*t\_nChars*\)。  沒有在緩衝區大小的限制 `CStringT` 物件的。  
  
-   `CFixedStringT` 的記憶體管理員自訂這類共用在兩個或多個之間的 [CStringData](../../atl-mfc-shared/reference/cstringdata-class.md) 物件不允許的 `CFixedStringT` objectsis。  `CStringT` 物件沒有這項限制。  
  
 如需 `CFixedStringT` 和記憶體管理的自訂的詳細資訊的字串物件，請參閱 [記憶體管理和 CStringT](../../atl-mfc-shared/memory-management-with-cstringt.md)。  
  
## 繼承階層架構  
 `IAtlStringMgr`  
  
 `StringType`  
  
 `CFixedStringMgr`  
  
 `CFixedStringT`  
  
## 需求  
 **Header:** cstringt.h  
  
## 請參閱  
 [CStringT Class](../../atl-mfc-shared/reference/cstringt-class.md)   
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [ATL\/MFC Shared Classes](../../atl-mfc-shared/atl-mfc-shared-classes.md)