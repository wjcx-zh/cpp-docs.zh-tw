---
title: "CA2CAEX 類別 | Microsoft Docs"
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
  - "ATL.CA2CAEX"
  - "ATL.CA2CAEX<t_nBufferLength>"
  - "ATLCONV/CA2CAEX"
  - "ATL::CA2CAEX<t_nBufferLength>"
  - "ATL::CA2CAEX"
  - "CA2CAEX"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CA2CAEX 類別"
ms.assetid: 388e7c1d-a144-474c-a182-b15f69a74bd8
caps.latest.revision: 20
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CA2CAEX 類別
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

字串轉換巨集 `CA2CTEX` 和 `CT2CAEX`和 typedef 使用這個類別 **CA2CA**。  
  
> [!IMPORTANT]
>  這個類別和其成員不能用於 Windows 執行階段執行的應用程式。  
  
## 語法  
  
```  
  
      template<  
int t_nBufferLength= 128  
>  
class CA2CAEX  
```  
  
#### 參數  
 `t_nBufferLength`  
 用來轉換程序的緩衝區大小。  預設長度為 128 個位元組。  
  
## Members  
  
### 公用建構函式  
  
|名稱|描述|  
|--------|--------|  
|[CA2CAEX::CA2CAEX](../Topic/CA2CAEX::CA2CAEX.md)|建構函式。|  
|[CA2CAEX::~CA2CAEX](../Topic/CA2CAEX::~CA2CAEX.md)|解構函式。|  
  
### 公用運算子  
  
|名稱|描述|  
|--------|--------|  
|[CA2CAEX::operator LPCSTR](../Topic/CA2CAEX::operator%20LPCSTR.md)|轉換運算子。|  
  
### 公用資料成員  
  
|名稱|描述|  
|--------|--------|  
|[CA2CAEX::m\_psz](../Topic/CA2CAEX::m_psz.md)|儲存來源字串的資料成員。|  
  
## 備註  
 除非需要額外的功能，請使用 `CA2CTEX`， `CT2CAEX`或 **CA2CA** 在自己的程式碼。  
  
 這個類別是安全使用迴圈，並不會讓堆疊溢位。  根據預設， ATL 轉換類別和巨集來轉換會使用目前執行緒的 ANSI 字碼頁。  
  
 下列巨集以此類別:  
  
-   `CA2CTEX`  
  
-   `CT2CAEX`  
  
 下列 typedef 依據此類別:  
  
-   **CA2 CA**  
  
 如需這些的討論文字轉換巨集，請參閱 [ATL 和 MFC 字串轉換巨集](../Topic/ATL%20and%20MFC%20String%20Conversion%20Macros.md)。  
  
## 範例  
 針對使用這類字串轉換巨集參閱 [ATL 和 MFC 字串轉換巨集](../Topic/ATL%20and%20MFC%20String%20Conversion%20Macros.md) 。  
  
## 需求  
 **Header:** atlconv.h  
  
## 請參閱  
 [CA2AEX 類別](../../atl/reference/ca2aex-class.md)   
 [CA2WEX 類別](../../atl/reference/ca2wex-class.md)   
 [CW2AEX 類別](../../atl/reference/cw2aex-class.md)   
 [CW2CWEX 類別](../../atl/reference/cw2cwex-class.md)   
 [CW2WEX 類別](../../atl/reference/cw2wex-class.md)   
 [Class Overview](../../atl/atl-class-overview.md)