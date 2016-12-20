---
title: "CComVariant Class | Microsoft Docs"
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
  - "ATL.CComVariant"
  - "ATL::CComVariant"
  - "CComVariant"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CComVariant class"
  - "VARIANT macro"
  - "VARIANT macro, ATL"
ms.assetid: 4d31149c-d005-44b5-a509-10f84afa2b61
caps.latest.revision: 26
caps.handback.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CComVariant Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

這個類別會包裝 `VARIANT` 型別，提供值的資料型別成員中。  
  
## 語法  
  
```  
  
class CComVariant : public tagVARIANT  
  
```  
  
## Members  
  
### 公用建構函式  
  
|名稱|描述|  
|--------|--------|  
|[CComVariant::CComVariant](../Topic/CComVariant::CComVariant.md)|建構函式。|  
|[CComVariant::~CComVariant](../Topic/CComVariant::~CComVariant.md)|解構函式。|  
  
### 公用方法  
  
|名稱|描述|  
|--------|--------|  
|[CComVariant::Attach](../Topic/CComVariant::Attach.md)|**VARIANT** `CComVariant` 附加至物件。|  
|[CComVariant::ChangeType](../Topic/CComVariant::ChangeType.md)|轉換為新的 `CComVariant` 物件。|  
|[CComVariant::Clear](../Topic/CComVariant::Clear.md)|清除 `CComVariant` 物件。|  
|[CComVariant::Copy](../Topic/CComVariant::Copy.md)|複製至 **VARIANT**`CComVariant` 物件。|  
|[CComVariant::CopyTo](../Topic/CComVariant::CopyTo.md)|複製 `CComVariant` 物件的內容。|  
|[CComVariant::Detach](../Topic/CComVariant::Detach.md)|中斷連結 `CComVariant` 物件的基礎 **VARIANT** 。|  
|[CComVariant::GetSize](../Topic/CComVariant::GetSize.md)|傳回大小總數 `CComVariant` 物件內容的位元組陣列。|  
|[CComVariant::ReadFromStream](../Topic/CComVariant::ReadFromStream.md)|從資料流載入 **VARIANT** 。|  
|[CComVariant::SetByRef](../Topic/CComVariant::SetByRef.md)|初始化 `CComVariant` 物件並設定 **vt** 成員至 **VT\_BYREF**。|  
|[CComVariant::WriteToStream](../Topic/CComVariant::WriteToStream.md)|儲存 **VARIANT** 基礎資料流。|  
  
### 公用運算子  
  
|||  
|-|-|  
|[CComVariant::operator \<](../Topic/CComVariant::operator%20%3C.md)|表示 `CComVariant` 物件是否大於指定的 **VARIANT**小於。|  
|[CComVariant::operator \>](../Topic/CComVariant::operator%20%3E.md)|表示 `CComVariant` 物件是否大於指定的 **VARIANT**大於。|  
|[運算子\! \=](../Topic/CComVariant::operator%20!=.md)|表示 `CComVariant` 物件是否不等於指定的 **VARIANT**。|  
|[\=運算子](../Topic/CComVariant::operator%20=.md)|將值指派給 `CComVariant` 物件。|  
|[運算子\=\=](../Topic/CComVariant::operator%20==.md)|表示 `CComVariant` 物件是否等於指定的 **VARIANT**。|  
  
## 備註  
 `CComVariant` 包裝 `VARIANT and VARIANTARG` 型別，包含值的資料型別、整合式並且儲存在成員產生關聯。  **VARIANT**s 通常用來自動化。  
  
 `CComVariant` 從 **VARIANT** 型別衍生自，所以可以使用它的地方，都可以使用 **VARIANT** 。  您可以使用，例如， **V\_VT** 巨集擷取 `CComVariant` 的型別也可以直接存取 **vt** 成員像與 **VARIANT**。  
  
## 繼承階層架構  
 `tagVARIANT`  
  
 `CComVariant`  
  
## 需求  
 **Header:** atlcomcli.h  
  
## 請參閱  
 [Class Overview](../../atl/atl-class-overview.md)