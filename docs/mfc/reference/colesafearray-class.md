---
title: "COleSafeArray Class | Microsoft Docs"
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
  - "COleSafeArray"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "陣列 [C++], safe"
  - "COleSafeArray class"
  - "ODBC, safe arrays"
  - "safe arrays"
ms.assetid: f45a5224-5f48-40ec-9ddd-287ef9740150
caps.latest.revision: 22
caps.handback.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# COleSafeArray Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

的類別具有選擇性型別和維度用法。  
  
## 語法  
  
```  
class COleSafeArray : public tagVARIANT  
```  
  
## 成員  
  
### 公用建構函式  
  
|名稱|描述|  
|--------|--------|  
|[COleSafeArray::COleSafeArray](../Topic/COleSafeArray::COleSafeArray.md)|建構 `COleSafeArray` 物件。|  
  
### 公用方法  
  
|名稱|描述|  
|--------|--------|  
|[COleSafeArray::AccessData](../Topic/COleSafeArray::AccessData.md)|擷取指標陣列資料。|  
|[COleSafeArray::AllocData](../Topic/COleSafeArray::AllocData.md)|會配置陣列的記憶體。|  
|[COleSafeArray::AllocDescriptor](../Topic/COleSafeArray::AllocDescriptor.md)|配置安全陣列描述項的記憶體。|  
|[COleSafeArray::Attach](../Topic/COleSafeArray::Attach.md)|重新命名現有的 **VARIANT** 陣列中的控制項 `COleSafeArray` 物件。|  
|[COleSafeArray::Clear](../Topic/COleSafeArray::Clear.md)|釋出基礎 **VARIANT**的任何資料。|  
|[COleSafeArray::Copy](../Topic/COleSafeArray::Copy.md)|建立現有陣列的複本。|  
|[COleSafeArray::Create](../Topic/COleSafeArray::Create.md)|建立一個安全陣列。|  
|[COleSafeArray::CreateOneDim](../Topic/COleSafeArray::CreateOneDim.md)|建立一維 `COleSafeArray` 物件。|  
|[COleSafeArray::Destroy](../Topic/COleSafeArray::Destroy.md)|終結現有的陣列。|  
|[COleSafeArray::DestroyData](../Topic/COleSafeArray::DestroyData.md)|終結在安全陣列中的資料。|  
|[COleSafeArray::DestroyDescriptor](../Topic/COleSafeArray::DestroyDescriptor.md)|終結一個安全陣列的描述項。|  
|[COleSafeArray::Detach](../Topic/COleSafeArray::Detach.md)|中斷連結 `COleSafeArray` 物件的 **VARIANT** 陣列 \(讓資料將不會釋放\)。|  
|[COleSafeArray::GetByteArray](../Topic/COleSafeArray::GetByteArray.md)|複製安全陣列的內容插入 [CByteArray](../../mfc/reference/cbytearray-class.md)。|  
|[COleSafeArray::GetDim](../Topic/COleSafeArray::GetDim.md)|傳回維度的參數數目等於陣列中的。|  
|[COleSafeArray::GetElement](../Topic/COleSafeArray::GetElement.md)|擷取安全陣列中的單一項目。|  
|[COleSafeArray::GetElemSize](../Topic/COleSafeArray::GetElemSize.md)|傳回的大小，以位元組為單位\)，在安全陣列中的項目。|  
|[COleSafeArray::GetLBound](../Topic/COleSafeArray::GetLBound.md)|傳回一個安全陣列的所有維度的下限。|  
|[COleSafeArray::GetOneDimSize](../Topic/COleSafeArray::GetOneDimSize.md)|傳回項目的數目。 `COleSafeArray` 一維物件中。|  
|[COleSafeArray::GetUBound](../Topic/COleSafeArray::GetUBound.md)|傳回一個安全陣列的所有維度的上限 \(Upper Bound\)。|  
|[COleSafeArray::Lock](../Topic/COleSafeArray::Lock.md)|將陣列的鎖定計數並將指標陣列資料在陣列描述項。|  
|[COleSafeArray::PtrOfIndex](../Topic/COleSafeArray::PtrOfIndex.md)|傳回指向這個索引的項目。|  
|[COleSafeArray::PutElement](../Topic/COleSafeArray::PutElement.md)|指派唯一的元素至陣列。|  
|[COleSafeArray::Redim](../Topic/COleSafeArray::Redim.md)|變更一個安全陣列的最不重要 \(最右邊\) 的界限。|  
|[COleSafeArray::ResizeOneDim](../Topic/COleSafeArray::ResizeOneDim.md)|變更項目的數目。 `COleSafeArray` 一維物件中。|  
|[COleSafeArray::UnaccessData](../Topic/COleSafeArray::UnaccessData.md)|減少陣列的鎖定計數而失效 `AccessData`擷取的指標。|  
|[COleSafeArray::Unlock](../Topic/COleSafeArray::Unlock.md)|減少陣列的鎖定計數\)，以便予以釋放或調整其大小。|  
  
### 公用運算子  
  
|名稱|描述|  
|--------|--------|  
|[COleSafeArray::operator LPCVARIANT](../Topic/COleSafeArray::operator%20LPCVARIANT.md)|存取 `COleSafeArray` 物件的基礎 **VARIANT** 結構。|  
|[COleSafeArray::operator LPVARIANT](../Topic/COleSafeArray::operator%20LPVARIANT.md)|存取 `COleSafeArray` 物件的基礎 **VARIANT** 結構。|  
|[COleSafeArray::operator \=](../Topic/COleSafeArray::operator%20=.md)|複製值加入至 `COleSafeArray` 物件 \(**SAFEARRAY**、 **VARIANT**、 `COleVariant`或 `COleSafeArray` 陣列\)。|  
|[COleSafeArray::operator \=\=](../Topic/COleSafeArray::operator%20==.md)|比較的兩個不同的陣列 \(**SAFEARRAY**、 **VARIANT**、 `COleVariant`或 `COleSafeArray` 陣列\)。|  
|[COleSafeArray::operator \<\<](../Topic/COleSafeArray::operator%20%3C%3C.md)|輸出的一 `COleSafeArray` 物件的內容至傾印內容的。|  
  
## 備註  
 `COleSafeArray` 從 OLE **VARIANT** 結構取得。  OLE **SAFEARRAY** 成員函式來 `COleSafeArray`，以及一組可用的特別設計的成員函式用於多維位元組陣列。  
  
## 繼承階層架構  
 `tagVARIANT`  
  
 `COleSafeArray`  
  
## 需求  
 **Header:** afxdisp.h  
  
## 請參閱  
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [COleVariant Class](../../mfc/reference/colevariant-class.md)   
 [CRecordset Class](../../mfc/reference/crecordset-class.md)   
 [CDatabase Class](../../mfc/reference/cdatabase-class.md)