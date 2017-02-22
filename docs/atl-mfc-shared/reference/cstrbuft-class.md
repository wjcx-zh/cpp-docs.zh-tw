---
title: "CStrBufT Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "ATL::CStrBufT<TCharType>"
  - "ATL.CStrBufT"
  - "CStrBufT"
  - "ATL::CStrBufT"
  - "ATL.CStrBufT<TCharType>"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CStrBufT class"
  - "shared classes, CStrBufT"
  - "字串 [C++], custom memory management"
ms.assetid: 6b50fa8f-87e8-4ed4-a229-157ce128710f
caps.latest.revision: 17
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 18
---
# CStrBufT Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

這個類別會提供 `GetBuffer` 提供自動清除資源，並在現有的 `CStringT` 的 `ReleaseBuffer` 物件上呼叫。  
  
## 語法  
  
```  
  
      template<  
   typename TCharType  
>  
class CStrBufT  
```  
  
#### 參數  
 *TCharType*  
 `CStrBufT` 類別的配置類型。  可以是下列其中一項：  
  
-   `char` \(ANSI 字串\)。  
  
-   `wchar_t` \(Unicode 字串\)。  
  
-   **TCHAR** \(適用於 ANSI 和 Unicode 字串\)。  
  
## Members  
  
### 公用 Typedefs  
  
|名稱|描述|  
|--------|--------|  
|`PCXSTR`|使用常數字串的指標。|  
|`PXSTR`|字串的指標。|  
|`StringType`|緩衝區中要由這個類別樣板的特製化作業的資料型別。|  
  
### 公用建構函式  
  
|名稱|描述|  
|--------|--------|  
|[CStrBufT::CStrBufT](../Topic/CStrBufT::CStrBufT.md)|字串緩衝區物件的建構函式。|  
  
### 公用方法  
  
|名稱|描述|  
|--------|--------|  
|[CStrBufT::SetLength](../Topic/CStrBufT::SetLength.md)|設定關聯之資料物件的字元緩衝區的長度。|  
  
### 公用運算子  
  
|名稱|描述|  
|--------|--------|  
|[CStrBufT::operator PCXSTR](../Topic/CStrBufT::operator%20PCXSTR.md)|擷取 **const** 指標關聯字串物件的字元緩衝區。|  
|[CStrBufT::operator PXSTR](../Topic/CStrBufT::operator%20PXSTR.md)|擷取指標關聯字串物件的字元緩衝區。|  
  
### 公用常數  
  
|名稱|描述|  
|--------|--------|  
|[CStrBufT::AUTO\_LENGTH](../Topic/CStrBufT::AUTO_LENGTH.md)|會自動判斷字串的新長度在版本。|  
|[CStrBufT::SET\_LENGTH](../Topic/CStrBufT::SET_LENGTH.md)|設定字串物件的長度 \(以 GetBuffer 時間|  
  
## 備註  
 這個類別會包裝函式類別會取代為 [GetBuffer](../Topic/CSimpleStringT::GetBuffer.md) 呼叫和 [ReleaseBuffer](../Topic/CSimpleStringT::ReleaseBuffer.md)或 [GetBufferSetLength](../Topic/CSimpleStringT::GetBufferSetLength.md) 和 `ReleaseBuffer`。  
  
 主要設計用來當做 Helper 類別， `CStrBufT` 如何列出為開發人員提供便利的方式與字串物件的字元緩衝區一起使用，而不用擔心或呼叫 `ReleaseBuffer`。  在例外狀況或多個結束的程式碼路徑的情況下，，，因為包裝函式物件自然超出範圍這是可行的，使其解構函式來釋放字串資源。  
  
## 需求  
 **Header:** atlsimpstr.h  
  
## 請參閱  
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [ATL\/MFC Shared Classes](../../atl-mfc-shared/atl-mfc-shared-classes.md)