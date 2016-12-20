---
title: "CComCurrency Class | Microsoft Docs"
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
  - "CComCurrency"
  - "ATL.CComCurrency"
  - "ATL::CComCurrency"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CComCurrency class"
ms.assetid: a1c3d10a-bba6-40cc-8bcf-aed9023c8a9e
caps.latest.revision: 21
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CComCurrency Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

`CComCurrency` 有方法和運算子可建立及管理 CURRENCY 物件。  
  
## 語法  
  
```  
  
class CComCurrency  
  
```  
  
## 成員  
  
### 公用建構函式  
  
|名稱|描述|  
|--------|--------|  
|[CComCurrency::CComCurrency](../Topic/CComCurrency::CComCurrency.md)|`CComCurrency` 物件的建構函式。|  
  
### 公用方法  
  
|名稱|描述|  
|--------|--------|  
|[CComCurrency::GetCurrencyPtr](../Topic/CComCurrency::GetCurrencyPtr.md)|傳回 `m_currency` 資料成員的位址。|  
|[CComCurrency::GetFraction](../Topic/CComCurrency::GetFraction.md)|呼叫此方法以傳回 `CComCurrency` 物件的小數部分。|  
|[CComCurrency::GetInteger](../Topic/CComCurrency::GetInteger.md)|呼叫此方法以傳回 `CComCurrency` 物件的整數部分。|  
|[CComCurrency::Round](../Topic/CComCurrency::Round.md)|呼叫此方法將 `CComCurrency` 物件四捨五入到最接近的整數值。|  
|[CComCurrency::SetFraction](../Topic/CComCurrency::SetFraction.md)|呼叫此方法以設定 `CComCurrency` 物件的小數部分。|  
|[CComCurrency::SetInteger](../Topic/CComCurrency::SetInteger.md)|呼叫此方法以設定 `CComCurrency` 物件的整數部分。|  
  
### 公用運算子  
  
|名稱|描述|  
|--------|--------|  
|[CComCurrency::operator \-](../Topic/CComCurrency::operator%20-2.md)|此運算子用在 `CComCurrency` 物件上執行減法。|  
|[CComCurrency::operator \!\=](../Topic/CComCurrency::operator%20!=.md)|比較兩個 `CComCurrency` 物件是否不相等。|  
|[CComCurrency::operator \*](../Topic/CComCurrency::operator%20*.md)|此運算子用在 `CComCurrency` 物件上執行乘法。|  
|[CComCurrency::operator \*\=](../Topic/CComCurrency::operator%20*=.md)|此運算子用在 `CComCurrency` 物件上執行乘法並指派結果。|  
|[CComCurrency::operator \/](../Topic/CComCurrency::operator%20-1.md)|此運算子用在 `CComCurrency` 物件上執行除法。|  
|[CComCurrency::operator \/\=](../Topic/CComCurrency::operator%20-=2.md)|此運算子用在 `CComCurrency` 物件上執行除法並指派結果。|  
|[CComCurrency::operator \+](../Topic/CComCurrency::operator%20+.md)|此運算子用在 `CComCurrency` 物件上執行加法。|  
|[CComCurrency::operator \+\=](../Topic/CComCurrency::operator%20+=.md)|此運算子用在 `CComCurrency` 物件上執行加法並指派結果給目前物件。|  
|[CComCurrency::operator \<](../Topic/CComCurrency::operator%20%3C.md)|此運算子比較兩個 `CComCurrency` 物件來判斷何者較小。|  
|[CComCurrency::operator \<\=](../Topic/CComCurrency::operator%20%3C=.md)|此運算子比較兩個 `CComCurrency` 物件來判斷是否相等或何者較小。|  
|[CComCurrency::operator \=](../Topic/CComCurrency::operator%20=.md)|此運算子將 `CComCurrency` 物件指派給新的值。|  
|[CComCurrency::operator \-\=](../Topic/CComCurrency::operator%20-=1.md)|此運算子用在 `CComCurrency` 物件上執行減法並指派結果。|  
|[CComCurrency::operator \=\=](../Topic/CComCurrency::operator%20==.md)|此運算子比較兩個 `CComCurrency` 物件是否相等。|  
|[CComCurrency::operator \>](../Topic/CComCurrency::operator%20%3E.md)|此運算子比較兩個 `CComCurrency` 物件來判斷何者較大。|  
|[CComCurrency::operator \>\=](../Topic/CComCurrency::operator%20%3E=.md)|此運算子比較兩個 `CComCurrency` 物件來判斷是否相等或何者較大。|  
|[CComCurrency::operator CURRENCY](../Topic/CComCurrency::operator%20CURRENCY.md)|轉換 `CURRENCY` 物件。|  
  
### 公用資料成員  
  
|名稱|描述|  
|--------|--------|  
|[CComCurrency::m\_currency](../Topic/CComCurrency::m_currency.md)|您的類別執行個體建立的 `CURRENCY` 變數。|  
  
## 備註  
 `CComCurrency` 是 **CURRENCY** 資料類型的包裝函式。  **CURRENCY** 實作為以 10,000 調整的 8 位元組二補數整數值。  這得出一個定點數字，小數點左邊 15 位數，小數點右邊 4 位數。  在涉及金額的計算中，或正確性很重要的任何固定點計算中，**CURRENCY** 資料類型相當有用。  
  
 **CComCurrency** 包裝函式實作此固定點類型的算術、指派和比較運算。  已選取支援的應用程式來控制固定點計算期間可能發生的四捨五入錯誤。  
  
 `CComCurrency` 物件讓您分兩部分來存取小數點兩側的數字：整數部分儲存小數點左邊的值，小數部分儲存小數點右邊的值。  小數部分在內部儲存為 \-9999 \(**CY\_MIN\_FRACTION**\) 和 \+9999 \(**CY\_MAX\_FRACTION**\) 之間的整數值。  [CComCurrency::GetFraction](../Topic/CComCurrency::GetFraction.md) 方法會傳回一個值的 10000 倍 \(**CY\_SCALE**\)。  
  
 指定 **CComCurrency** 物件的整數和小數部分時，請記住小數部分是範圍 0 到 9999 之間的數字。  在處理貨幣時，例如，美元在小數點後面只以兩個有效位數來表示金額，這就很重要。  即使沒有顯示最後兩位數，也必須納入考量。  
  
|值|可能的 CComCurrency 指派|  
|-------|-------------------------|  
|$10.50|CComCurrency\(10,5000\) *或* CComCurrency\(10.50\)|  
|$10.05|CComCurrency\(10,500\) *或* CComCurrency\(10.50\)|  
  
 atlcur.h 中定義 **CY\_MIN\_FRACTION**、**CY\_MAX\_FRACTION** 和 **CY\_SCALE** 值。  
  
## 需求  
 **標頭：**atlcur.h  
  
## 請參閱  
 [COleCurrency Class](../../mfc/reference/colecurrency-class.md)   
 [CURRENCY](http://msdn.microsoft.com/zh-tw/5e81273c-7289-45c7-93c0-32c1553f708e)   
 [Class Overview](../../atl/atl-class-overview.md)