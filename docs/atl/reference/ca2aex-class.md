---
title: "CA2AEX 類別 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "ATL::CA2AEX<t_nBufferLength>"
  - "CA2AEX"
  - "ATL.CA2AEX<t_nBufferLength>"
  - "ATLCONV/CA2AEX"
  - "ATL.CA2AEX"
  - "ATL::CA2AEX"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CA2AEX 類別"
ms.assetid: 57dc65df-d9cf-4a84-99d3-6e031dde3664
caps.latest.revision: 20
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 23
---
# CA2AEX 類別
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

字串轉換巨集 `CA2TEX` 和 `CT2AEX`和 typedef 使用這個類別 **CA2A**。  
  
> [!IMPORTANT]
>  這個類別和其成員不能用於 Windows 執行階段執行的應用程式。  
  
## 語法  
  
```  
  
      template<  
int t_nBufferLength= 128  
>  
class CA2AEX  
```  
  
#### 參數  
 `t_nBufferLength`  
 用來轉換程序的緩衝區大小。  預設長度為 128 個位元組。  
  
## Members  
  
### 公用建構函式  
  
|名稱|描述|  
|--------|--------|  
|[CA2AEX::CA2AEX](../Topic/CA2AEX::CA2AEX.md)|建構函式。|  
|[CA2AEX::~CA2AEX](../Topic/CA2AEX::~CA2AEX.md)|解構函式。|  
  
### 公用運算子  
  
|名稱|描述|  
|--------|--------|  
|[CA2AEX::operator LPSTR](../Topic/CA2AEX::operator%20LPSTR.md)|轉換運算子。|  
  
### 公用資料成員  
  
|名稱|描述|  
|--------|--------|  
|[CA2AEX::m\_psz](../Topic/CA2AEX::m_psz.md)|儲存來源字串的資料成員。|  
|[CA2AEX::m\_szBuffer](../Topic/CA2AEX::m_szBuffer.md)|靜態緩衝區，用來存放已轉換的字串。|  
  
## 備註  
 除非需要額外的功能，請使用 `CA2TEX`， `CT2AEX`或 **CA2A** 在自己的程式碼。  
  
 這個類別包含用來儲存轉換結果的固定大小的靜態緩衝區。  如果結果太大而無法符合這個靜態緩衝區，使用 `malloc`，類別配置記憶體，釋放記憶體，當物件超出範圍時。  這可確保不同，文字轉換巨集有 ATL 舊版中，這個類別是安全使用迴圈，並不會讓堆疊溢位。  
  
 如果類別嘗試在堆積上配置記憶體而失敗時，便會呼叫與 **E\_OUTOFMEMORY**引數的 `AtlThrow` 。  
  
 根據預設， ATL 轉換類別和巨集來轉換使用目前執行緒的 ANSI 字碼頁。  
  
 下列巨集以此類別:  
  
-   `CA2TEX`  
  
-   `CT2AEX`  
  
 下列 typedef 依據此類別:  
  
-   **CA2。**  
  
 如需這些的討論文字轉換巨集，請參閱 [ATL 和 MFC 字串轉換巨集](../Topic/ATL%20and%20MFC%20String%20Conversion%20Macros.md)。  
  
## 範例  
 針對使用這類字串轉換巨集參閱 [ATL 和 MFC 字串轉換巨集](../Topic/ATL%20and%20MFC%20String%20Conversion%20Macros.md) 。  
  
## 需求  
 **Header:** atlconv.h  
  
## 請參閱  
 [CA2CAEX 類別](../../atl/reference/ca2caex-class.md)   
 [CA2WEX 類別](../../atl/reference/ca2wex-class.md)   
 [CW2AEX 類別](../../atl/reference/cw2aex-class.md)   
 [CW2CWEX 類別](../../atl/reference/cw2cwex-class.md)   
 [CW2WEX 類別](../../atl/reference/cw2wex-class.md)   
 [Class Overview](../../atl/atl-class-overview.md)