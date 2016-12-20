---
title: "CW2CWEX 類別 | Microsoft Docs"
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
  - "CW2CWEX"
  - "ATL::CW2CWEX"
  - "ATL.CW2CWEX"
  - "ATL.CW2CWEX<t_nBufferLength>"
  - "ATL::CW2CWEX<t_nBufferLength>"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CW2CWEX 類別"
ms.assetid: d654b22b-05a6-410f-a0ec-9a2cbbb4cca7
caps.latest.revision: 20
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CW2CWEX 類別
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

字串轉換巨集 `CW2CTEX` 和 `CT2CWEX`和 typedef 使用這個類別 `CW2W`。  
  
> [!IMPORTANT]
>  這個類別和其成員不能用於 Windows 執行階段執行的應用程式。  
  
## 語法  
  
```  
  
      template<  
int t_nBufferLength= 128  
>  
class CW2CWEX  
```  
  
#### 參數  
 `t_nBufferLength`  
 用來轉換程序的緩衝區大小。  預設長度為 128 個位元組。  
  
## Members  
  
### 公用建構函式  
  
|名稱|描述|  
|--------|--------|  
|[CW2CWEX::CW2CWEX](../Topic/CW2CWEX::CW2CWEX.md)|建構函式。|  
|[CW2CWEX::~CW2CWEX](../Topic/CW2CWEX::~CW2CWEX.md)|解構函式。|  
  
### 公用運算子  
  
|名稱|描述|  
|--------|--------|  
|[CW2CWEX::operator LPCWSTR](../Topic/CW2CWEX::operator%20LPCWSTR.md)|轉換運算子。|  
  
### 公用資料成員  
  
|名稱|描述|  
|--------|--------|  
|[CW2CWEX::m\_psz](../Topic/CW2CWEX::m_psz.md)|儲存來源字串的資料成員。|  
  
## 備註  
 除非需要額外的功能，請使用 `CW2CTEX`， `CT2CWEX`或 `CW2W` 在您的程式碼。  
  
 這個類別是安全使用迴圈，並不會讓堆疊溢位。  根據預設， ATL 轉換類別和巨集來轉換使用目前執行緒的 ANSI 字碼頁。  
  
 下列巨集以此類別:  
  
-   `CW2CTEX`  
  
-   `CT2CWEX`  
  
 下列 typedef 依據此類別:  
  
-   `CW2W`  
  
 如需這些的討論文字轉換巨集，請參閱 [ATL 和 MFC 字串轉換巨集](../Topic/ATL%20and%20MFC%20String%20Conversion%20Macros.md)。  
  
## 範例  
 針對使用這類字串轉換巨集參閱 [ATL 和 MFC 字串轉換巨集](../Topic/ATL%20and%20MFC%20String%20Conversion%20Macros.md) 。  
  
## 需求  
 **Header:** atlconv.h  
  
## 請參閱  
 [CA2AEX 類別](../../atl/reference/ca2aex-class.md)   
 [CA2CAEX 類別](../../atl/reference/ca2caex-class.md)   
 [CA2WEX 類別](../../atl/reference/ca2wex-class.md)   
 [CW2AEX 類別](../../atl/reference/cw2aex-class.md)   
 [CW2WEX 類別](../../atl/reference/cw2wex-class.md)   
 [Class Overview](../../atl/atl-class-overview.md)