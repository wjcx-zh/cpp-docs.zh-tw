---
title: "CCustomTransition 類別 | Microsoft Docs"
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
  - "afxanimationcontroller/CCustomTransition"
  - "CCustomTransition"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CCustomTransition 類別"
ms.assetid: 5bd3f492-940f-4290-a38b-fa68eb8f8401
caps.latest.revision: 17
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CCustomTransition 類別
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

實作自訂的轉換。  
  
## 語法  
  
```  
class CCustomTransition : public CBaseTransition;  
```  
  
## Members  
  
### 公用建構函式  
  
|名稱|描述|  
|--------|--------|  
|[CCustomTransition::CCustomTransition](../Topic/CCustomTransition::CCustomTransition.md)|建構自訂轉換物件。|  
  
### 公用方法  
  
|名稱|描述|  
|--------|--------|  
|[CCustomTransition::Create](../Topic/CCustomTransition::Create.md)|呼叫轉換程式庫，以建立封裝的轉換 COM 物件。  \(覆寫 [CBaseTransition::Create](../Topic/CBaseTransition::Create.md)\)。|  
|[CCustomTransition::SetInitialValue](../Topic/CCustomTransition::SetInitialValue.md)|設定初始值，這個值將會套用至與此轉換相關聯的動畫變數。|  
|[CCustomTransition::SetInitialVelocity](../Topic/CCustomTransition::SetInitialVelocity.md)|設定初始速度，這個速度將會套用至與此轉換相關聯的動畫變數。|  
  
### 受保護的資料成員  
  
|名稱|描述|  
|--------|--------|  
|[CCustomTransition::m\_bInitialValueSpecified](../Topic/CCustomTransition::m_bInitialValueSpecified.md)|指定是否已透過 SetInitialValue 指定初始值。|  
|[CCustomTransition::m\_bInitialVelocitySpecified](../Topic/CCustomTransition::m_bInitialVelocitySpecified.md)|指定是否已透過 SetInitialVelocity 指定初始速度。|  
|[CCustomTransition::m\_initialValue](../Topic/CCustomTransition::m_initialValue.md)|儲存初始值。|  
|[CCustomTransition::m\_initialVelocity](../Topic/CCustomTransition::m_initialVelocity.md)|儲存初始速度。|  
|[CCustomTransition::m\_pInterpolator](../Topic/CCustomTransition::m_pInterpolator.md)|儲存自訂插補器的指標。|  
  
## 備註  
 CCustomTransitions 類別可讓開發人員實作自訂轉換。  這會建立並做為標準轉換，但其建構函式接受自訂插補器的指標做為參數。  執行下列步驟以使用自訂轉換：1.  從 CCustomInterpolator 衍生類別，並至少實作 InterpolateValue 方法。  2.  確保自訂插補器物件的存留期必須超過使用該物件之動畫的期間。  3.  產生 \(使用運算子 new\) CCustomTransition 物件，並將指標傳遞給建構函式中的自訂插補器。  4.  如果自訂內插補點需要這些參數，請呼叫 CCustomTransition::SetInitialValue 和 CCustomTransition::SetInitialVelocity。  5.  將自訂轉換的指標傳遞給動畫物件的 AddTransition 方法，這個物件的值應該會透過自訂演算法顯示為動畫。  6.  動畫物件的值一旦變更時，Windows 動畫 API 將會呼叫 CCustomInterpolator 中的 InterpolateValue \(和其他相關方法\)。  
  
## 繼承階層架構  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CBaseTransition](../../mfc/reference/cbasetransition-class.md)  
  
 [CCustomTransition](../../mfc/reference/ccustomtransition-class.md)  
  
## 需求  
 **標頭檔：**afxanimationcontroller.h  
  
## 請參閱  
 [類別](../../mfc/reference/mfc-classes.md)