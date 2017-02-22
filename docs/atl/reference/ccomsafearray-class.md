---
title: "CComSafeArray 類別 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CComSafeArray"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CComSafeArray 類別"
ms.assetid: ee349aef-33db-4c85-bd08-5d86a3c9d53a
caps.latest.revision: 26
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 29
---
# CComSafeArray 類別
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

此類別是 **SAFEARRAY** 結構的包裝函式。  
  
## 語法  
  
```  
template <  
   typename T,  
   VARTYPE _vartype = _ATL_AutomationType< T >::type  
>  
class CComSafeArray  
```  
  
#### 參數  
 `T`  
 陣列中儲存之資料的類型。  
  
## Members  
  
### 公用建構函式  
  
|名稱|描述|  
|--------|--------|  
|[CComSafeArray::CComSafeArray](../Topic/CComSafeArray::CComSafeArray.md)|建構函式。|  
|[CComSafeArray::~CComSafeArray](../Topic/CComSafeArray::~CComSafeArray.md)|解構函式。|  
  
### 公用方法  
  
|名稱|描述|  
|--------|--------|  
|[CComSafeArray::Add](../Topic/CComSafeArray::Add.md)|將一或多個項目 \(或 **SAFEARRAY** 結構\) 加入 `CComSafeArray`。|  
|[CComSafeArray::Attach](../Topic/CComSafeArray::Attach.md)|將 **SAFEARRAY** 結構附加至 `CComSafeArray` 物件。|  
|[CComSafeArray::CopyFrom](../Topic/CComSafeArray::CopyFrom.md)|將 **SAFEARRAY** 結構的內容複製到 `CComSafeArray` 物件中。|  
|[CComSafeArray::CopyTo](../Topic/CComSafeArray::CopyTo.md)|建立 `CComSafeArray` 物件的複本。|  
|[CComSafeArray::Create](../Topic/CComSafeArray::Create.md)|建立 `CComSafeArray` 物件。|  
|[CComSafeArray::Destroy](../Topic/CComSafeArray::Destroy.md)|終結 `CComSafeArray` 物件。|  
|[CComSafeArray::Detach](../Topic/CComSafeArray::Detach.md)|從 `CComSafeArray` 物件卸離 **SAFEARRAY**。|  
|[CComSafeArray::GetAt](../Topic/CComSafeArray::GetAt.md)|從一維陣列中擷取單一項目。|  
|[CComSafeArray::GetCount](../Topic/CComSafeArray::GetCount.md)|傳回陣列中的元素數目。|  
|[CComSafeArray::GetDimensions](../Topic/CComSafeArray::GetDimensions.md)|傳回陣列中的維度數目。|  
|[CComSafeArray::GetLowerBound](../Topic/CComSafeArray::GetLowerBound.md)|傳回陣列中指定維度的下限。|  
|[CComSafeArray::GetSafeArrayPtr](../Topic/CComSafeArray::GetSafeArrayPtr.md)|傳回 `m_psa` 資料成員的位址。|  
|[CComSafeArray::GetType](../Topic/CComSafeArray::GetType.md)|傳回陣列中儲存之資料的類型。|  
|[CComSafeArray::GetUpperBound](../Topic/CComSafeArray::GetUpperBound.md)|傳回陣列中任何維度的上限。|  
|[CComSafeArray::IsSizable](../Topic/CComSafeArray::IsSizable.md)|測試是否可以調整 `CComSafeArray` 物件大小。|  
|[CComSafeArray::MultiDimGetAt](../Topic/CComSafeArray::MultiDimGetAt.md)|從多維陣列中擷取單一項目。|  
|[CComSafeArray::MultiDimSetAt](../Topic/CComSafeArray::MultiDimSetAt.md)|設定多維陣列中的項目值。|  
|[CComSafeArray::Resize](../Topic/CComSafeArray::Resize.md)|調整 `CComSafeArray` 物件大小。|  
|[CComSafeArray::SetAt](../Topic/CComSafeArray::SetAt.md)|設定一維陣列中的項目值。|  
  
### 公用運算子  
  
|名稱|描述|  
|--------|--------|  
|[CComSafeArray::operator LPSAFEARRAY](../Topic/CComSafeArray::operator%20LPSAFEARRAY.md)|將值轉換成 **SAFEARRAY** 指標。|  
|[CComSafeArray::operator](../Topic/CComSafeArray::operator.md)|從陣列中擷取項目。|  
|[CComSafeArray::operator \=](../Topic/CComSafeArray::operator%20=.md)|指派運算子。|  
  
### 公用資料成員  
  
|名稱|描述|  
|--------|--------|  
|[CComSafeArray::m\_psa](../Topic/CComSafeArray::m_psa.md)|此資料成員包含 **SAFEARRAY** 結構的位址。|  
  
## 備註  
 `CComSafeArray` 提供 [SAFEARRAY Data Type](http://msdn.microsoft.com/zh-tw/9ec8025b-4763-4526-ab45-390c5d8b3b1e) 類別的包裝函式，因此可輕鬆地建立及管理由幾乎任何支援 VARIANT 的類型所組成的一維和多維陣列。  
  
 `CComSafeArray` 不僅簡化了在處理序之間傳遞陣列的作業，還藉由針對上下限檢查陣列索引值，來提供額外的安全性。  
  
 `CComSafeArray` 的下限開頭可以是任何使用者定義值；不過，透過 C\+\+ 存取的陣列應該使用下限 0。 Visual Basic 等其他語言可能會使用其他界限值 \(例如 \-10 到 10\)。  
  
 使用 [CComSafeArray::Create](../Topic/CComSafeArray::Create.md) 可建立 `CComSafeArray` 物件，而 [CComSafeArray::Destroy](../Topic/CComSafeArray::Destroy.md) 可將它刪除。  
  
 `CComSafeArray` 可包含以下 VARIANT 資料類型的子集︰  
  
|VARTYPE|描述|  
|-------------|--------|  
|VT\_I1|char|  
|VT\_I2|short|  
|VT\_I4|int|  
|VT\_I4|long|  
|VT\_I8|longlong|  
|VT\_UI1|byte|  
|VT\_UI2|ushort|  
|VT\_UI4|uint|  
|VT\_UI4|ulong|  
|VT\_UI8|ulonglong|  
|VT\_R4|float|  
|VT\_R8|double|  
|VT\_DECIMAL|decimal 指標|  
|VT\_VARIANT|variant 指標|  
|VT\_CY|Currency 資料類型|  
  
## 需求  
 **標頭︰**atlsafe.h  
  
## 範例  
 [!code-cpp[NVC_ATL_Utilities#75](../../atl/codesnippet/CPP/ccomsafearray-class_1.cpp)]  
  
## 請參閱  
 [SAFEARRAY Data Type](http://msdn.microsoft.com/zh-tw/9ec8025b-4763-4526-ab45-390c5d8b3b1e)   
 [CComSafeArray::Create](../Topic/CComSafeArray::Create.md)   
 [CComSafeArray::Destroy](../Topic/CComSafeArray::Destroy.md)   
 [Class Overview](../../atl/atl-class-overview.md)