---
title: "CTypedPtrArray Class | Microsoft Docs"
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
  - "CTypedPtrArray"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CTypedPtrArray class"
  - "pointer arrays"
ms.assetid: e3ecdf1a-a889-4156-92dd-ddbd36ccd919
caps.latest.revision: 22
caps.handback.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CTypedPtrArray Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

為類別提供型別安全的「包裝函式」 `CPtrArray` 或 `CObArray`物件。  
  
## 語法  
  
```  
template< class BASE_CLASS, class TYPE >  
class CTypedPtrArray : public BASE_CLASS  
```  
  
#### 參數  
 `BASE_CLASS`  
 具型別指標陣列類別的基底類別，必須為陣列類別 \(`CObArray` 或 `CPtrArray`\)。  
  
 `TYPE`  
 在基底類別陣列中元素的型別。  
  
## 成員  
  
### 公用方法  
  
|名稱|描述|  
|--------|--------|  
|[CTypedPtrArray::Add](../Topic/CTypedPtrArray::Add.md)|將新的項目加入至陣列的結尾。  如果需要，擴大陣列|  
|[CTypedPtrArray::Append](../Topic/CTypedPtrArray::Append.md)|將陣列內容加入至的結尾。  如果需要，擴大陣列|  
|[CTypedPtrArray::Copy](../Topic/CTypedPtrArray::Copy.md)|複製到另一個陣列的陣列;如果需要，擴大陣列。|  
|[CTypedPtrArray::ElementAt](../Topic/CTypedPtrArray::ElementAt.md)|傳回項目指標的暫存參考在陣列中。|  
|[CTypedPtrArray::GetAt](../Topic/CTypedPtrArray::GetAt.md)|傳回值是在指定的索引。|  
|[CTypedPtrArray::InsertAt](../Topic/CTypedPtrArray::InsertAt.md)|插入項目 \(或另一個檔案中的所有元素的陣列\) 中的指定索引。|  
|[CTypedPtrArray::SetAt](../Topic/CTypedPtrArray::SetAt.md)|設定指定之索引的值;不允許的陣列成長。|  
|[CTypedPtrArray::SetAtGrow](../Topic/CTypedPtrArray::SetAtGrow.md)|設定指定之索引的值;如果需要，擴大陣列。|  
  
### 公用運算子  
  
|名稱|描述|  
|--------|--------|  
|[CTypedPtrArray::operator](../Topic/CTypedPtrArray::operator.md)|設定或取得這個項目在指定之索引處的。|  
  
## 備註  
 當您使用 `CTypedPtrArray` 而不是 `CPtrArray` 或 `CObArray`時， C\+\+ 型別檢查的安裝有助於排除不相符的指標型別所造成的錯誤。  
  
 此外， `CTypedPtrArray` 包裝函式執行所需的大部分轉型您是否已經使用 `CObArray` 或 `CPtrArray`。  
  
 由於所有 `CTypedPtrArray` 函式內嵌，此範本就不會明顯影響您程式碼的大小或速度。  
  
 如需使用 `CTypedPtrArray`的相關資訊，請參閱 Microsoft 知識庫文件 [集合](../../mfc/collections.md) 和 [樣板類別](../../mfc/template-based-classes.md)。  
  
## 繼承階層架構  
 `BASE_CLASS`  
  
 `CTypedPtrArray`  
  
## 需求  
 **Header:** afxtempl.h  
  
## 請參閱  
 [MFC 範例收集](../../top/visual-cpp-samples.md)   
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [CPtrArray Class](../../mfc/reference/cptrarray-class.md)   
 [CObArray Class](../../mfc/reference/cobarray-class.md)