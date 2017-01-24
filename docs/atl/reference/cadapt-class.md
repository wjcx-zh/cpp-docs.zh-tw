---
title: "CAdapt Class | Microsoft Docs"
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
  - "ATL.CAdapt"
  - "ATL.CAdapt<T>"
  - "ATL::CAdapt"
  - "ATL::CAdapt<T>"
  - "CAdapt"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "& 運算子, 傳址運算子"
  - "adapter objects"
  - "傳址運算子"
  - "CAdapt class"
ms.assetid: 0bb695a5-72fe-43d1-8f39-7e4da6e34765
caps.latest.revision: 21
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CAdapt Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

此範本用來包裝重新定義傳址 \(address\-of\) 運算子的類別，以傳回物件位址以外的內容。  
  
## 語法  
  
```  
  
      template <  
   class T  
>  
class CAdapt  
```  
  
#### 參數  
 `T`  
 配接的類型。  
  
## 成員  
  
### 公用建構函式  
  
|名稱|描述|  
|--------|--------|  
|[CAdapt::CAdapt](../Topic/CAdapt::CAdapt.md)|建構函式。|  
  
### 公用運算子  
  
|名稱|描述|  
|--------|--------|  
|[CAdapt::operator const T&](../Topic/CAdapt::operator%20const%20T&.md)|傳回 `m_T` 的 `const` 參考。|  
|[CAdapt::operator T&](../Topic/CAdapt::operator%20T&.md)|傳回 `m_T` 的參考。|  
|[CAdapt::operator \<](../Topic/CAdapt::operator%20%3C.md)|將所配接類型的物件與 `m_T` 相比較。|  
|[CAdapt::operator \=](../Topic/CAdapt::operator%20=.md)|將所配接類型的物件指派給 `m_T`。|  
|[CAdapt::operator \=\=](../Topic/CAdapt::operator%20==.md)|將所配接類型的物件與 `m_T` 相比較。|  
  
### 公用資料成員  
  
|名稱|描述|  
|--------|--------|  
|[CAdapt::m\_T](../Topic/CAdapt::m_T.md)|要配接的資料。|  
  
## 備註  
 `CAdapt` 是一個簡單的範本，用來包裝重新定義傳址運算子 \(`operator &`\) 的類別，以傳回物件位址以外的內容。  這些類別的範例包括 ATL 的 `CComBSTR`、`CComPtr` 和 `CComQIPtr` 類別，以及編譯器 COM 支援類別 `_com_ptr_t`。  這些類別全都會重新定義傳址運算子，以傳回其中一個資料成員的位址 \(在 `CComBSTR` 的情況下是 `BSTR`，在其他類別的情況下是介面指標\)。  
  
 `CAdapt` 的主要角色是隱藏 `T` 類別所定義的傳址運算子，但是仍然保留所配接類別的特性。  `CAdapt` 可藉由保留 `T` 類型的公用成員 [m\_T](../Topic/CAdapt::m_T.md)，以及定義轉換運算子、比較運算子和複製建構函式，以便將 `CAdapt` 特製化視為 `T` 類型的物件，藉此滿足此角色的需求。  
  
 配接器類別 `CAdapt` 非常實用，因為某些容器樣式類別預期能夠使用傳址運算子取得其內含物件的位址。  因此，重新定義傳址運算子可能會混淆此需求，而這通常會造成編譯錯誤，並且無法使用非配接的類型搭配只要該類型「可運作」的類別。  `CAdapt` 提供了解決這些問題的方式。  
  
 通常，當您要將 `CComBSTR`、`CComPtr`、`CComQIPtr` 或 `_com_ptr_t` 儲存在容器樣式類別中時，會使用 `CAdapt`。  在支援 C\+\+11 標準之前，這對於 C\+\+ 標準程式庫容器而言是最常要執行的工作，不過，C\+\+11 標準程式庫容器會自動搭配具有多載 `operator&()` 的類型運作。  標準程式庫會在內部使用 [std::addressof\(\)](../Topic/addressof.md) 取得真正的物件位址來達成這個目的。  
  
## 需求  
 **標頭：**atlcomcli.h  
  
## 請參閱  
 [Class Overview](../../atl/atl-class-overview.md)