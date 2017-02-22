---
title: "CTypedPtrMap Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CTypedPtrMap"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CTypedPtrMap class"
  - "對應"
  - "pointer maps"
  - "template classes, CTypedPtrMap class"
  - "type-safe collections"
ms.assetid: 9f377385-c6e9-4471-8b40-8fe220c50164
caps.latest.revision: 23
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 25
---
# CTypedPtrMap Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

為指標對應類別提供型別安全的「包裝函式」 `CMapPtrToPtr`、 `CMapPtrToWord`、 `CMapWordToPtr`和 `CMapStringToPtr`的物件。  
  
## 語法  
  
```  
template< class BASE_CLASS, class KEY, class VALUE >  
class CTypedPtrMap : public BASE_CLASS  
```  
  
#### 參數  
 `BASE_CLASS`  
 具型別指標對應類別的基底類別，必須是指標對應類別 \(`CMapPtrToPtr`、 `CMapPtrToWord`、 `CMapWordToPtr`或 `CMapStringToPtr`\)。  
  
 `KEY`  
 當做索引鍵的物件類別對應。  
  
 `VALUE`  
 在對應中之物件的類別。  
  
## 成員  
  
### 公用方法  
  
|名稱|描述|  
|--------|--------|  
|[CTypedPtrMap::GetNextAssoc](../Topic/CTypedPtrMap::GetNextAssoc.md)|取得可逐一查看的下一個項目。|  
|[CTypedPtrMap::Lookup](../Topic/CTypedPtrMap::Lookup.md)|會根據 `VALUE`的 `KEY` 。|  
|[CTypedPtrMap::RemoveKey](../Topic/CTypedPtrMap::RemoveKey.md)|移除指定索引鍵的項目。|  
|[CTypedPtrMap::SetAt](../Topic/CTypedPtrMap::SetAt.md)|將項目插入映像;，如果找到的話，會取代任何現有項目相符的金鑰。|  
  
### 公用運算子  
  
|名稱|描述|  
|--------|--------|  
|[CTypedPtrMap::operator](../Topic/CTypedPtrMap::operator.md)|將元素插入至對應。|  
  
## 備註  
 當您使用時， `CTypedPtrMap`C\+\+ 型別檢查的安裝有助於排除不相符的指標型別所造成的錯誤。  
  
 由於所有 `CTypedPtrMap` 函式內嵌，此範本就不會明顯影響您程式碼的大小或速度。  
  
 如需使用 `CTypedPtrMap`的相關資訊，請參閱 Microsoft 知識庫文件 [集合](../../mfc/collections.md) 和 [樣板類別](../../mfc/template-based-classes.md)。  
  
## 繼承階層架構  
 `BASE_CLASS`  
  
 `CTypedPtrMap`  
  
## 需求  
 **Header:** afxtempl.h  
  
## 請參閱  
 [MFC 範例收集](../../top/visual-cpp-samples.md)   
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [CMapPtrToPtr Class](../../mfc/reference/cmapptrtoptr-class.md)   
 [CMapPtrToWord Class](../../mfc/reference/cmapptrtoword-class.md)   
 [CMapWordToPtr Class](../../mfc/reference/cmapwordtoptr-class.md)   
 [CMapStringToPtr Class](../../mfc/reference/cmapstringtoptr-class.md)