---
title: "COleCurrency Class | Microsoft Docs"
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
  - "CURRENCY"
  - "COleCurrency"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "COleCurrency class"
  - "CURRENCY"
  - "fixed-point numbers"
  - "數字, fixed-point"
ms.assetid: 3a36e345-303f-46fb-a57c-858274378a8d
caps.latest.revision: 24
caps.handback.revision: 13
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# COleCurrency Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

封裝 OLE Automation `CURRENCY` 資料型別。  
  
## 語法  
  
```  
class COleCurrency  
```  
  
## 成員  
  
### 公用建構函式  
  
|名稱|描述|  
|--------|--------|  
|[COleCurrency::COleCurrency](../Topic/COleCurrency::COleCurrency.md)|建構 `COleCurrency` 物件。|  
  
### 公用方法  
  
|名稱|描述|  
|--------|--------|  
|[COleCurrency::Format](../Topic/COleCurrency::Format.md)|產生 `COleCurrency` 物件中的格式化字串表示。|  
|[COleCurrency::GetStatus](../Topic/COleCurrency::GetStatus.md)|取得狀態 \(驗證\) 這 `COleCurrency` 物件。|  
|[COleCurrency::ParseCurrency](../Topic/COleCurrency::ParseCurrency.md)|讀取字串中的 **貨幣** 值並將 `COleCurrency`的值。|  
|[COleCurrency::SetCurrency](../Topic/COleCurrency::SetCurrency.md)|設定這 `COleCurrency` 物件值的深層複本。|  
|[COleCurrency::SetStatus](../Topic/COleCurrency::SetStatus.md)|設定狀態 \(驗證\) `COleCurrency` 這個物件的。|  
  
### 公用運算子  
  
|名稱|描述|  
|--------|--------|  
|[\=運算子](../Topic/COleCurrency::operator%20=.md)|複製 `COleCurrency` 值。|  
|[運算子 \+ \-，](../Topic/COleCurrency::operator%20+,%20-.md)|加入，減去，並變更 `COleCurrency` 值的正負號。|  
|[\+\=運算子， \- \=](../Topic/COleCurrency::operator%20+=,%20-=.md)|從這個物件 `COleCurrency` 增加和減少 `COleCurrency` 值。|  
|[運算子\*，\/](../Topic/COleCurrency::operator%20*,%20-.md)|以整數值來呼叫 `COleCurrency` 值。|  
|[\*\=運算子，\/\=](../Topic/COleCurrency::operator%20*=,%20-=.md)|以整數值來呼叫這個 `COleCurrency` 值。|  
|[運算子\<\<](../Topic/COleCurrency::operator%20%3C%3C,%20%3E%3E.md)|輸出 `COleCurrency` 值加入至 `CArchive` 或 `CDumpContext`。|  
|[運算子\>\>](../Topic/COleCurrency::operator%20%3C%3C,%20%3E%3E.md)|項目會從 `CArchive`的 `COleCurrency` 物件。|  
|[運算子貨幣](../Topic/COleCurrency::operator%20CURRENCY.md)|轉換 `COleCurrency` 值至 **貨幣**。|  
|[運算子\=\=， \<， \<\=等等\_.](../Topic/COleCurrency%20Relational%20Operators.md)|比較兩個 `COleCurrency` 值。|  
  
### 公用資料成員  
  
|名稱|描述|  
|--------|--------|  
|[COleCurrency::m\_cur](../Topic/COleCurrency::m_cur.md)|包含這個 `COleCurrency` 物件的基礎 **貨幣** 。|  
|[COleCurrency::m\_status](../Topic/COleCurrency::m_status.md)|包含這個 `COleCurrency` 物件的狀態。|  
  
## 備註  
 **COleCurrency** 不具有基底類別。  
  
 **貨幣** 實作成 8 個位元組， two's 補數整數值以 10,000 為倍數縮放的。  這在小數點左邊以數字 15 和 4 個數字的定點數靠右對齊。  **貨幣** 資料型別是極為有用。與貨幣有關的計算，或是精確度是很重要的所有固定點計算。  它是一個 OLE Automation 的 `VARIANT` 資料型別的可能型別。  
  
 **COleCurrency** 也會實作這個定點型別的基本算術運算。  支援的作業已選取控制項中的一個計算期間，發生的誤差  
  
## 繼承階層架構  
 `COleCurrency`  
  
## 需求  
 **Header:** afxdisp.h  
  
## 請參閱  
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [COleVariant Class](../../mfc/reference/colevariant-class.md)