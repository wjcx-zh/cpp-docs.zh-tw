---
title: "CComBSTR 類別 | Microsoft Docs"
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
  - "ATL::CComBSTR"
  - "CComBSTR"
  - "ATL.CComBSTR"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "BSTR, 包裝函式"
  - "CComBSTR"
  - "CComBSTR 類別"
ms.assetid: 8fea1879-a05e-47a5-a803-8dec60eaa534
caps.latest.revision: 21
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CComBSTR 類別
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

這個類別是 `BSTR`. 的包裝函式。  
  
## 語法  
  
```  
  
class CComBSTR  
  
```  
  
## Members  
  
### 公用建構函式  
  
|名稱|描述|  
|--------|--------|  
|[CComBSTR::CComBSTR](../Topic/CComBSTR::CComBSTR.md)|建構函式。|  
|[CComBSTR::~CComBSTR](../Topic/CComBSTR::~CComBSTR.md)|解構函式。|  
  
### 公用方法  
  
|名稱|描述|  
|--------|--------|  
|[CComBSTR::Append](../Topic/CComBSTR::Append.md)|將字串附加至 `m_str`。|  
|[CComBSTR::AppendBSTR](../Topic/CComBSTR::AppendBSTR.md)|附加至 `BSTR``m_str`。|  
|[CComBSTR::AppendBytes](../Topic/CComBSTR::AppendBytes.md)|將指定的位元組數目。 `m_str`。|  
|[CComBSTR::ArrayToBSTR](../Topic/CComBSTR::ArrayToBSTR.md)|建立由每個項目的第一個字元的 `BSTR` 在 safearray 的並將其附加至 `CComBSTR` 物件。|  
|[CComBSTR::AssignBSTR](../Topic/CComBSTR::AssignBSTR.md)|指派給 `BSTR``m_str`。|  
|[CComBSTR::Attach](../Topic/CComBSTR::Attach.md)|`BSTR` `CComBSTR` 附加至物件。|  
|[CComBSTR::BSTRToArray](../Topic/CComBSTR::BSTRToArray.md)|建立一個以零起始的一維 safearray，其中陣列的每個元素是從 `CComBSTR` 物件中的字元。|  
|[CComBSTR::ByteLength](../Topic/CComBSTR::ByteLength.md)|以位元組傳回 `m_str` 的長度。|  
|[CComBSTR::Copy](../Topic/CComBSTR::Copy.md)|傳回 `m_str`的複本。|  
|[CComBSTR::CopyTo](../Topic/CComBSTR::CopyTo.md)|藉由 **\[out\]** 參數傳回 `m_str` 的複本。|  
|[CComBSTR::Detach](../Topic/CComBSTR::Detach.md)|中斷連結 `CComBSTR` 物件的 `m_str` 。|  
|[CComBSTR::Empty](../Topic/CComBSTR::Empty.md)|釋放 `m_str`。|  
|[CComBSTR::Length](../Topic/CComBSTR::Length.md)|傳回 `m_str`的長度。|  
|[CComBSTR::LoadString](../Topic/CComBSTR::LoadString.md)|載入字串資源。|  
|[CComBSTR::ReadFromStream](../Topic/CComBSTR::ReadFromStream.md)|從資料流載入 `BSTR` 物件。|  
|[CComBSTR::ToLower](../Topic/CComBSTR::ToLower.md)|將字串轉換為小寫。|  
|[CComBSTR::ToUpper](../Topic/CComBSTR::ToUpper.md)|將字串轉換成大寫。|  
|[CComBSTR::WriteToStream](../Topic/CComBSTR::WriteToStream.md)|`m_str` 儲存至資料流。|  
  
### 公用運算子  
  
|名稱|描述|  
|--------|--------|  
|[CComBSTR::operator BSTR](../Topic/CComBSTR::operator%20BSTR.md)|要轉型為的 `BSTR`的 `CComBSTR` 物件。|  
|[CComBSTR::operator \!](../Topic/CComBSTR::operator%20!.md)|傳回 `true` 或 `false`，取決於 `m_str`是否為 `NULL`。|  
|[CComBSTR::operator \!\=](../Topic/CComBSTR::operator%20!=.md)|`CComBSTR` 與字串比較。|  
|[CComBSTR::operator &](../Topic/CComBSTR::operator%20&.md)|傳回 `m_str`位址。|  
|[CComBSTR::operator \+\=](../Topic/CComBSTR::operator%20+=.md)|`CComBSTR` 附加至物件。|  
|[CComBSTR::operator \<](../Topic/CComBSTR::operator%20%3C.md)|`CComBSTR` 與字串比較。|  
|[CComBSTR::operator \=](../Topic/CComBSTR::operator%20=.md)|將值指派給 `m_str`。|  
|[CComBSTR::operator \=\=](../Topic/CComBSTR::operator%20==.md)|`CComBSTR` 與字串比較。|  
|[CComBSTR::operator \>](../Topic/CComBSTR::operator%20%3E.md)|`CComBSTR` 與字串比較。|  
  
### 公用資料成員  
  
|名稱|描述|  
|--------|--------|  
|[CComBSTR::m\_str](../Topic/CComBSTR::m_str.md)|包含 `BSTR` 與 `CComBSTR` 物件。|  
  
## 備註  
 `CComBSTR` 類別是 `BSTR`的包裝函式，是固定長度的字串。  長度形式儲存在資料之前的記憶體位置的整數資料。  
  
 上一個計數的字元，但也可能包含在字串中之後，內嵌的 null 字元 [BSTR。](http://msdn.microsoft.com/zh-tw/1b2d7d2c-47af-4389-a6b6-b01b7e915228) null 結束。  字元計數不取決於字串長度，不含第一個 Null 字元。  
  
> [!NOTE]
>  `CComBSTR` 類別提供大量該名稱的成員 \(建構函式、指派運算子和比較運算子\) 接受 ANSI 或 Unicode 字串做為引數。  因為暫時 Unicode 字串內部，通常會建立這些函式 ANSI 版本比其 Unicode 的對應效果不彰。  為了提高效率，就請使用 Unicode 版本。  
  
> [!NOTE]
>  由於 Visual Studio 實作的改良的查閱行為 .NET，應實作程式碼，例如 `bstr = L"String2" + bstr;`在先前的版本中可能會進行編譯，做為 `bstr = CStringW(L"String2") + bstr`。  
  
 如需注意清單時， `CComBSTR`時，請參閱 [利用 CComBSTR](../../atl/programming-with-ccombstr-atl.md)。  
  
## 需求  
 **Header:** atlbase.h  
  
## 請參閱  
 [Class Overview](../../atl/atl-class-overview.md)   
 [ATL and MFC String Conversion Macros](../Topic/ATL%20and%20MFC%20String%20Conversion%20Macros.md)